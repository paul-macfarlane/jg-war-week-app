# People

**Features:** Teams & roster, Person page
**Core journey:** yes (Organizer sets up teams and roster)
**Design:** <Claude Design link, TBD>

## Rules

### People
- A person is a roster entry, owned by Organizers. A person can exist without an email and without ever signing in (e.g. Bucky the Horse); they can be entered by hosts but can't self-report.
- A person has one email. Signing in links the account to the person with that email. If someone's email changes, an Organizer edits it.
- A person persists across years: each edition's roster reuses existing people, so history follows them.

### Teams and roster
- In a team edition everyone on the roster is on a team, and nobody changes teams mid-week. Free-for-all editions have no teams.
- Teams and leaders can be edited in the app. Changing a person's team is a correction, not a transfer: Organizers can do it at any time, standings are recalculated with them on the new team, and the app shows each team's total before and after (e.g. "Red 412 → 398, Blue 390 → 404") before saving. A change that would split a squad across teams is blocked, naming the squad.

### Importing the sign-up sheet
- Jason pastes the sheet's rows, header included. Columns are matched by header name in any order: Name, Email, Team, Leader. Other columns are ignored. Any non-empty Leader value marks a leader. In free-for-all editions, Team and Leader are ignored.
- The app matches existing people by email, then name, and shows existing vs. new before anything is saved.
- Import adds and updates; it never removes. People on the roster but not in the paste are listed so Jason can remove them by hand.
- Import updates teams and leaders for people already on the roster only while the edition is in Setup. Once it's Live, import only adds new people; team changes are made by hand.

### Person page
- Shows the person's results and the points they've contributed in the current edition (what counts is in [competitions.md](competitions.md#points-and-standings)), and across years: editions, team each year, 1st places and awards.
- No individual leaderboard in team editions.

## Edge cases
- **Name matches, email differs:** the import asks whether it's the same person. Yes updates the email; no creates a new person. An email decides who can sign in as that person, so it's never changed silently.
- **Missing data:** every row needs a name, and in a team edition a team. Email is optional (e.g. Bucky the Horse). If a required column is missing the import says which and saves nothing; rows missing a required value are flagged in the preview.

## Open questions
None.
