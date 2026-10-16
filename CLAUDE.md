# War Week

The app for Jahnel Group's yearly War Week: the schedule, live standings and results during the week, and the history after it.

## Docs
- `docs/requirements.md`: profile, purpose, roles and other app-wide rules, features and their status, non-functional requirements, Needs buy-in, Before War Week XII.
- `docs/features/`: `competitions.md` (formats, setup, entrants, matches and results, self-recording, subjective points, standings, corrections), `editions.md` (lifecycle, winner, awards, home, pages, archive), `people.md` (sign-in incl. partners, roster and sign-up import, team view, person page, Organizers, install).
- `docs/architecture.md`: stack, code structure, key decisions and why.
- The [screens canvas](https://claude.ai/artifact/JNYqMR3uwFtcJrrRYv98eo) holds every approved screen; each feature doc says which parts are its own.

## Screen conventions
- The screens canvas has one page per role (Participant, Host, Organizer). Each screen goes under the least-privileged role that sees it, and wide-screen boards sit beside their phone versions.
- Nothing should wrap or overflow awkwardly at 390px with long names: metadata that could wrap goes on separate lines, and a header sub-line holds at most two short parts.
