# War Week requirements

Owned by Paul.

## Profile
- **Profile:** product, small group. First goal is a coherent version that gets Jason's buy-in.
- **Expected scale:** ~100–125 people per edition (Jahnel Group employees plus partner-company participants from LTI and InfoLink, about 20 in War Week XI). Both partner companies are under Jahnel Group ownership: their people can do everything JG employees can, and anyone at them may sign in. Intense for one week a year, near zero otherwise: it must be rock solid during War Week; the rest of the year only the archive needs to work.
- **Exceptions to the standards:** none.
- **Context that shapes priorities:**
  - **Next edition:** War Week XII is a free-for-all, so free-for-all scoring must be fully supported, not treated as an edge case. Partner sign-in must be in place before it.
  - **Pitch:** design only, nothing built. Jason sees the approved screens, then the proposals canvas: mockups of the Needs buy-in items marked "Mocked for the pitch", and the question after "Ask:" for each of them. Building starts after his feedback is in the docs.
  - **Check-in:** once built, Jason sees the core journeys working on War Week XI data (Paul supplies the data in the work package that builds the archive).
  - **Timeline:** pitch in the week of 12 or 19 October 2026; build in the following week or two; then the check-in. Timeline doesn't drive tech choices; the goal is something Paul believes in, shown early enough to get feedback.

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
- **Design system:** [War Week design system](https://claude.ai/artifact/LqzxzyrRyqLSR2hswxjoW2) (Claude Design). Screens per feature are linked from each feature doc. Proposals for the Needs buy-in items: [proposals canvas](https://claude.ai/artifact/4MsEVNtGypnZ179EFXkwkg).

## App-wide rules

### Roles
- **Organizer:** runs the whole edition (Jason, Paul). Manages the Organizer list.
- **Host:** runs one or more competitions (e.g. a pool tournament host), as set out in [competitions.md](features/competitions.md#setup). Assigned by an Organizer.
- **User:** anyone who signs in. Users can read everything except Setup editions ([editions.md](features/editions.md#lifecycle)) and emails ([people.md](features/people.md#people)).
- **Participant:** a person on the edition's roster. Participants who are also users can self-report results where a host allows it.

### Navigation
Home, Competitions, Info and Archive for everyone; Manage for Organizers (editions, teams and roster, competitions and hosts, subjective points, awards, Organizer list). Things are edited where they live: a host records on the match, an Organizer edits a page from the page. Person pages are reached from standings and team member lists, your own from your avatar menu; names mentioned in passing (a host, an award recipient, a subjective-points entry, an entrant list) are plain text, and a row whose job is something else (a match, a picker result) does that job. A tap does one predictable thing: standings and team lists are where people go looking for a person, and making every name a link would put a second target inside rows that already do something. Team views are reached by tapping a team. Your avatar opens a small menu: your own page, theme (System, Dark or Light; System follows the phone), Install app (on phones, until installed) and Sign out.

### Structured vs. pages
Structured data only where the app computes something or it's history people care about: editions, teams and roster, competitions, matches, results, points, standings, awards. Everything else is an Organizer-written page (rich text and links, no images), listed under Info in the order Organizers set (e.g. schedule above FAQ). JG branding ships with the app. Sign-up forms and similar stay as external links in pages.

### Saving
Settings and edits save as you make them; there's no Save button to miss. Recording a result, giving or editing subjective points, creating something new and anything destructive (delete, end, remove) are explicit actions.

### Times
Every time is shown in Eastern Time, matching the schedule pages.

## Features

| Feature | Use case (who, when) | Detail | Status |
|---|---|---|---|
| Sign in | Any employee opening the app with their Jahnel Group Google account | [features/people.md](features/people.md) | todo |
| Partner sign-in | An LTI or InfoLink participant opening the app during War Week XII | [features/people.md](features/people.md) | todo |
| Home | Anyone opening the app to see what needs them and where they stand | [features/editions.md](features/editions.md) | todo |
| Standings | A participant on Tuesday night checking which team is ahead | [features/competitions.md](features/competitions.md) | todo |
| Competitions & results | A host recording a bracket match as it finishes | [features/competitions.md](features/competitions.md) | todo |
| Match history | A pool player checking how the other side of the bracket is going; someone who missed Tournament Night looking up how the Smash bracket played out | [features/competitions.md](features/competitions.md) | todo |
| Self-entry | A player entering the pool bracket from their phone, so the host doesn't have to chase who's in | [features/competitions.md](features/competitions.md) | todo |
| Self-report | A player in a large tournament reporting their own match so the host doesn't have to chase every result | [features/competitions.md](features/competitions.md) | todo |
| Subjective points | Jason awarding spirit or bonus points, with a reason, outside any competition | [features/competitions.md](features/competitions.md) | todo |
| Awards | Jason entering MVPs, Top Biller and Black Midnight finishers after closing ceremonies | [features/editions.md](features/editions.md) | todo |
| Teams & roster | Jason importing the War Week sign-up sheet in one go | [features/people.md](features/people.md) | todo |
| Team view | A participant on day one seeing who's on their team and who leads it | [features/people.md](features/people.md) | todo |
| Hosts | Jason creating a competition and assigning its host before the week | [features/competitions.md](features/competitions.md) | todo |
| Pages | Jason writing the schedule, meals, FAQ, scoring overview and essentials for the week, as flexibly as the wiki | [features/editions.md](features/editions.md) | todo |
| Edition lifecycle | Jason creating War Week XII, running it, and ending it with a winner so it moves to the archive | [features/editions.md](features/editions.md) | todo |
| Archive | Anyone looking back at who won War Week IX and how | [features/editions.md](features/editions.md) | todo |
| Person page | A participant checking their results and the points they've contributed this week; anyone looking at everything one person has won across years | [features/people.md](features/people.md) | todo |
| Organizer list | Jason adding Paul as an Organizer | [features/people.md](features/people.md) | todo |
| Install to home screen | A participant adding the app to their phone's home screen for the week | [features/editions.md](features/editions.md) | todo |

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
- People search. Organizers and hosts find people through pickers; person pages are reached as Navigation describes.
- Notifications (push, email or in-app). Announcements stay in Slack; Home shows what needs you.
- Accomplishments / immunity (lighter than awards, as in War Week X).
- A "War Week Wrapped" recap. The person page already shows a person's week.

## Needs buy-in
Ideas that need Jason's yes before building.
- In-app sign-up for War Week, replacing the sign-up sheet. Ask: is the sign-up sheet a pain, and how would you draft teams without it?
- Running closing ceremonies from the app. Free-form slides belong in Google Slides. Ask: how do you run closing ceremonies today, and is anything painful?
- Per-edition theme: Organizers pick a color from a short list of presets, each checked for contrast in dark and light, an optional matching background tint, and a headline font. JG logo, body text and layout don't change. Trades some JG branding consistency for each year's flair. Mocked for the pitch. Ask: do you want each War Week to look different in the app?
- Hosts creating their own competitions and setting their points. Trades Organizers' single view of point balance for less setup work for Jason. Ask: should hosts add their own competitions and set points, or only Organizers?
- Stats: the standings race over the week (below standings, live and archived; free-for-all shows the top 5 plus you), and all-time records across editions (most 1st place finishes, most awards). A day's points are those recorded that day (ET). Mocked for the pitch. Ask: mid-week, do people ask who's catching up, and would they look at all-time records?
- Hidden drafts: preparing pages, competitions or subjective points privately in a Live edition (e.g. secret Team Night events) and revealing them later. Standings are never hidden. Ask: has anything had to stay secret until it was revealed?
- Negative subjective points (penalties). Ask: has a team or person ever lost points?

## Suggestions
Ideas from others at JG, captured with who suggested them. None yet.

## Deferred
Known future needs, not built yet.
- League formats (Swiss, round robin) for chess and MTG.
- Best-of matches (e.g. a best-of-3 final).
- Chaining a qualifier into bracket seeding.
- A participation result auto-creating an award (e.g. Black Midnight).
- Backfilling editions before War Week XI.
- Image uploads (team logos, edition banners, people uploading their own photo).
- Display names people set for themselves.

## Open questions
- **Partner sign-in:** which accounts (Google, Microsoft or other) and email domains do LTI and InfoLink participants sign in with? Paul finds out from each company; it isn't a question for Jason.
