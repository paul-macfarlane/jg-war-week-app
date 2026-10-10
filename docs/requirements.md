# War Week requirements

Owned by Paul.

## Profile
- **Profile:** product, small group. First goal is a coherent version that gets Jason's buy-in.
- **Expected scale:** ~100–125 people per edition (Jahnel Group employees plus partner-company participants from LTI and InfoLink). Intense for one week a year, near zero otherwise: it must be rock solid during War Week; the rest of the year only the archive needs to work.
- **Exceptions to the standards:** none.
- **Context that shapes priorities:**
  - **Next edition:** War Week XII is a free-for-all, so free-for-all scoring must be fully supported, not treated as an edge case. Partner sign-in must be in place before it.
  - **Pitch demo:** the core journeys working on War Week XI data (Paul supplies the data in the work package that builds the archive), plus Claude Design mockups for the visual Needs buy-in items. Partner sign-in isn't part of the pitch.
  - **Timeline:** pitch to Jason targeted for end of October 2026. Timeline doesn't drive tech choices; the goal is something Paul believes in, shown early enough to get feedback.

## Purpose
During War Week, one place where employees see what's happening, the schedule and the standings, and where organizers and hosts record results so standings stay live. After the week, it keeps the history.

It must be **easy to use for everyone: participants, hosts and organizers.** Participants find what they need in a tap or two on their phone, hosts record results in seconds, and running War Week in the app is less work for Jason than the wiki was. If any of the three finds it harder than what they did before, it fails.

### Problems it solves
1. Hosts track results separately and report back to Jason, who then records them.
2. Participants don't have a good sense of the live score.
3. Match history is hard to find, whether you're in the event (how is the other side of my bracket going?) or not.
4. History gets lost over time when the wiki isn't kept up and things are scattered.

## Character
- Feels like War Week: competitive, a little irreverent, Jahnel Group through and through.
- JG branding is the baseline look. Each edition's theme comes through in its theme name, in naming (what teams are called, e.g. Houses, Tribes) and in the pages Organizers write.
- Copy is plain and direct. No marketing voice.

## Design
- **Design system:** <Claude Design link, TBD>
- **Screens:** <Claude Design links, TBD>

## App-wide rules

### Roles
- **Organizer:** runs the whole edition (Jason, Paul). Manages the Organizer list.
- **Host:** runs one or more competitions (e.g. a pool tournament host), as set out in [competitions.md](features/competitions.md#setup). Assigned by an Organizer.
- **User:** anyone who signs in. Users can read everything except Setup editions ([editions.md](features/editions.md#lifecycle)) and emails ([people.md](features/people.md#people)).
- **Participant:** a person on the edition's roster. Participants who are also users can self-report results where a host allows it.

### Navigation
Home, Competitions, Info and Archive for everyone; Manage for Organizers (editions, teams and roster, competitions and hosts, subjective points, awards, Organizer list). Things are edited where they live: a host records on the match, an Organizer edits a page from the page. Person pages are reached by tapping a name, your own from your avatar; team views by tapping a team.

### Structured vs. pages
Structured data only where the app computes something or it's history people care about: editions, teams and roster, competitions, matches, results, points, standings, awards. Everything else is an Organizer-written page (rich text and links, no images), listed under Info in the order Organizers set (e.g. schedule above FAQ). JG branding ships with the app. Sign-up forms and similar stay as external links in pages.

### Times
Every time is shown in Eastern Time, matching the schedule pages.

## Features

| Feature | Use case (who, when) | Detail |
|---|---|---|
| Sign in | Any employee opening the app with their Jahnel Group Google account | [features/people.md](features/people.md) |
| Partner sign-in | An LTI or InfoLink participant opening the app during War Week XII | — |
| Home | Anyone opening the app to see what needs them and where they stand | [features/editions.md](features/editions.md) |
| Standings | A participant on Tuesday night checking which team is ahead | [features/competitions.md](features/competitions.md) |
| Competitions & results | A host recording a bracket match as it finishes | [features/competitions.md](features/competitions.md) |
| Match history | A pool player checking how the other side of the bracket is going; someone who missed Tournament Night looking up how the Smash bracket played out | [features/competitions.md](features/competitions.md) |
| Self-report | A player in a large tournament reporting their own match so the host doesn't have to chase every result | [features/competitions.md](features/competitions.md) |
| Subjective points | Jason awarding spirit or bonus points, with a reason, outside any competition | [features/competitions.md](features/competitions.md) |
| Awards | Jason entering MVPs, Top Biller and Black Midnight finishers after closing ceremonies | [features/editions.md](features/editions.md) |
| Teams & roster | Jason importing the War Week sign-up sheet in one go | [features/people.md](features/people.md) |
| Team view | A participant on day one seeing who's on their team and who leads it | [features/people.md](features/people.md) |
| Hosts | Jason creating a competition and assigning its host before the week | [features/competitions.md](features/competitions.md) |
| Pages | Jason writing the schedule, meals, FAQ, scoring overview and essentials for the week, as flexibly as the wiki | [features/editions.md](features/editions.md) |
| Edition lifecycle | Jason creating War Week XII, running it, and ending it with a winner so it moves to the archive | [features/editions.md](features/editions.md) |
| Archive | Anyone looking back at who won War Week IX and how | [features/editions.md](features/editions.md) |
| Person page | A participant checking their results and the points they've contributed this week; anyone looking at everything one person has won across years | [features/people.md](features/people.md) |
| Organizer list | Jason adding Paul as an Organizer | [features/people.md](features/people.md) |
| Install to home screen | A participant adding the app to their phone's home screen for the week | — |

Several rows can share one feature doc.

## Non-functional
- Access is internal only: every page requires sign-in. Nothing may assume every user has a Jahnel Group email.
- A request to remove a person's data is handled manually by the database owner (e.g. name replaced, email cleared, results kept so team history still adds up).

## Out of scope
- Anyone outside Jahnel Group and its War Week partner companies, and any event other than War Week.
- Marketing or "about" pages.
- Offline support.
- Team drafting. Teams are drafted outside the app and arrive through the sign-up sheet.
- Copying an edition forward. Each year is different; text worth keeping is copied from the archived page.
- People search. Organizers and hosts find people through pickers; names elsewhere link to person pages.
- Notifications (push, email or in-app). Announcements stay in Slack; Home shows what needs you.

## Needs buy-in
Ideas that need Jason's yes before building.
- In-app sign-up and enrollment for competitions.
- Closing ceremonies run-through (finale slideshow) and a personal "War Week Wrapped" recap for each participant. Mocked in Claude Design for the pitch.
- Per-edition color theming. Mocked in Claude Design for the pitch.
- Accomplishments / immunity (lighter than awards; e.g. War Week X).
- Hosts creating their own competitions and setting their points.
- Stats and visualizations: scoring breakdowns, trends over the week, overall scores (Competiscore had this), all-time leaderboards across editions. Mocked in Claude Design for the pitch so it can get real feedback.
- Hidden drafts: preparing pages, competitions or subjective points privately in a Live edition (e.g. secret Team Night events) and revealing them later. Standings are never hidden.
- Negative subjective points (penalties).

## Suggestions
Ideas from others at JG, captured with who suggested them. None yet.

## Deferred
Known future needs, not built yet.
- League formats (Swiss, round robin) for chess and MTG.
- Best-of matches (e.g. a best-of-3 final).
- Chaining a qualifier into bracket seeding.
- A participation result auto-creating an award (e.g. Black Midnight).
- Backfilling editions before War Week XI.
- Image uploads (team logos, edition banners, people uploading their own photo). Likely returns with per-edition theming.
- Display names people set for themselves.

## Open questions
- **Partner sign-in:** how do LTI and InfoLink participants sign in (their own Google/Microsoft accounts, or something else)?
