# People

**Features:** Sign in, Partner sign-in, Teams & roster, Team view, Person page, Organizer list, Install to home screen

## Screens
Approved in the [screens canvas](https://claude.ai/artifact/JNYqMR3uwFtcJrrRYv98eo): Participant page (sign in, team view, person page, your menu, install tip and sheets); Organizer page, People row (roster, import, person and team edits, blocked removals) and Organizers row.

## Rules

### People
- A person is a roster entry, owned by Organizers. A person can exist without an email and without ever signing in (e.g. Bucky the Horse); they can be entered by hosts but can't record their own results.
- A person has at most one email, and no two people share one (compared ignoring case). Emails are visible to Organizers only (roster, import, editing a person); everywhere else, including hosts' pickers, people appear by name.
- A person's name is the one Organizers set, by import or by hand, and it's shown everywhere. People can't change their own yet; display names they set themselves are planned before War Week XII ([requirements](../requirements.md#before-war-week-xii)).
- A person's avatar is the profile photo from their last sign-in, cleared when their email changes. Without one, it's their initials on their team's color in the edition being viewed, or neutral where there's no team (free-for-all, outside an edition).
- A person persists across years: each edition's roster reuses existing people, so history follows them.
- A person with anything recorded or assigned in an edition (results, attempts, completions, squads, subjective-point credit, an award, a host role) can't be removed from its roster; the app shows where they appear. Someone who withdraws stays on the roster, and hosts handle their remaining matches.

### Sign in
- Only accounts with a Jahnel Group, LTI or InfoLink email can sign in (which partner accounts is an [open question](../requirements.md#open-questions)). Anyone else is told so on the sign-in screen, with who to ask.
- After signing in, you land on the page you opened, or Home if you can't see it, so a shared link (e.g. a competition to enter) works for someone not yet signed in.
- Sign-in links the account to the person whose email matches the account's verified email. The link follows the person's current email, so an email change takes effect immediately and the old account loses that person.
- If someone's email changes, an Organizer edits it. Changing the email of an Organizer or Host, whether by editing, linking a sign-in or importing, shows its own warning naming the access that moves (e.g. "This moves Paul's Organizer access to p.mcfarlane@…").
- Someone who signs in but matches no person can read the app as a User, and has no "Your page". During a Live edition, Home tells anyone not on its roster (Organizers and hosts excepted): "You're not on the War Week XII roster. If you should be, ask an Organizer." People can't claim a person themselves.
- Manage shows Organizers sign-ins that matched no person and roster people (especially hosts) who have never signed in, so emails can be fixed before the week.

### Organizers
- An Organizer is a person who needn't be on any roster.
- The last Organizer can't be removed.

### Teams and roster
- In a team edition everyone on the roster is on a team. Free-for-all editions have no teams.
- A team edition can set its own words for a team (singular and plural, e.g. House / Houses) and for a team leader (singular and plural, e.g. Tribal Chief / Tribal Chiefs). Blank means Team / Teams and Leader / Leaders. The app uses them everywhere it names teams or leaders, including Manage.
- Each team has a name, a color from the app's fixed palette that no other team in the edition uses, and any number of leaders, who are members of the team and are set from the team. An edition has at most as many teams as the palette has colors (8). A new team gets the next unused palette color. A team with no members can be deleted. The color marks the team next to its name, never replaces it. Leaders are shown, not given extra permissions; anything they run, they run as a host.
- Teams and leaders can be edited in the app. People rarely change teams mid-week, but Organizers can move someone at any time, whether fixing a mistake or a real move. Their points ([a person's points](competitions.md#points-and-standings)) go with them: standings, including Participation headcounts and percentages, are recalculated as if they'd always been on the new team, and the app shows each team's total before and after (e.g. "Red 58 → 55, Blue 54 → 57") before saving. A change that would split a squad across teams is blocked, naming the squad.

#### Importing the sign-up sheet
- Jason pastes the sheet's rows, header included. Columns are matched by header name in any order, ignoring case and extra words (e.g. "Email Address"): Name, Email, Team, Leader. Other columns are ignored. If no Email column is found, the preview says so. Yes, Y, True, X or 1 in Leader marks a leader; No, False, 0 or blank doesn't. In free-for-all editions, Team and Leader are ignored.
- The app matches existing people by email, then name, and shows existing vs. new before anything is saved. Names match ignoring case, spacing and apostrophe style. Teams named in the sheet that don't exist yet are listed as new teams in the preview.
- Import adds and updates; it never removes. People on the roster but not in the paste are listed so Jason can remove them by hand.
- Import is available while the edition is in Setup or Live, so people who join after points start counting (e.g. new hires during War Week XII's three months) can come in from an updated sheet. It still only adds and updates. In a Live team edition, a sheet that would move someone to a different team shows the same before-and-after totals as moving them by hand. People can also be added and edited by hand: adding a person by hand searches everyone in the app first; "Add someone new" only if they're not there.

### Team view
- A team's view shows its color, leaders, members ranked by the points each has contributed (then by name), and its total.

### Person page
- Shows the person's results and the points they've contributed in the current edition (what counts is in [competitions.md](competitions.md#points-and-standings)), grouped as on the Competitions tab ([In progress, Not started, Finished](competitions.md#competitions-list)), then the subjective points naming them; and across years: editions, team each year, 1st place finishes they can be tied to (as for a person's points) and awards.
- No edition-wide individual leaderboard in team editions; a team's member list is the only place its members are ranked.

### Install to home screen
- The app can be added to a phone's home screen as "War Week" with the JG logo. It opens to Home.
- On a phone where it isn't installed, the avatar menu has **Install app**. It shows the steps for that phone: one tap on Android; Share, then Add to Home Screen on iPhone. Inside another app's browser (e.g. Slack) it first says to open the page in Safari or Chrome.
- While an edition is Live, Home shows a one-line tip pointing to Install app until it's installed or dismissed. Dismissing is remembered on that phone.
- Nothing about installing shows once it's installed, or on a computer.

## Edge cases
- **Name matches, email differs:** the import asks whether it's the same person. Yes updates the email; no creates a new person. It's never changed silently.
- **Name matches a person with no email** (e.g. someone loaded from the archive): matched; the sheet's email is added, shown in the preview.
- **Ambiguous rows:** a name matching more than one person, or two rows sharing an email, is flagged in the preview and not imported until fixed.
- **Email matches, name differs** (e.g. a married name): the sheet's name replaces the app's, shown in the preview.
- **Missing data:** every row needs a name, and in a team edition a team. Email is optional (e.g. Bucky the Horse). If a required column is missing the import says which and saves nothing; rows missing a required value are flagged in the preview.

## Open questions
None.
