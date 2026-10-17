# Editions

**Features:** Edition lifecycle, Home, Archive, Awards, Pages, Export

## Core journey
**Organizer:** sets up an edition (teams, hosts, competitions, pages), makes it Live, runs it, ends it, and it lands in the archive.

## Screens
Approved in the [screens canvas](https://claude.ai/artifact/JNYqMR3uwFtcJrrRYv98eo): Participant page (Home in every state, Info, Archive); Organizer page, Edition row (lifecycle, end, transitions, winner change) and Points and awards row (awards). Wider-screen versions sit next to their phone screens.

## Rules

### Lifecycle
- An edition has a unique number (e.g. XII), and optionally a theme name (e.g. Survivor) and the date War Week starts, and is either teams or free-for-all, changeable only in Setup. Editions are ordered by number. Wherever an edition is named in a header or the Archive, its theme name and year (from its start date) show with its number, when set.
- An edition is **Setup**, **Live** or **Ended**. An Organizer moves it between them.
  - **Setup:** nothing from it is shown to, or changeable by, anyone but Organizers, including hosts, person pages and Home. Jason builds teams, competitions and pages before anyone sees them.
  - **Live:** visible to everyone, and anything saved shows immediately. Usually from when teams are announced, weeks before the week itself, so hosts can set up and run qualifiers; or from when points start counting, months before (War Week XII is Live from mid-November).
  - **Ended:** in the archive. Organizers can still edit it (e.g. entering awards); hosts and participants are read-only.
- One edition is Live at a time. A Setup edition can exist alongside Live and Ended ones. A Setup edition can be deleted (e.g. created by mistake); the app shows what goes with it, and deleting is confirmed and permanent.
- **Live → Setup** is allowed while nothing is recorded in it: no results, marks, attempts, entries or subjective points (e.g. made Live too early). Competitions can still be created and edited while Live.
- **Setup → Ended** happens only when a past edition is backfilled by import ([architecture.md](../architecture.md)), so it's never public half-built. The app doesn't offer it.
- **Ending** a Live edition finishes any open Ranking and Participation competitions; their current points become final. Unfinished Bracket, Heats and Survival competitions stay unfinished (their decided places still count; see [competitions.md](competitions.md#points-and-standings)) until an Organizer records the rest. Before confirming, the Organizer sees what's still open, what ending will do, and who wins.
- **Ended → Live** is allowed for the highest-numbered edition (e.g. ended by mistake mid-week) if no other edition is Live. Competitions finished by ending stay finished. Hosts and participants get back what they have in any Live edition.

#### Winner
- The winner is first place in the edition's standings; a tie shows co-winners. (With tiers, a proposal under [Needs buy-in](../requirements.md#needs-buy-in), the winners are the tier finals' winners instead.)
- An Organizer edit to an Ended edition that would change who's first is confirmed first, showing the before and after (e.g. "This makes Blue the winner instead of Red").

### Awards
- Organizers enter an edition's awards (e.g. MVPs, Top Biller, Black Midnight finishers): honors with recipients, no points.
- An award has a free-text name (e.g. "Red MVP", "Top Biller – 1st") and an optional one-line description. Recipients are people on the edition's roster.
- An edition's awards show with its standings once it has any.

### Home
- Home shows the current edition: the Live one, else the highest-numbered Ended one.
- At the top, only when it has something in it: the competitions you host and your open matches where you can record your own result (a Ranking once you have a score in it).
- Then the standings ([competitions.md](competitions.md#points-and-standings)). An Ended edition shows its winner.

### Pages
- Every page belongs to one edition. Organizers create, rename, reorder and delete pages; deleting is confirmed and permanent.
- Info shows the current edition's pages.

### Export
- Organizers download an edition's data from Manage, Live or Ended, as a spreadsheet: the standings, every competition's places and points, subjective points with their groups and reasons, and awards. It's for Jason's closing ceremony slides and anything else he builds outside the app; which columns he wants is a [question for Jason](../requirements.md#questions-for-jason).

### Archive
- Lists every Ended edition by number. Opening one shows the same screens as the current edition (standings and winner, competitions, pages).

## Edge cases
None yet.

## Open questions
None.
