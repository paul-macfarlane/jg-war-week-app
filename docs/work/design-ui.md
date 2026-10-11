# Design system and core-journey screens

Work package for `/design-ui`: the design system, then mocks of every surface for the participant, host and organizer journeys. Covers [requirements.md](../requirements.md) (all features) and [editions.md](../features/editions.md), [competitions.md](../features/competitions.md), [people.md](../features/people.md).

## Where it lives
- Design system (Claude Design): https://claude.ai/artifact/LqzxzyrRyqLSR2hswxjoW2
- Screens canvas (Claude Design): https://claude.ai/artifact/JNYqMR3uwFtcJrrRYv98eo — pages: Participant, Host, By format, Organizer, Wider screens.

Both are private to Paul until shared.

## Status
- Design system: built; updated through five feedback rounds.
- Screens: about 65 boards; Paul has reviewed every page. Final round in progress: mock the remaining surfaces (below), fresh-agent review, then Paul approves.
- On approval: add the design-system link to `requirements.md` (Design section) and screen links to the three feature docs; delete this file in the same PR.

## Decisions made while designing
Requirement changes Paul approved are already in the docs on this branch. Design decisions (recorded in the design system README, not the docs):
- Look: jahnelgroup.com (Anton, Libre Franklin, JetBrains Mono, near-black, JG blue `#00BDFF`), JG hexagon as the team marker. Dark default, light follows the phone, manual choice in the avatar menu.
- Wider screens: same single column centred at 720px; from 720px the tab bar moves into the header, brackets lay rounds side by side, sheets become centred dialogs.
- Controls: segmented for 2–3 options, Tabs for switching views, RadioList for 4–7 or explained options, switches, Checkbox for multi-select, PersonPicker for every person choice, numbered Pager (10 per page), steppers only for small counts, typeable numeric fields for scores, no dropdowns.
- Every button has a visible edge, except the header's Refresh, Back and Close icons.
- Status words: In progress / Not started / Finished; matches "To play"; host chips "To record" / "To set up"; "You're in" / "You played"; "Record result" everywhere.
- Every component maps to a shadcn part (table in the design system README).

## Remaining before approval
Canvas has 80 boards (all features have at least their main screens). Still to mock, each a variant of an existing pattern:
- People: blocked roster removal (lists where they appear); entrant with results can't be removed; team change blocked by a squad; add a team (next unused colour); Organizer email-change warning; import edge cases (missing column, flagged rows, people not in the paste).
- Edition: Setup → Ended (backfill); Ended → Live confirmation (enabled); co-winners; an Organizer's Home while an edition is only in Setup.
- Competitions: move entrants between heats / add a heat / late entrant in round 1; Bracket 3rd-place match; "Points not set yet" warning; tie at a Best score cutoff; Finish for Participation and Best score; participant removing their own mark or attempt; self-report locked after a later match has a result; teams as entrants; Survival scored by last survivor.
- Confirmations: delete subjective points; delete an award; last Organizer can't be removed.
- Wider screens: a sheet as a centred dialog; avatar menu as a dropdown; header nav on screens other than Home.
Then: fresh-agent review of the whole canvas; Paul approves; add links to the docs; open the PR.

Open items for Paul:
- Install to home screen: feature row but no rules in `editions.md`; InstallHint board is a proposal (one-time dismissible tip on Home).
- Partner sign-in: open question in requirements; not mocked.

Working files for the mocks live only in the Claude Design artifacts above (the source of truth); a new session reads them with the Artifact tool before editing.
