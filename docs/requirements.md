# War Week requirements

Owned by Paul. AI may propose changes; none land without approval.

## Profile
- **Audience:** small group. Jahnel Group employees plus partner-company participants (LTI, InfoLink), ~100–125 people per edition.
- **Stage:** product. First goal is a coherent version that gets Jason's buy-in.
- **Usage shape:** intense for one week a year, near zero otherwise. It must be rock solid during War Week; the rest of the year only the archive needs to work.
- **Relaxed for this project:** scale.
- **Next edition:** War Week XII is a free-for-all, so free-for-all scoring must be fully supported, not treated as an edge case.
- **Pitch demo:** the core journeys working on War Week XI data (Paul supplies the data in the work package that builds the archive), plus Claude Design mockups for the visual Pitch to Jason items.
- **Timeline:** pitch to Jason targeted for end of October 2026. Timeline doesn't drive tech choices; the goal is something Paul believes in, shown early enough to get feedback.

## Purpose
During War Week, one place where employees see what's happening, the schedule and the standings, and where organizers and hosts record results so standings stay live. After the week, it keeps the history.

### Problems it solves
1. Hosts track results separately and report back to Jason, who then records them.
2. Participants don't have a good sense of the live score.
3. Match history is hard to find, whether you're in the event (how is the other side of my bracket going?) or not.
4. History gets lost over time when the wiki isn't kept up and things are scattered.

It must be **easy to use for everyone: participants, hosts and organizers.** Participants find what they need in a tap or two on their phone, hosts record results in seconds, and running War Week in the app is less work for Jason than the wiki was. If any of the three finds it harder than what they did before, it fails.

## Character
- Feels like War Week: competitive, a little irreverent, Jahnel Group through and through.
- JG branding is the baseline look. Each edition's theme comes through in naming (what teams are called, e.g. Houses, Tribes) and in the pages Organizers write.
- Copy is plain and direct. No marketing voice.

## Design
- **Design system:** <Claude Design link, TBD>
- **Screens:** <Claude Design links, TBD>

## App-wide rules

### Roles
- **Organizer:** runs the whole edition (Jason, Paul). Manages the Organizer list.
- **Host:** runs one or more competitions (e.g. a pool tournament host). Assigned by an Organizer. Records results for their competitions.
- **User:** anyone who signs in. Users can read everything in Live and Ended editions; Setup editions are visible to Organizers only.
- **Participant:** a person on the edition's roster. Participants who are also users can self-report results where a host allows it.

### Navigation
Home, Competitions, Info and Archive for everyone; Manage for Organizers (editions, teams and roster, competitions and hosts, subjective points, awards, Organizer list). Things are edited where they live: a host records on the match, an Organizer edits a page from the page. Person pages are reached by tapping a name; your own from your avatar.

### Structured vs. pages
Structured data only where the app computes something or it's history people care about: editions, teams and roster, competitions, matches, results, points, standings, awards. Everything else is an Organizer-written page (rich text and links, no images), listed under Info in the order Organizers set (e.g. schedule above FAQ). JG branding ships with the app. Sign-up forms and similar stay as external links in pages.

## Features

| Feature | Use case (who, when) | Core journey? | Detail |
|---|---|---|---|
| Sign in | Any employee opening the app with their Jahnel Group Google account | yes | — |
| Home | Anyone opening the app to see where the current War Week stands | yes | [features/editions.md](features/editions.md) |
| Standings | A participant on Tuesday night checking which team is ahead | yes | [features/competitions.md](features/competitions.md) |
| Competitions & results | A host recording a bracket match as it finishes; points land in standings as soon as the result is decided | yes | [features/competitions.md](features/competitions.md) |
| Match history | A pool player checking how the other side of the bracket is going; someone who missed Tournament Night looking up how the Smash bracket played out | yes | [features/competitions.md](features/competitions.md) |
| Self-report | A player in a large tournament reporting their own match so the host doesn't have to chase every result | yes | [features/competitions.md](features/competitions.md) |
| Subjective points | Jason awarding spirit or bonus points, with a reason, outside any competition | yes | — |
| Awards | Jason entering MVPs, Top Biller and Black Midnight finishers after closing ceremonies. Honors with recipients, no points | no | — |
| Teams & roster | Jason importing the War Week sign-up sheet in one go | yes | [features/people.md](features/people.md) |
| Hosts | Jason creating a competition and assigning its host before the week | yes | [features/competitions.md](features/competitions.md) |
| Pages | Jason writing the schedule, meals, FAQ, scoring overview and essentials for the week, as flexibly as the wiki | yes | — |
| Edition lifecycle | Jason creating War Week XII, running it, and ending it with a winner so it moves to the archive | yes | [features/editions.md](features/editions.md) |
| Archive | Anyone looking back at who won War Week IX and how | yes | [features/editions.md](features/editions.md) |
| Person page | A participant checking their results and the points they've contributed this week; anyone looking at everything one person has won across years | no | [features/people.md](features/people.md) |
| Organizer list | Jason adding Paul as an Organizer | no | — |
| Install to home screen | A participant adding the app to their phone's home screen for the week | no | — |

Core journeys get e2e coverage. The core functionality of each role is tested:
1. **Participant:** checks standings, results and match history on their phone; self-reports a match where allowed.
2. **Host:** records results; points land in standings.
3. **Organizer:** sets up an edition (teams, hosts, competitions, pages), runs it, ends it, and it lands in the archive.

## Non-functional
- Access is internal only: every page requires sign-in. Jahnel Group Google accounts first; LTI and InfoLink participants later (see Deferred).
- Error alerting and logs good enough to debug, per the small-group profile.

## Out of scope
- Anyone outside Jahnel Group and its War Week partner companies, and any event other than War Week.
- Marketing or "about" pages.
- Offline support.
- Team drafting. Teams are drafted outside the app and arrive through the sign-up sheet.

## Pitch to Jason
Ideas that need his yes before building.
- In-app sign-up and enrollment for competitions.
- Closing ceremonies run-through (finale slideshow) and a personal "War Week Wrapped" recap for each participant. Mocked in Claude Design for the pitch.
- Per-edition color theming. Mocked in Claude Design for the pitch.
- Accomplishments / immunity (lighter than awards; e.g. War Week X).
- Hosts creating their own competitions and setting their points.
- Stats and visualizations: scoring breakdowns, trends over the week, overall scores (Competiscore had this). Mocked in Claude Design for the pitch so it can get real feedback.

## Suggestions
Ideas from others at JG, captured with who suggested them. None yet.

## Deferred
Known future needs, not needed for the first version. The architecture must leave room for each of these without a rewrite, but none are built until approved.
- Sign-in for LTI and InfoLink participants, who have non-JG emails. Nothing in the first version may assume every user has a Jahnel Group email.
- League formats (Swiss, round robin) for chess and MTG.
- Best-of matches (e.g. a best-of-3 final).
- Chaining a qualifier into bracket seeding.
- A participation result auto-creating an award (e.g. Black Midnight).
- Backfilling editions before War Week XI.
- Image uploads (team logos, photos, edition banners). Likely returns with per-edition theming.

## Open questions
- **Partner sign-in:** how do LTI and InfoLink participants sign in (their own Google/Microsoft accounts, or something else)?
