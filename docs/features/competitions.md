# Competitions

**Use case:** Hosts run their events and record results as they happen; everyone sees results, match history and standings live.
**Core journey:** yes (participant views and self-reports, host records, organizer sets up)
**Design:** <Claude Design link, TBD>

Priorities, in order: easy for hosts and participants, then flexible. Simple choices in front, one flexible model behind.

## Formats
A host picks one of six formats. The first four are all rounds of matches, where each match ranks its entrants.

| Format | What it is | Examples |
|---|---|---|
| **Ranking** | One match, all entrants ranked | Memes, billable hours, beer cans, a Team Night event |
| **Bracket** | Single elimination, 2 per match, winner advances | Pool, Smash, Beyblade finals |
| **Heats** | Tables of several entrants, top N advance, until a winner | Catan, Beer & Cards, Mario Kart, group stage then knockout |
| **Survival** | Everyone in one pool, some eliminated each round; each round can have a description | Ultimate Survivor, Tri-Wizard |
| **Best score** | Attempts, ranked by score; optionally top N advance | Beyblade and Bouncy Pong qualifiers, the steak wall |
| **Participation** | Who completed it | Midnight Club, Beast Mode, Black Tuesday, AI survey |

Subjective points and awards are not competitions. Events that aren't competitions live on the schedule page.

## Setup
- **Organizers** create competitions, set the points and assign hosts. A competition can have several hosts, chosen from the roster.
- **Hosts** set the format, rules, entrants and self-report switch, and record results. Organizers can do anything a host can.
- Competitions can award no points (e.g. qualifiers).
- The format is fixed once the first match is played. Points and rules can change any time.
- **Deleting:** Organizers only. Before deleting, the app shows the impact (matches and points removed, and from whom). Deletion is permanent.

## Entrants
- An entrant is an individual, a squad or a whole team. Squads can enter any format. Hosts create squads inline by picking members.
- In team editions, a squad's members must all be on the same team.
- **Ranking, Bracket, Heats, Survival** have an entrant list, built from the roster. "Add everyone" adds anyone not already in; pressing it again after roster changes adds only the missing people. Entrants can be removed.
- **Participation and Best score** have no entrant list. Anyone on the roster (or any squad) can be marked done or log a score.
- No late-entry feature. Hosts can edit any match's entrants by hand, which covers late arrivals.

## Building matches
- The app builds the first round automatically when the host starts the competition. Order is random by default; the host can reorder before starting.
- **Bracket:** byes go to the top of the order when the count isn't a power of two. Optional "Play a 3rd place match" (off by default); when off, semifinal losers tie for 3rd, quarterfinal losers tie for 5th, and so on.
- **Heats:** the host picks a table size and how many advance; the app splits entrants as evenly as possible (uneven tables allowed). Table size can change between rounds (e.g. groups, then a final table). The host can move people between tables before play.
- Later rounds fill in automatically as results come in.

## Recording results
- Each competition sets how a match is decided: **higher score wins**, **lower score wins**, or **finishing order**.
- With scores, the host enters only scores and the order follows. Manual ordering is only needed for tied scores or when there are no scores.
- Bracket matches can't tie; the host picks a winner.
- **Best score:** each competition sets the team (or squad) total as **sum of all members** or **best member**.
- **Participation:** individual completion, optionally with **tiers** that earn different points (e.g. Black Tuesday 12/15/18 hours). Team scoring is one of: **points per finisher**, **teams ranked by headcount**, or **teams ranked by percentage of team**.

## Self-report
- The host turns it on per competition; off by default.
- In match formats, anyone in the match (including any squad member) can report it. In Participation, participants mark themselves done; in Best score, they log their own attempts. Participants can only report for themselves.
- Reports count immediately. No opponent confirmation, disputes or approval queue. The honor system applies; hosts correct mistakes.

## Points and standings
- Points are set per place (e.g. 5/3/1). Places beyond the list earn 0.
- **Ties** share the place and each get its full points; the next place is skipped (1st, 1st, 3rd).
- **Team editions:** points go to the team. An individual's points count for their team.
- **Free-for-all editions:** points go to individuals. Each member of a squad gets the squad's full points.
- **Survival with team points:** each team scores by its best-placed member.
- Standings show every competition's point value in one place so Organizers can keep points balanced.

## Finishing
- Bracket, Heats and Survival finish when the final match is recorded; Ranking when the order is entered. Points land immediately.
- Participation and Best score are open-ended: a host or Organizer taps **Finish**. Until then their points show in standings as **in progress**.
- No close/reopen ceremony. Editing a finished competition updates points and standings recalculate.

## Ties that block advancement
In Heats, Survival or a Best score cutoff, the app flags the tie and the host picks who advances. No automatic tie-break rules.

## Corrections
Hosts and Organizers can edit anything in their competitions. Every result shows who recorded or changed it.
