# People

**Features:** Sign in, Partner sign-in, Teams & roster, Team view, Person page, Organizer list

## Rules

### People
- A person is a roster entry, owned by Organizers. A person can exist without an email and without ever signing in (e.g. Bucky the Horse); they can be entered by hosts but can't self-report.
- A person has at most one email, and no two people share one (compared ignoring case). Emails are visible to Organizers only (roster, import, editing a person); everywhere else, including hosts' pickers, people appear by name.
- A person's name is the one Organizers set, by import or by hand, and it's shown everywhere. People can't change their own.
- A person's avatar is the profile photo from their last sign-in, cleared when their email changes. Without one, it's their initials on their team's color in the edition being viewed, or neutral where there's no team (free-for-all, outside an edition).
- A person persists across years: each edition's roster reuses existing people, so history follows them.
- A person with anything recorded or assigned in an edition (results, attempts, completions, squads, subjective-point credit, a host role) can't be removed from its roster; the app shows where they appear. Someone who withdraws stays on the roster, and hosts handle their remaining matches.

### Sign in
- Sign-in links the account to the person whose email matches the account's verified email. The link follows the person's current email, so an email change takes effect immediately and the old account loses that person.
- If someone's email changes, an Organizer edits it. Changing the email of an Organizer or Host shows its own warning naming the access that moves (e.g. "This moves Paul's Organizer access to p.mcfarlane@…").
- Someone who signs in but matches no person can read the app as a User. During a Live edition, Home tells them: "You're not on the War Week XII roster. If you should be, ask an Organizer." People can't claim a person themselves.
- Manage shows Organizers sign-ins that matched no person and roster people (especially hosts) who have never signed in, so emails can be fixed before the week.

### Organizers
- An Organizer is a person who needn't be on any roster.
- The last Organizer can't be removed.

### Teams and roster
- In a team edition everyone on the roster is on a team, and nobody changes teams mid-week. Free-for-all editions have no teams.
- A team edition can set its own words for a team (singular and plural, e.g. House / Houses) and for a team leader (e.g. Tribal Chief). Blank means Team / Teams and Leader. The app uses them everywhere it names teams or leaders, including Manage.
- Each team has a name, a color from the app's fixed palette, and any number of leaders. A new team gets the next unused palette color. The color marks the team next to its name, never replaces it. Leaders are shown, not given extra permissions; anything they run, they run as a host.
- Teams and leaders can be edited in the app. Changing a person's team is a correction, not a transfer: Organizers can do it at any time, standings are recalculated with them on the new team, and the app shows each team's total before and after (e.g. "Red 412 → 398, Blue 390 → 404") before saving. A change that would split a squad across teams is blocked, naming the squad.

### Importing the sign-up sheet
- Jason pastes the sheet's rows, header included. Columns are matched by header name in any order: Name, Email, Team, Leader. Other columns are ignored. Any non-empty Leader value marks a leader. In free-for-all editions, Team and Leader are ignored.
- The app matches existing people by email, then name, and shows existing vs. new before anything is saved.
- Import adds and updates; it never removes. People on the roster but not in the paste are listed so Jason can remove them by hand.
- Import updates teams and leaders for people already on the roster only while the edition is in Setup. Once it's Live, import only adds new people; team changes are made by hand.

### Team view
- A team's view shows its color, leaders, members, and the points it earned in each competition and from subjective points.

### Person page
- Shows the person's results and the points they've contributed in the current edition (what counts is in [competitions.md](competitions.md#points-and-standings)), and across years: editions, team each year, 1st places and awards.
- No individual leaderboard in team editions.

## Edge cases
- **Name matches, email differs:** the import asks whether it's the same person. Yes updates the email; no creates a new person. It's never changed silently.
- **Email matches, name differs** (e.g. a married name): the sheet's name replaces the app's, shown in the preview.
- **Missing data:** every row needs a name, and in a team edition a team. Email is optional (e.g. Bucky the Horse). If a required column is missing the import says which and saves nothing; rows missing a required value are flagged in the preview.

## Open questions
None.
