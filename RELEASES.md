# Releases: Stable and Dev

UntoCaesar, Gantrel and Corunis depend on Fonsviva, so it must be stable. It ships on two update channels only. There is no nightly channel.

## Channels

| Channel | Branch | Who it's for | How often |
|---|---|---|---|
| **Stable** | `stable` | Everyone. This is the default and the only channel most people see. | When a tested release is promoted |
| **Dev** | `main` | Developers and testers only. Hidden behind a developer setting and never used for real work. | When `main` has new commits and CI is green |

## How a change reaches users

1. Work happens on feature branches and merges into `main` by pull request, with CI green.
2. `main` is published to the Dev channel, tagged `dev-YYYY-MM-DD`.
3. A Dev build is promoted to Stable only after every test in TESTING.md passes, including the API compatibility tests for every supported harness and each dependent app's test suite run against it, with no regressions. It is then merged into `stable` and tagged `vMAJOR.MINOR.PATCH`.
4. Urgent fixes go to `stable` through a pull request, then get merged back into `main`.

## Update rules for the app

- Updates are signed and verified before they install.
- Settings, keys, the job queue and the model inventory are backed up before every update, and migrations are reversible.
- Every update can be rolled back to the previous version.
- Updates wait for running jobs to finish or pause them safely; they never drop queued work.
- Downloaded models are never deleted by an update.
- The API stays backward compatible. A breaking change needs a new version path and a migration window announced in the release notes.
- The app shows what changed, in plain words, before and after updating.
