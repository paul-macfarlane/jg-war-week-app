# War Week architecture

Owned by Paul.

## Stack
- **Framework:** Next.js 16 (App Router), React, TypeScript, pnpm. One app; same stack as Paul's other projects.
- **UI:** Tailwind v4 and shadcn/ui on Base UI. Same as Paul's other projects; accessible primitives (focus, dialogs, menus) by default.
- **Validation:** Zod for all input at the action boundary.
- **Hosting:** Vercel, `staging` branch → staging, `main` → production. Zero ops for an app that's idle most of the year.
- **Database:** Neon Postgres (Docker Postgres locally), Drizzle ORM, drizzle-kit migrations run from a GitHub Action. Relational data with real constraints and transactions; scales to zero between War Weeks.
- **Auth:** Better Auth, Google OAuth only for v1. No passwords. Keeps employee data in our own database.
- **Pages and competition rules:** Tiptap editor; documents stored as JSON and rendered on the server. WYSIWYG for Jason and hosts, no raw HTML.
- **Testing:** Vitest (unit, and integration against real Postgres), Playwright with axe for e2e. GitHub Actions for CI. Fast checks on every PR, core journeys before `main`.
- **Observability:** structured JSON logs to Vercel; Sentry (free plan) for error alerts, added before War Week XII. Meets the small-group floor of alerting plus debuggable logs.

## Structure
Organized by feature, with the same layers inside each feature.

```
src/
  app/              Next.js routes: pages, thin Server Actions, route-specific components
  modules/          server-side only, no React
    <feature>/
      domain/       pure functions: rules, formats, scoring
      service.ts    writes (use cases)
      queries.ts    reads shaped for pages
  db/               Drizzle schema (one file per module) and migrations
  lib/              action wrapper, logger, reportError, typed errors
  components/ui/    shadcn
```

Modules follow the requirements' feature list: `competitions`, `standings`, `people`, `editions`, `pages`, `awards`, `subjective-points`, `access`.

- **Dependency direction:** `app` → a module's `service`/`queries` → its `domain`. Domain imports nothing from the database, Next.js or services. Modules use each other only through `service`/`queries` exports, never each other's tables. Enforced by lint.
- **Services:** every function is `(ctx, input)` with `ctx = { db, actor, now }`. It checks `can()`, runs one transaction, and records who did it. Services throw typed errors (NotAllowed, NotFound, Invalid, Stale). Authorization lives here because Server Actions are public endpoints. Stale saves ([competitions.md](features/competitions.md#corrections)) are caught by each result write carrying the version the user loaded.
- **Queries:** reads need a signed-in actor and two visibility rules: Setup editions are visible to Organizers only, and emails appear only in Organizer-only queries. Beyond that, queries return page-shaped data with no permission logic. Standings composes other modules' queries and runs the pure scoring.
- **Server Actions:** go through one wrapper that resolves the actor, validates input, logs one JSON line with a request id, maps typed errors to plain messages and passes unexpected ones to `reportError()`. No business logic.
- **Error boundaries** on every route from the start.
- **Time:** stored in UTC; displayed as the requirements say.

## Decisions

### Feature modules with a service layer, no repositories
Code is grouped by feature so a work package or feature spec maps to one folder. Each feature has a pure domain, a service for writes and queries for reads. Drizzle is the data abstraction: no repository layer, dependency injection or interfaces, since tests use real Postgres and there is nothing to swap.
- **Alternative:** top-level layers (`server/`, `domain/`). Rejected: slightly fewer rules, but a feature spans four folders. Either is a mechanical move to the other while the dependency rules hold.
- **Alternative:** logic in Server Actions. Rejected: authorization would scatter across public endpoints and testing would need Next's request context.

### One Next.js app, no separate API
Server-rendered pages for reads, Server Actions for writes. Install to home screen is a web manifest, not a native app.
- **Alternative:** Vite SPA + Hono API (picksleagues). Rejected: API-first only pays off for a non-web client, and nothing in the requirements or Deferred list needs one. It would mean two deploy units and a contract layer for no use case.

### Vercel, moving to Jahnel Group ownership before War Week XII
Built and pitched on Paul's account; moved to a JG-owned Vercel Pro team (with the database, OAuth client and domain) before War Week XII. Hobby is for non-commercial personal use, and Jason needs access if Paul is unavailable during the week. All configuration comes from environment variables so the move is configuration, not code.
- **Alternative:** Fly.io or Render containers. Rejected: more ops for an app that's idle most of the year.

### Migrations run from a GitHub Action, not the Vercel build
A failed deploy must never leave production's schema ahead of its code, least of all during War Week. Every migration must work with the code already deployed. Staging runs on a Neon branch.
- **Alternative:** migrate in the Vercel build (prototype). Rejected for the reason above.

### Accounts, people and sign-in policy are separate
- **Account:** a Better Auth user with one or more provider logins. Adding a provider (e.g. Microsoft) is configuration.
- **Person:** a roster entry, with any email or none. Owned by Organizers.
- **Role:** Organizer and Host are stored against the person, never derived from an email domain.
- Linking an account to a person follows [people.md](features/people.md#sign-in). Only **provider-verified** emails link. The link and the person's roles are resolved on every request, so an email change or a removed role takes effect immediately.
- **Avatar:** the provider's profile photo URL is stored on the account at each sign-in and the image loads from the provider (Google), so image and content-security settings allow that host. It's personal data visible to every signed-in user; Sentry and logs never receive it.
- Who may sign in is decided by one policy function. For v1 it allows verified emails in `ALLOWED_EMAIL_DOMAINS` (`jahnelgroup.com`). Nothing else in the code knows about Jahnel Group's domain: no Google `hd` restriction, no domain checks elsewhere.
- Sessions expire after a fixed 30 days: Better Auth's expiry is set to 30 days with refresh-on-use turned off (its default is shorter and sliding). Signing in again re-runs the sign-in policy, so a suspended Google account loses access within 30 days.
- The first Organizer on a new deployment is created by a documented one-off setup step naming their email.
- **Partner sign-in:** add a Better Auth provider and extend the sign-in policy. People, roles, roster import and linking never look at an email's domain. The Google OAuth client must be **External** (not Workspace-Internal) when it moves to JG, or Google itself blocks non-JG accounts. Microsoft accounts don't always assert a verified email; linking still requires one.
- E2E tests sign in through a secret-gated test route that is refused in production.
- **Alternative:** Supabase (Postgres, auth and realtime bundled). Rejected: replaces auth and ORM conventions Paul already owns to gain realtime we don't need.
- **Alternative:** Clerk or WorkOS. Rejected: a new third party holding employee personal data, an extra dependency during War Week, and a second user list to sync with people. Revisit only if a partner company requires sign-in through its own corporate identity provider.

### Recovery: surgical restore, and archive dumps at edition end
Deleting a competition is permanent by design, and results keep only who recorded them and who last changed them. To undo a mistake, a copy of the database is restored with Neon to just before it, and only the affected rows are copied back, so everyone else's results since are kept. Neon's restore window is confirmed when the database moves to JG, and the steps are written down and rehearsed before War Week XII.

Neon's history only reaches back days, so the archive also gets a long-term copy: when an edition ends and after any backfill, the database owner runs one documented `pg_dump` command and saves the file to a restricted JG Google Drive folder (it contains emails).
- **Alternative:** soft delete, app-level undo or per-result history. Rejected: not in the requirements, and adds state to every query.
- **Alternative:** scheduled automated backups (GitHub Action to a repo or Drive). Rejected: the archive changes once or twice a year, so automation and its permissions cost more than the manual step.

### Fresh on load, no polling or push
Every page reads from the database at request time; no data caching. A write refreshes the writer's view, and a page refreshes once when the app or tab returns to the foreground (installed iOS apps have no reload or pull-to-refresh). Standings change a few dozen times a week, so nothing more is needed.
- **Alternative:** polling every 20–30s. Rejected for now; easy to add to a single page if a TV display becomes a use case.
- **Alternative:** realtime push (Pusher, Ably). Rejected: a new third party and failure mode for no real gain. Vercel functions can't hold websockets themselves.
- **Manual refresh:** installed apps have no browser refresh. A visible refresh control on live pages, and optionally a custom pull-to-refresh in standalone mode, are decided in design (/design-ui). A gesture is never the only way to refresh.

### Pages: restricted rich text, links for everything else
Organizer pages and competition rules allow headings, paragraphs, bold/italic, lists and links (`https:` and `mailto:` only). Stored as JSON, validated against that schema, and rendered on the server as semantic HTML, never raw HTML. This matches what the old Google Sites wikis actually used (11 years of exports: day headings, event lines, FAQ, sign-up links). Collapsible sections (e.g. FAQ) are decided in design; if wanted, they are one more block type.
- **Not in v1:** tables (Google Sites has no native tables and phone tables are poor), images and media (Deferred), embeds. Drive files and media are linked, not embedded: embedded Drive content fails without Google cookies in the frame (Safari, installed iOS apps) and for partner users without access. Each is a later schema addition, not a rewrite. Inline media will need blob storage, proposed when images are approved.
- **Alternative:** Markdown textarea. Rejected: harder for Jason than the wiki.
- **Alternative:** hosted CMS. Rejected: content outside the app is the scattered-history problem again.

### Standings are derived, never stored
The database stores facts: match entrants with scores or finishing order, participation marks, best-score attempts, subjective points (entries Organizers type in), and each competition's settings. One pure scoring module turns those into places, points, team or individual totals and standings on every read. Pages call it (e.g. `getEditionStandings`); none reimplements scoring.
- **Why:** the spec lets points, decide-by, tiers, team scoring, squads and teams change at any time, and edits to finished competitions must recalculate. With a stored ledger every one of those actions must also rebuild points, and missing one shows wrong standings. Derived standings can't drift, and an edition is a few hundred rows, so computing is effectively free.
- **Guarding history:** scoring rules are stored on each competition as data, so new rules are new options rather than changes to old behavior. A test pins each ended edition's final standings (starting with War Week XI) so any change that would alter the archive fails CI.
- **Alternative:** a points ledger written on every change. Rejected: the same scoring logic plus a table and a rebuild on every mutation path. If stats ever want SQL-friendly totals, a view or cache can sit behind the scoring module without changing what's stored.

### One match model for all match formats
Ranking, Bracket, Heats and Survival share one shape: a competition has entrants (a person, squad or team, per its entrant type), rounds, matches, and match entrants with a score and/or place. Best score has attempts; Participation has completions (with optional tier). Each format is a pure module that builds the first round, advances when a match is recorded (including flagging ties that block advancement) and knows when it's finished.
- **Why:** it's how the spec describes formats, so the schema matches how hosts think. Scoring and history read one shape. New formats (Deferred Swiss and round robin) are new modules on the same tables.
- **Alternative:** tables per format (prototype). Rejected: every new format adds tables and read paths.

### Testing: most confidence from the domain and the services
- **Unit:** the pure domain (formats, scoring, permissions, sign-in policy). The bulk of the tests.
- **Integration:** services and queries against real Postgres, including authorization (who may record, self-report, edit, delete) and transactions. No mocks of our own code.
- **E2E:** Playwright on a phone viewport for the three core journeys (participant, host, organizer), with axe accessibility checks. Run before merge to `main`, not on every PR.
- **Every PR:** lint, format, typecheck, unit, integration, build.
- Bug fixes get a test at the lowest level that catches them, not a new e2e spec.
- **Alternative:** e2e on every PR. Rejected: slower PRs; core journeys before merge to `main` is enough.

### Sentry for alerts, structured logs for debugging
Sentry on server and client alerts on unhandled errors. It is added before War Week XII, on JG-owned accounts, not for the pitch; the action wrapper's `reportError()` and the route error boundaries are the seams it plugs into. Each server action logs one JSON line (actor, action, outcome, duration) with a request id shared with Sentry. Sentry receives account ids only: no emails, names or request bodies. Who recorded each result and who last changed it are stored with the result (a requirement), which answers most score questions better than logs.
- **Alternative:** Vercel logs only. Rejected: no alerting, below the profile floor.
- **Alternative:** hand-rolled notifier. Rejected: misses client errors and stack traces.
- Sentry moves to JG ownership with everything else.

### History goes in through the services
War Week XI's results (for the pitch) and any backfilled edition are loaded by a one-off import script that calls the same services, so every rule and validation applies. Imported results are marked as imported rather than recorded by a person. A backfilled edition goes straight from Setup to Ended.
- **Alternative:** a seed script writing tables directly. Rejected: it would bypass the rules the archive guard test depends on.

### Room for Deferred requirements
Each Deferred item fits without a rewrite:
- **League formats (Swiss, round robin):** new format modules on the same rounds and matches. Scoring only sees final places, so it doesn't change.
- **Best-of matches:** works today by recording games won as the match score (higher score wins). Per-game detail, if wanted, is a child table of match.
- **Qualifier into bracket seeding:** hosts can already set round-one order by hand. Automatic chaining is a source-competition setting that builds the order from its final places.
- **Participation result auto-creating an award:** an award gains an optional source competition, and its recipients come from that competition's completions.
- **Backfilling editions before XI:** through the same import path as XI. Where only final results are known, a Ranking competition records them; where only team totals are known, subjective points with a reason fill the gap.
- **Image uploads:** blob storage (to be proposed when approved), image columns on teams, editions and people, and an image block in pages.
