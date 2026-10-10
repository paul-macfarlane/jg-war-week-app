# Competitions

**Features:** Competitions & results, Hosts, Self-report, Match history, Standings, Subjective points

Priorities, in order: easy for participants, hosts and organizers, then flexible. Simple choices in front, one flexible model behind.

See [Examples](#examples) for what each named competition was.

## Core journey
1. **Participant:** checks standings, results and match history on their phone; self-reports a match where allowed.
2. **Host:** records a result; points land in standings.

## Rules

### Formats
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

### Setup
- **Organizers** create competitions, set the points, set their order, assign hosts and delete competitions. A competition can have several hosts, chosen from the roster.
- **Hosts** set the format, rules, entrants and self-report switch, and record every result in their competitions, including ones they took part in. Organizers can do anything a host can.
- Rules are optional, in the same restricted rich text as pages ([requirements](../requirements.md#structured-vs-pages)).
- Competitions can award no points (e.g. qualifiers).
- The format is fixed once the first match is played. Points and rules can change any time.
- **Deleting:** before deleting, the app shows the impact (matches and points removed, and from whom). Deletion is permanent.

### Competitions list
- The Competitions tab groups an edition's competitions as **In progress** (started, or anything recorded), **Not started** and **Finished** ([Finishing](#finishing)), each group in the order Organizers set. Competitions you host or take part in are marked.
- Competitions have no day or time; when they happen is on the schedule page.

### Entrants
- Each competition sets its entrant type: **individuals**, **squads** or **teams**. Every entrant in a competition is that type; an individual never faces a squad or a team. Any format can use any entrant type, except that free-for-all editions have no **teams** entrant type.
- A squad can be any size. Hosts create squads inline by picking members.
- In team editions, a squad's members must all be on the same team.
- **Ranking, Bracket, Heats, Survival** have an entrant list, built from the roster. "Add everyone" adds anyone not already in; pressing it again after roster changes adds only the missing people. An entrant with no results can be removed; one with results can't (the app shows where they played).
- **Participation and Best score** have no entrant list. Anyone on the roster (or any squad, for squad competitions) can be marked done or log a score.
- No late-entry feature. Hosts can edit any match's entrants by hand, which covers late arrivals.

### Building matches
- The app builds the first round automatically when the host starts the competition. Order is random by default; the host can reorder before starting.
- **Bracket:** byes go to the top of the order when the count isn't a power of two. Optional "Play a 3rd place match" (off by default).
- **Heats:** the host picks a heat size and how many advance; the app splits entrants as evenly as possible (uneven heats allowed). The host can move entrants between heats before play and add a heat to the current round (e.g. for late arrivals) until starting the next round. Starting the next round closes the current one, advances the top N of each heat, and can use a new heat size (e.g. heats of 4, then a final heat).
- **Bracket and Survival:** later rounds fill in automatically as results come in.

### Recording results
- Each competition sets how a match is decided: **higher score wins**, **lower score wins**, or **finishing order**.
- With scores, the host enters only scores and the order follows. Manual ordering is only needed for tied scores or when there are no scores.
- Bracket matches can't tie; the host picks a winner.
- **Best score:** an entrant's score is their best attempt. What's ranked follows the entrant type: individuals and squads are ranked as entrants; with the **teams** entrant type, each team's total is the **sum of all members** or the **best member**, set per competition.
- **Participation:** individual completion, optionally with **tiers** that earn different points (e.g. Black Tuesday 12/15/18 hours). In team editions, team scoring is one of: **points per finisher**, **teams ranked by headcount**, or **teams ranked by percentage of team**. Tiers combine only with points per finisher. In free-for-all editions each finisher earns the points (by tier) directly.
- **Survival in team editions:** the competition scores either **individual places** (each person's place points go to their team) or **teams ranked by last survivor** (teams are ranked by when their last member is eliminated, and the points list applies to those team ranks).

### Self-report
- The host turns it on per competition; off by default. It isn't offered for competitions with the **teams** entrant type.
- In match formats, anyone in the match (including any squad member) can report its result or change it; the last change wins. Once a later match built on it has a result, only hosts and Organizers can change it.
- In Participation, participants mark themselves done; in Best score, they log their own attempts, and any squad member can log the squad's. While the competition is unfinished, participants can remove their own marks and attempts, but not ones a host made. Participants only report for themselves or their squad.
- Reports count immediately. No opponent confirmation, disputes or approval queue. The honor system applies; hosts correct mistakes.

### Subjective points
- Organizers only. Each entry has positive points and a reason shown to everyone. Entries can be edited and deleted.
- **Team editions:** given to a team, optionally naming the team members who earned it.
- **Free-for-all editions:** given to a person.

### Points and standings
- Points are set per place (e.g. 5/3/1). Places beyond the list earn 0. Any point value (per place, tier, per finisher, subjective) can be a half (e.g. 1.5).
- **Ties** share the place and each get its full points; the next place is skipped (1st, 1st, 3rd).
- **Knocked out together:** entrants knocked out in the same round of a Bracket, Heats or Survival tie for the next place below everyone who went further (e.g. without a 3rd place match, semifinal losers tie for 3rd and quarterfinal losers for 5th; 14 players out in round one of Catan tie for 5th). In Survival scored by last survivor, teams whose last members go out in the same round tie.
- **Participation team rankings:** a team with no completions gets no place and no points. Percentage is of the team's current roster.
- A place counts in standings as soon as it's decided; until its competition finishes, those points show as **in progress**.
- **Team editions:** points go to the team. An individual's points count for their team.
- **Free-for-all editions:** points go to individuals. Each member of a squad gets the squad's full points.
- **A person's points** (person page, team editions) are the points they can be concretely tied to: their own placings, their squad's points (full to each member), Survival team points for the team's last survivor(s), Participation completions including team rankings by headcount or percentage (credited to each person who completed), and subjective points naming them. Team-entrant results and subjective points naming no one show on members' pages but don't count toward their points.
- **Standings** show ranked totals (teams, or individuals in free-for-all) with your team or your own row highlighted, and every competition's status, point value and where its points went, with subjective points and their reasons. Seeing every point value in one place lets Organizers keep points balanced.

### Finishing
- Bracket, Heats and Survival finish when the final match is recorded; Ranking when the order is entered.
- Participation and Best score are open-ended: a host or Organizer taps **Finish**, or the edition ends ([editions.md](editions.md#lifecycle)).
- No close/reopen ceremony. Editing a finished competition updates points and standings recalculate.

### Ties that block advancement
In Heats, Survival or a Best score cutoff, the app flags the tie and the host picks who advances. No automatic tie-break rules.

### Corrections
- Hosts can change any result in their competitions, and Organizers in any competition (after the edition ends, see [editions.md](editions.md#lifecycle)). Every result shows who recorded it and who last changed it.
- If a correction changes who advanced, the app first names the later matches affected. On confirm, the right entrant replaces the wrong one in the next round, and any later result that included the wrong entrant is cleared to be recorded again.
- A result saved from an out-of-date view is refused ("Updated by Dom just now") and shows the current result; it never silently overwrites someone else's change. Submitting the same result twice changes nothing.

## Edge cases
- **Running tallies** (e.g. 2023's stairs, up to 5 a day, ranked by total): the host logs each person's running total as their Best score.
- **Consolation tables** (e.g. 2023's Catan "Second Table Champion"): run as a separate Ranking competition.

## Open questions
None.

## Examples
Past War Week competitions named in this spec.
- **Memes:** live meme showdown; teams ranked by vote.
- **Billable hours:** teams ranked by billable hours (or % of their usual hours).
- **Beer cans:** teams ranked by how many cans they added to the office beer can collection.
- **Team Night events:** a series of small head-to-head events on Team Night, each one group (or whole team) vs. another, each worth its own points.
- **Pool, Smash:** classic single-elimination 1v1 brackets.
- **Beyblade:** a qualifier ranked by best rips, then a finals bracket.
- **Bouncy Pong:** pairs; a qualifier ranked by best score, then finals between squads.
- **Catan:** tables of 4–5 players formed as people arrive, each table's winner advances to a final table.
- **Beer & Cards, Mario Kart:** groups of uneven size, top finishers advance to a final group.
- **Ultimate Survivor (2025):** nearly everyone in one pool; each round a different challenge, some eliminated each round, until one winner.
- **Tri-Wizard (2023):** each house entered its 12 best into an elimination-style challenge; houses ranked by when their last member was eliminated (10/5/3/1).
- **Steak wall (2025):** eat as many as you can; a best-score event.
- **Midnight Club / Black Midnight:** work from 12:00 AM to noon Sunday; points per finisher or teams ranked by headcount.
- **Beast Mode:** a morning workout; points for completing it.
- **Black Tuesday:** a focused, no-nonsense work day; in 2024 points by tier for 12, 15 or 18 hours.
- **AI survey (2026):** team with the highest completion percentage wins.
