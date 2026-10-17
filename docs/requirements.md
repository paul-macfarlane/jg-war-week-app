# War Week requirements

Owned by Paul.

## Profile
- **Profile:** product, small group. Jason agreed on 17 October 2026 that War Week needs the app, so the goal is now that it delivers what War Week XII needs.
- **Expected scale:** ~100–125 people per edition (Jahnel Group employees plus partner-company participants from LTI and InfoLink, about 20 in War Week XI). Both partner companies are under Jahnel Group ownership: their people can do everything JG employees can, and anyone at them may sign in. Busy while an edition is Live and intense during the week itself, near zero otherwise: it must be rock solid from when points start counting to the end of the week; the rest of the year only the archive needs to work. War Week XII is Live for about three months (mid-November 2026 to the week in February 2027).
- **Exceptions to the standards** (Paul's engineering standards, from the [harness](https://github.com/paul-macfarlane/harness)): none.
- **Context that shapes priorities:**
  - **Next edition:** War Week XII (Beast Games) is in February 2027 and is a free-for-all, so free-for-all scoring must be fully supported, not treated as an edge case. People earn points from about mid-November (early events, and penalties from the tense death pool), and War Week events weigh much more. Per Jason, total points set tiers for a Friday elimination, each tier playing for its own prize (e.g. bottom third for $500, top third for $5,000); his format is still taking shape, so tiers are a sketch under [Needs buy-in](#needs-buy-in). Sign-in (partners included), the roster, subjective points and standings must work when points start counting, not just for the week.
  - **Meeting with Jason, 2 November 2026:** he sees the approved screens and the proposals canvas (the Needs buy-in items, each with a mockup where marked "Mocked"), and we bring the [questions for Jason](#questions-for-jason). Whatever doesn't depend on his answers can be built before then; the rest waits for his answers to be in the docs.
  - **Check-in:** once built, Jason sees the core journeys working on War Week XI data (Paul supplies the data in the work package that builds the archive).
  - **Timeline:** build what's settled now; the meeting on 2 November; the core live by mid-November when points start counting; War Week XII in February. Timeline doesn't drive tech choices; the goal is something Paul believes in, shown early enough to get feedback.

## Purpose
War Week runs on Slack channels, sign-up surveys, a wiki and a lot of chasing. The app makes it easier for each group involved:

- **Organizers administer War Week without coordinating with every host** to collect results and enter them by hand: results land in the app as they happen. Other Organizer pain points come in where the app is the right home for them.
- **Hosts run their competitions with less chasing.** People enter in the app instead of through a survey. The host records results or lets players record their own, instead of chasing people down, and nothing needs reporting back to Jason. Other host pain points come in where the app is the right home for them.
- **Participants see what's going on and join in** without digging through Slack and hoping the wiki has their results: the schedule, live standings and match history, and they record their own entries and results. Once Organizers' and hosts' problems are solved, participants' own requests come next.
- **Anyone can look back at past War Weeks:** who won and what happened, in one place instead of scattered or lost.

It must be **easy to use for everyone.** Participants find what they need in a tap or two on their phone, hosts record results in seconds, and running War Week is less work for Jason than the wiki was. If any of them finds it harder than what they did before, it fails.

## Character
- Feels like War Week: competitive, a little irreverent, Jahnel Group through and through.
- JG branding is the baseline look and ships with the app. Each edition's theme comes through in its theme name, in naming (what teams are called, e.g. Houses, Tribes) and in the pages Organizers write.
- Copy is plain and direct. No marketing voice.

## Design
- **Design system:** [War Week design system](https://claude.ai/artifact/LqzxzyrRyqLSR2hswxjoW2) (Claude Design). Screens per feature are linked from each feature doc. Proposals for the Needs buy-in items: [proposals canvas](https://claude.ai/artifact/4MsEVNtGypnZ179EFXkwkg).

## App-wide rules

### Roles
- **Organizer:** runs the whole edition (Jason, Paul). Manages the Organizer list.
- **Host:** runs one or more competitions (e.g. a pool tournament host), as set out in [competitions.md](features/competitions.md#hosts). Assigned by an Organizer.
- **User:** anyone who signs in. Users can read everything except Setup editions ([editions.md](features/editions.md#lifecycle)) and emails ([people.md](features/people.md#people)).
- **Participant:** a person on the edition's roster. Participants who are also users can record their own results where a host allows it.

### Navigation
- **Sections:** Home, Competitions, Info and Archive for everyone; Manage for Organizers (editions, teams and roster, competitions and hosts, subjective points, awards, export, Organizer list).
- **Edit in place:** things are edited where they live. A host records on the match; an Organizer edits a page from the page.
- **People and teams:** a person's page opens from standings and team member lists, and your own from your avatar menu. Tapping a team opens its team view. Names mentioned in passing (a host, an award recipient, a subjective-points entry, an entrant list) are plain text, and a row with another job (a match, a picker result) does that job. Each tap does one predictable thing: standings and team lists are where people go looking for a person, and making every name a link would put a second target inside rows that already do something.
- **Highlighted tab:** a team view or person page keeps the tab it was opened from highlighted (from Home's standings, Home; from a competition, Competitions; your own page, whichever tab you were on), and back returns there.
- **Wider screens:** the tab bar moves into the header, and breadcrumbs (e.g. Manage › Competitions › Smash) replace the back arrow. Everything else is the same screen as on a phone.
- **Avatar menu:** your own page, theme (System, Dark or Light; System follows the phone), Install app (on phones, until installed) and Sign out.

### Structured data vs. pages
Structured data only where the app computes something or it's history people care about: editions, teams and roster, competitions, matches, results, points, standings, awards. Everything else is an Organizer-written page (rich text and links, no images), listed under Info in the order Organizers set (e.g. schedule above FAQ).

### Saving
Settings and configuration save as you make them; there's no Save button to miss. Recording anything (results, marks, attempts, subjective points, awards), creating something new, anything destructive (delete, end, remove) and anything that moves someone's access (e.g. changing an Organizer's or host's email) are explicit actions.

### Times
Times the app shows are in the viewer's own time zone. Times in pages are shown as the Organizer wrote them.

## Features

| Feature | Use case (who, when, and what it gets them) | Detail | Status |
|---|---|---|---|
| Sign in | Any employee opening the app with their Jahnel Group Google account, so it shows their team, their matches and what needs them | [features/people.md#sign-in](features/people.md#sign-in) | todo |
| Partner sign-in | An LTI or InfoLink participant opening the app from November, when War Week XII points start counting, so they can see their team, enter competitions and record their own results like everyone else | [features/people.md#sign-in](features/people.md#sign-in) | todo |
| Home | Anyone opening the app to see what needs them and where they stand, without digging through Slack | [features/editions.md#home](features/editions.md#home) | todo |
| Standings | A participant on Tuesday night checking who's ahead, without waiting for Jason to tally it | [features/competitions.md#points-and-standings](features/competitions.md#points-and-standings) | todo |
| Competitions & results | A host recording a bracket match as it finishes, so standings update without reporting back to Jason | [features/competitions.md#competitions--results](features/competitions.md#competitions--results) | todo |
| Match history | A pool player checking how the other side of the bracket is going; someone who missed Tournament Night looking up how the Smash bracket played out, without asking the host | [features/competitions.md#match-history](features/competitions.md#match-history) | todo |
| Self-entry | A player entering the pool bracket from their phone, so the host doesn't have to chase who's in | [features/competitions.md#self-entry](features/competitions.md#self-entry) | todo |
| Self-recording | A player in a large tournament recording their own match so the host doesn't have to chase every result | [features/competitions.md#self-recording](features/competitions.md#self-recording) | todo |
| Subjective points | Jason awarding spirit or bonus points, with a reason, outside any competition, so they count in the standings and everyone sees why; Zach taking points off for each tense error he catches in the tense death pool, from November on | [features/competitions.md#subjective-points](features/competitions.md#subjective-points) | todo |
| Standings over time | A participant in January seeing how they've climbed since November, and everyone looking back at how the lead changed during the week | [features/competitions.md#standings-over-time](features/competitions.md#standings-over-time) | todo |
| Slack posts | Everyone in the War Week channel seeing a competition's podium as it finishes and where the standings are, without opening the app | [features/competitions.md#slack-posts](features/competitions.md#slack-posts) | todo |
| Export | Jason downloading the standings, results and awards for the closing ceremony slides he builds himself | [features/editions.md#export](features/editions.md#export) | todo |
| Awards | Jason entering MVPs, Top Biller and Black Midnight finishers after closing ceremonies, so they stay with the edition's history | [features/editions.md#awards](features/editions.md#awards) | todo |
| Teams & roster | Jason importing the War Week sign-up sheet in one go, instead of entering over 100 people by hand, and importing again for people who join after points have started counting | [features/people.md#teams-and-roster](features/people.md#teams-and-roster) | todo |
| Team view | A participant on day one seeing who's on their team and who leads it, so they know who they're competing alongside | [features/people.md#team-view](features/people.md#team-view) | todo |
| Hosts | Jason creating a competition and assigning its host before the week, so the host runs it and records results without going through Jason | [features/competitions.md#hosts](features/competitions.md#hosts) | todo |
| Pages | Jason writing the schedule, meals, FAQ, scoring overview and essentials for the week, as flexibly as the wiki, so everything about the week is in the same place as the standings | [features/editions.md#pages](features/editions.md#pages) | todo |
| Edition lifecycle | Jason creating War Week XII, running it, and ending it with a winner, so he controls when it goes public and when results are final | [features/editions.md#lifecycle](features/editions.md#lifecycle) | todo |
| Archive | Anyone looking back at who won War Week IX and how, instead of hunting through old wikis | [features/editions.md#archive](features/editions.md#archive) | todo |
| Person page | A participant checking their results and the points they've contributed this week, to see their part in the standings; anyone looking at everything one person has won across years, so wins aren't lost from one year to the next | [features/people.md#person-page](features/people.md#person-page) | todo |
| Organizer list | Jason adding Paul as an Organizer, so running War Week doesn't rest on one person | [features/people.md#organizers](features/people.md#organizers) | todo |
| Install to home screen | A participant adding the app to their phone's home screen for the week, so it's one tap away like any other app | [features/people.md#install-to-home-screen](features/people.md#install-to-home-screen) | todo |

Several rows can share one feature doc.

## Non-functional
- Access is internal only: every page requires sign-in. Nothing may assume every user has a Jahnel Group email.
- A request to remove a person's data is handled manually by the database owner (e.g. name replaced, email cleared, results kept so team history still adds up).

## Out of scope
- Anyone outside Jahnel Group and its War Week partner companies, and any event other than War Week.
- Marketing or "about" pages.
- Offline support.
- Sign-ups other than entering a competition (e.g. meals, workouts). They stay as external links in pages unless the in-app sign-up proposal under Needs buy-in is approved.
- Copying an edition forward. Each year is different; text worth keeping is copied from the archived page.
- People search. Organizers and hosts find people through pickers; person pages are reached as Navigation describes.
- Accomplishments / immunity (lighter than awards, as in War Week X).
- A "War Week Wrapped" recap. The person page already shows a person's week.
- Closing ceremony slides. Jason builds his own deck; [Export](features/editions.md#export) gives him the data (Dom's feedback, October 2026).

## Needs buy-in
Proposals that need Jason's yes before building.
- In-app sign-up for War Week, replacing the sign-up sheet: one tap, since you're signed in, plus a few questions Organizers set (e.g. wanting to lead a team). It comes with RSVPs for anything that needs a headcount (meals, workouts, Black Midnight, drinks after work), with totals for Organizers. Sign-up comes before teams exist, so the edition needs a sign-up stage people can see before it's Live. Drafted teams get in through in-app team drafting, or by Organizers setting each person's team. Mocked.
- Tiers, a sketch while Jason settles the format: an optional setting for free-for-all editions where the standings set tiers for a final competition, as a qualifier sets who goes through. Organizers set the number of tiers and how they split (how is a [question for Jason](#questions-for-jason)), and each tier can carry a prize label (e.g. "$5,000"). Everyone on the roster is in a tier, 0 points and late joiners included. A tie at a cut line puts everyone tied in the higher tier. Standings show the cut lines and each person sees their tier and how far they are from the next. Each tier's final is a Survival competition whose entrants a host fills with "Add tier 1" (and so on) instead of "Add everyone": the tier's people are copied in once, and the host edits the list as usual (e.g. someone who can't make Friday). Nothing locks, and points earned after that don't move anyone. The winners of an edition with tiers are its tier finals' winners, not first in standings. Mocked.
- Automatic tense death pool penalties, a reach goal: the app reads the tense API on a schedule and adds a penalty for each tense error, instead of Zach entering them. Needs the API's details and Zach's agreement.
- Per-edition theme: Organizers pick a color from a short list of presets, each checked for contrast in dark and light, an optional matching background tint, and a headline font. JG logo, body text and layout don't change. Trades some JG branding consistency for each year's flair. Mocked.
- Hosts creating their own competitions and setting their points. Trades Organizers' single view of point balance for less setup work for Jason.
- All-time records across editions in the Archive (most 1st place finishes, most awards). Mocked.
- Scheduled reveals: Jason enters subjective points or an award when it comes to mind and sets when it shows. Until then only Organizers see it, and hidden subjective points don't count in standings. Competitions and pages are never hidden. A small convenience. Mocked.
- Team drafting in the app, after War Week XII: team leaders pick in turns from the sign-up list in a live session, on a shared screen and their phones, and the picks become the roster. Teams are drafted outside the app today and arrive through the sign-up sheet. Mocked.

## Suggestions
Ideas from others at JG, captured with who suggested them.
- **Drag to place** (Dom, pool and chess host, October 2026): placing people by dragging instead of typing numbers. Taken up: hosts drag wherever they set an order ([competitions.md](features/competitions.md#recording-results)). Mocked on the proposals canvas for feedback.
- **No closing ceremonies in the app** (Dom): Jason makes his own slides, so an export is enough. Taken up: the closing ceremonies proposal is dropped for [Export](features/editions.md#export).

## Before War Week XII
Needed before the week itself in February, not for when points start counting in November.
- League formats (Swiss, round robin) for chess and MTG. Still to be fleshed out.
- Chaining a qualifier into bracket seeding.
- A participation result auto-creating an award (e.g. Black Midnight).
- Backfilling editions before War Week XI.
- Image uploads (team logos, edition banners, people uploading their own photo). Optional for War Week XII.
- Display names people set for themselves.

## Open questions
- **Partner sign-in:** which accounts (Google, Microsoft or other) and email domains do LTI and InfoLink participants sign in with? Paul finds out from each company; it isn't a question for Jason. Needed by mid-November, when partners start earning points.

### Questions for Jason
For the meeting on 2 November 2026. Answers go into the docs; anything that depends on one waits for it.

**The format**
- When exactly do points start counting, and what earns them before the week (events, tense death pool, anything else)? Roughly how many points does a War Week event carry next to an early one?
- What is the Friday elimination: one Survival-style knockout per tier, or something else? Where does the AI component come in, and does the app need to know about it?
- Is the LatAm elimination part of War Week XII's standings, or its own thing with its own prize?
- Who is the edition's winner: the winner of each tier's final, the top tier's winner, or first in standings?

**Tiers**
- How many tiers, and are they split by headcount (e.g. thirds of people) or by points? Do the splits change if the roster changes?
- When are tiers set: Thursday night, or at some other moment? Do points from War Week events up to Friday count?
- Does everyone on the roster get a tier, including people with 0 points or below?
- Should people see the tier lines and prizes all along, or only near the week?

**Penalties**
- Is a tense error a fixed number of points, or does Zach decide each time?
- Can penalties take someone below 0?
- Are the people "in white" (no tense errors since February) given points once, and how many?
- Is Zach happy to enter penalties as an Organizer? Is automatic entry from the tense API worth pursuing?

**The app**
- Each proposal under Needs buy-in, on the proposals canvas.
- Slack posts: which channel, and a standings summary weekly until the week and then each evening?
- Export: which columns does he want for his slides (standings, every competition's places and points, subjective points, awards, tiers)?
