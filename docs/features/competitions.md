# Competitions

**Features:** Competitions & results, Hosts, Self-entry, Self-report, Match history, Standings, Subjective points

Priorities, in order: easy for participants, hosts and organizers, then flexible. Simple choices in front, one flexible model behind.

See [Examples](#examples) for what each named competition was.

## Core journey
1. **Participant:** enters a competition where allowed; checks standings, results and match history on their phone; self-reports a match where allowed.
2. **Host:** sets up and starts a competition; records a result; points land in standings.

## Screens
Approved in the [screens canvas](https://claude.ai/artifact/JNYqMR3uwFtcJrrRYv98eo): By format page (set up, competition page and record, per format, plus variants and self-entry); Host page (host Home, corrections, stale saves, ties, Finish); Organizer page, Competitions and Points and awards rows; Participant page (Competitions list, self-report).

## Rules

### Formats
A host picks one of five formats. The first four are all rounds of matches, where each match ranks its entrants.

| Format | What it is | Examples |
|---|---|---|
| **Ranking** | One list, all entrants ranked by score or order; optionally the best of several attempts counts and the top N are marked as going through | Memes, billable hours, beer cans, a Team Night event, the steak wall, Beyblade and Bouncy Pong qualifiers |
| **Bracket** | Single elimination, 2 per match, winner advances | Pool, Smash, Beyblade finals |
| **Heats** | Heats of several entrants, top N advance, until a winner | Catan, Beer & Cards, Mario Kart, group stage then knockout |
| **Survival** | Everyone in one pool, some eliminated each round; each round can have a description | Ultimate Survivor, Tri-Wizard |
| **Participation** | Who completed it | Midnight Club, Beast Mode, Black Tuesday, AI survey |

Subjective points and awards are not competitions. Events that aren't competitions live on the schedule page.

### Setup
- **Organizers** create competitions, set their order, assign hosts and delete competitions. They set every point value and scoring choice: points per place, Participation tiers and their points, points per finisher, and how teams are scored. A competition can have several hosts, chosen from anyone in the app, as Organizers are; a host needn't be on the roster.
- **Hosts** set the format, description, entrants, how a match is decided, the attempts switch, the Ranking cutoff, the self-entry switch and the self-report switch, and record every result in their competitions, including ones they took part in. Organizers can do anything a host can, so they can set a competition up as far as they like before handing it over.
- Each competition has one setup screen, reached from its page. Organizers edit all of it; its hosts edit everything except the name, hosts, point values and scoring choices, which they see read-only.
- A competition whose format needs points or a scoring choice that isn't set yet says so to its hosts and Organizers.
- A **description** is optional (what it is, its rules), in the same restricted rich text as pages ([requirements](../requirements.md#structured-data-vs-pages)).
- An Organizer can turn off **Awards points** (e.g. qualifiers); the competition then shows "No points" and is never flagged as not set.
- Once the first result is recorded, the format, entrant type, how a match is decided, the attempts switch, how a Ranking scores teams and the 3rd place match are fixed. Points, description, the Ranking cutoff, self-entry, self-report and hosts can change any time.
- **Deleting:** before deleting, the app shows the impact (matches and points removed, and from whom). Deletion is permanent.

### Competitions list
- The Competitions tab groups an edition's competitions as **In progress** (started, or anything recorded), **Not started** and **Finished** ([Finishing](#finishing)), each group in the order Organizers set. Each competition shows its point values and where its points went; subjective points and their reasons follow the competitions. This is the edition's only points breakdown: seeing every point value in one place lets Organizers keep points balanced. Competitions you host or take part in are marked.
- Competitions have no day or time; when they happen is on the schedule page.

### Entrants
- Each competition sets its entrant type: **individuals**, **squads** or **teams**. Every entrant in a competition is that type; an individual never faces a squad or a team. Any format can use any entrant type, except that Participation and free-for-all editions have no **teams** entrant type.
- A squad can be any size. Hosts create squads inline by picking members.
- In a Ranking with attempts on, a person can be on more than one squad. Squads are ranked in score order, and a squad is skipped (no place, no points, not counted toward a cutoff) if anyone in it is already on a ranked squad. Squads tied on score that share someone are a tie the host resolves, as at a cutoff ([Ties that block advancement](#ties-that-block-advancement)). Pairs can try with different partners. Someone on more than one squad picks which squad they're logging for. Everywhere else, nobody is on two squads, or on a squad and entered alone, in the same competition.
- In team editions, a squad's members must all be on the same team.
- In a squad Ranking, a host (or, with self-report, a participant) forms a squad by picking its members when logging its first score.
- **Bracket, Heats, Survival** have an entrant list, built from the roster. "Add everyone" adds anyone not already in; pressing it again after roster changes adds only the missing people. An entrant with no results can be removed; one with results can't (the app shows where they played).
- **Self-entry:** Bracket, Heats and Survival competitions with individual or squad entrants have a "Let people enter themselves" switch, off by default. When it's on, participants who have signed in can enter from the competition page while the edition is Live and the competition hasn't started. Team-entrant competitions never have it.
- In a squad competition, you enter by picking your squadmates, under the same rules as hosts (same team in team editions). Squadmates don't have to accept. Picking someone who's already entered is blocked, and the app says where they're in. Anyone in the squad can withdraw it.
- You can leave until the competition starts. Once it starts, entries close and only hosts add late entrants (below).
- **Ranking and Participation** have no entrant list. Anyone on the roster (or any squad of roster members, for squad competitions) can be given a score, place or mark; they're in it once they have one, and out again if it's removed.
- In Bracket, Heats and Survival, late entrants can be added only during the first round, and only where no played match has to be redone (e.g. a new heat, or a first-round match not yet played). Hosts can edit an unplayed match's entrants by hand.

### Building matches
- **Bracket, Heats, Survival:** the app builds the first round automatically when the host starts the competition. Order is random by default; the host can reorder before starting.
- **Bracket:** byes go to the top of the order when the count isn't a power of two. Optional "Play a 3rd place match" (off by default).
- **Heats:** the host picks a heat size and how many advance; the app splits entrants as evenly as possible (uneven heats allowed). The host can move entrants between heats before play and add a heat to the current round (e.g. for late arrivals) until starting the next round. Starting the next round closes the current one, advances the top N of each heat, and can use a new heat size (e.g. heats of 4, then a final heat).
- **Bracket and Survival:** later rounds fill in automatically as results come in.
- **Ranking and Participation** have no start: they're in progress from the first result or mark.

### Recording results
- Each competition except Survival sets how a match is decided: **higher score wins**, **lower score wins**, or **finishing order**. A Survival round records who goes through.
- With scores, the host enters only scores and the order follows. Manual ordering is only needed for tied scores or when there are no scores.
- Bracket matches can't tie; the host picks a winner.
- A competition decided by score can set a **score unit** (e.g. steaks, hours), shown after its scores. Blank shows bare numbers.
- **Ranking by score:** each entrant has one score, which the host (or, with self-report, the entrant) updates; the last change wins. With **"Count best of several attempts"** on (off by default), each entry is an attempt and the best one counts.
- **Ranking with the teams entrant type**, decided by score: a team's score is **entered for the team**, the **sum of members** or the **best member**, set per competition. With sum or best member, scores are recorded per member (each member's best attempt, with attempts on). Sum of members isn't offered when lower score wins. Decided by order, it's entered for the team.
- **Ranking cutoff:** optional; the host sets a top N. It only marks who goes through (e.g. into a finals bracket) and doesn't change places or points.
- **Participation:** individual completion, optionally with **tiers** that earn different points (e.g. Black Tuesday 12/15/18 hours). In team editions, team scoring is one of: **points per finisher**, **teams ranked by headcount**, or **teams ranked by percentage of team**. Tiers combine only with points per finisher. In free-for-all editions each finisher earns the points (by tier) directly.
- **Survival in team editions:** the competition scores either **individual places** (each person's place points go to their team) or **teams ranked by last survivor** (teams are ranked by when their last member is eliminated, and the points list applies to those team ranks).

### Self-report
- The host turns it on per competition; off by default. It isn't offered for **Survival**, a Ranking decided by order, or competitions with the **teams** entrant type, except a Ranking scored by sum of members or best member.
- In Bracket and Heats, anyone in the match (including any squad member) can report its result or change it; the last change wins. Once the next round includes anyone from it, or a later match built on it has a result, only hosts and Organizers can change it.
- In Participation, participants mark themselves done; in a Ranking by score, they log their own score or attempts, and any squad member can log the squad's. Participants can update their own score whoever entered it, and remove their own marks, scores and attempts, but not ones a host made. Participants only report for themselves or their squad.
- Once a competition is finished, only hosts and Organizers change its results, marks and attempts.
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
- **A person's points** (person page, team editions) are the points they can be concretely tied to: their own placings, their squad's points (full to each member), Survival team points for the team's last survivor(s), Participation completions including team rankings by headcount or percentage (credited to each person who completed), member-scored team Rankings (credited to each member with a score for sum of members, or to the best member), and subjective points naming them. Other team-entrant results and subjective points naming no one show on members' pages but don't count toward their points.
- **Standings** show ranked totals (teams, or individuals in free-for-all) with your team or your own row highlighted. Where the points came from is on the Competitions tab ([Competitions list](#competitions-list)).

### Finishing
- Bracket and Heats finish when the final match is recorded; Survival when one entrant is left (or, scored by last survivor, one team).
- Ranking and Participation are open-ended: a host or Organizer taps **Finish**, or the edition ends ([editions.md](editions.md#lifecycle)).
- No close/reopen ceremony. Editing a finished competition updates points and standings recalculate.

### Ties that block advancement
In Heats or at a Ranking cutoff, the app flags the tie and the host picks who advances when people advance: on starting the next round (Heats) or on Finish (Ranking). No automatic tie-break rules. At a Ranking cutoff, the tie is flagged again whenever the cutoff or a score changes, even after Finish. The pick only marks who goes through; tied entrants keep their shared place and points, including when the edition ends before a pick.

### Corrections
- Hosts can change any result in their competitions while the edition is Live; Organizers can change any result in any competition, including after the edition ends ([editions.md](editions.md#lifecycle)). Every result, mark and attempt stores who recorded it and when, and who last changed it and when; a result's time is when it was recorded. Hosts and Organizers see both when they open the match.
- If a correction changes who advanced, the app first names the later matches affected. On confirm, the right entrant replaces the wrong one in the next round, and any later result that included the wrong entrant is cleared to be recorded again.
- A result saved from an out-of-date view is refused ("Updated by Dom just now") and shows the current result; it never silently overwrites someone else's change. Submitting the same result twice changes nothing. In a Ranking, this is checked per entrant's score, and adding an attempt is never refused.

## Edge cases
- **Switching format before play:** switching to Ranking or Participation, which have no entrant list, clears the entrants, after a confirmation.
- **Running tallies** (e.g. 2023's stairs, up to 5 a day, ranked by total): the host (or, with self-report, each person) updates their running total as their Ranking score.
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
- **Steak wall (2025):** eat as many as you can; ranked by count.
- **Midnight Club / Black Midnight:** work from 12:00 AM to noon Sunday; points per finisher or teams ranked by headcount.
- **Beast Mode:** a morning workout; points for completing it.
- **Black Tuesday:** a focused, no-nonsense work day; in 2024 points by tier for 12, 15 or 18 hours.
- **AI survey (2026):** team with the highest completion percentage wins.
