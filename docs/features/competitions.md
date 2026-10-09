# Competitions

**Features:** Competitions & results, Hosts, Self-report, Match history, Standings
**Core journey:** yes (participant views and self-reports, host records, organizer sets up)
**Design:** <Claude Design link, TBD>

Priorities, in order: easy for participants, hosts and organizers, then flexible. Simple choices in front, one flexible model behind.

Background: Paul's [mapping of past competitions to formats](https://app.notion.com/p/JG-War-Week-App-Assess-if-current-game-types-match-what-is-needed-3efc4dbb621780e99537fab116f3c14e) (Notion). This spec stands on its own; see [Examples](#examples) for what each named competition was.

## Formats
A host picks one of six formats. The first four are all rounds of matches, where each match ranks its entrants.

| Format | What it is | Examples |
|---|---|---|
| **Ranking** | One match, all entrants ranked | Memes, billable hours, beer cans, a Team Night event |
| **Bracket** | Single elimination, 2 per match, winner advances | Pool, Smash, Beyblade finals |
| **Heats** | Heats of several entrants, top N advance, until a winner | Catan, Beer & Cards, Mario Kart, group stage then knockout |
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
- Each competition sets its entrant type: **individuals**, **squads** or **teams**. Every entrant in a competition is that type; an individual never faces a squad or a team. Any format can use any entrant type.
- A squad can be any size. Hosts create squads inline by picking members.
- In team editions, a squad's members must all be on the same team.
- **Ranking, Bracket, Heats, Survival** have an entrant list, built from the roster. "Add everyone" adds anyone not already in; pressing it again after roster changes adds only the missing people. Entrants can be removed.
- **Participation and Best score** have no entrant list. Anyone on the roster (or any squad, for squad competitions) can be marked done or log a score.
- No late-entry feature. Hosts can edit any match's entrants by hand, which covers late arrivals.

## Building matches
- The app builds the first round automatically when the host starts the competition. Order is random by default; the host can reorder before starting.
- **Bracket:** byes go to the top of the order when the count isn't a power of two. Optional "Play a 3rd place match" (off by default); when off, semifinal losers tie for 3rd, quarterfinal losers tie for 5th, and so on.
- **Heats:** the host picks a heat size and how many advance; the app splits entrants as evenly as possible (uneven heats allowed). Heat size can change between rounds (e.g. heats of 4, then a final heat). The host can move entrants between heats before play.
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
- **A person's points** (person page, team editions) are the points they can be concretely tied to: their own placings, their squad's points (full to each member), Survival team points for the best-placed member, and Participation completions, including team rankings by headcount or percentage (credited to each person who completed). Team-entrant results show on members' pages but don't count toward their points.
- **Standings** show ranked totals (teams, or individuals in free-for-all, where your own row is easy to find) and every competition's status, point value and where its points went, with subjective points and their reasons. Seeing every point value in one place lets Organizers keep points balanced.

## Finishing
- Bracket, Heats and Survival finish when the final match is recorded; Ranking when the order is entered. Points land immediately.
- Participation and Best score are open-ended: a host or Organizer taps **Finish**, or the edition ends ([editions.md](editions.md#lifecycle)). Until then their points show in standings as **in progress**.
- No close/reopen ceremony. Editing a finished competition updates points and standings recalculate.

## Ties that block advancement
In Heats, Survival or a Best score cutoff, the app flags the tie and the host picks who advances. No automatic tie-break rules.

## Corrections
Hosts and Organizers can edit anything in their competitions. Once the edition ends, only Organizers can. Every result shows who recorded or changed it.

## Examples
Past War Week competitions named in this spec.
- **Memes:** live meme showdown; teams ranked by vote.
- **Billable hours:** teams ranked by billable hours (or % of their usual hours).
- **Beer cans:** teams ranked by how many cans they added to the office beer can collection.
- **Team Night events:** a series of small head-to-head events on Team Night, each one group (or whole team) vs. another, each worth its own points.
- **Pool, Smash:** classic single-elimination 1v1 brackets.
- **Beyblade:** a qualifier ranked by best rips, then a finals bracket.
- **Bouncy Pong:** pairs; a qualifier ranked by best score, then finals between squads.
- **Catan:** tables of 4–5 players, each table's winner advances to a final table.
- **Beer & Cards, Mario Kart:** groups of uneven size, top finishers advance to a final group.
- **Ultimate Survivor (2025):** nearly everyone in one pool; each round a different challenge, some eliminated each round, until one winner.
- **Tri-Wizard (2023):** each house entered its 12 best into an elimination-style challenge; houses scored by their best finisher's place.
- **Steak wall (2025):** eat as many as you can; a best-score event.
- **Midnight Club / Black Midnight:** work from 12:00 AM to noon Sunday; points per finisher or teams ranked by headcount.
- **Beast Mode:** a morning workout; points for completing it.
- **Black Tuesday:** a focused, no-nonsense work day; in 2024 points by tier for 12, 15 or 18 hours.
- **AI survey (2026):** team with the highest completion percentage wins.
