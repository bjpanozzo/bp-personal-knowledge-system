# Registrations checklist (personal-knowledge-system)

Every account and install a new user needs before they can run the skills, in dependency order,
with purpose, rough cost, the one action to take after signing up, and who performs it under a
KAG-assisted onboarding. A non-coder user typically only does the two Claude steps themselves;
the person onboarding them (the KAG operator) handles the Git and GitHub wiring.

| Step | Service / install | Purpose | Rough cost | Post-signup action | Who does it |
|---|---|---|---|---|---|
| 1 | Anthropic account + **Claude Pro** | The Claude subscription that includes Claude Code | ~$20/mo | Subscribe to Pro at claude.ai | User |
| 2 | **Claude Code** (desktop app) | The workspace where you run the skills against your repo | included with Pro | Install the desktop app for your OS, sign in with your Claude account | User |
| 3 | **Git** (Git for Windows or Mac) | Version control + pulling the shared skills submodule + signing in to GitHub | Free | Install. On Windows this includes Git Credential Manager, so you log in to GitHub through a browser window with no manual token | Operator |
| 4 | **GitHub account** | Hosts your private PKS repo for backup and cross-machine sync | Free | Create the account; keep your `<you>-personal-knowledge-system` repo **private** | Operator (creates repo), User (owns account) |
| 5 | **`KAG_OPERATOR_ID`** environment variable | Tells the system who you are so your records carry your identity, not someone else's | n/a | Set it once to your email at the user/system level (e.g. `you@example.com`) | Operator |

## Notes

- Pilot users mount the curated `kag-pilot-skills` distribution repo as their `skills` submodule,
  not the full engine repo. That distribution repo is **private** and you are granted read access,
  so cloning it uses the same browser login (Git Credential Manager) as pushing to your own private
  PKS repo. Pilot users are never given the full private `skills` engine repo.
- You never need a code editor, a terminal you operate yourself, or any developer tooling beyond
  the above. Day to day you work by talking to Claude Code in plain English.
- Optional niceties the operator may also set on your machine: latest auto-update channel and
  desktop notifications in Claude Code settings, and a small set of relevant plugins. None are
  required to run the job search workflow.
