# [USER]'s Personal Knowledge System

Template repository for setting up a new personal-knowledge-system (PKS) repo for a Kosek Advisory
Group LLC member, family contributor, or pilot user. Copy this directory's contents into a new repo
to bootstrap. New non-coding users are usually onboarded by someone who runs the setup steps for
them.

## Setup steps for new user

1. Create a new **private** GitHub repository under your personal account named
   `[firstname]-personal-knowledge-system` (for example `jordan-personal-knowledge-system`).
2. Clone the new empty repo locally.
3. Copy the contents of `templates/personal-repo/` from the `skills` repo into your new clone.
4. Rename `dot-claude/` to `.claude/` so the session hooks are active.
5. Add the `skills` repo as a submodule:
   ```
   git submodule add https://github.com/Kosek-Advisory-Group-LLC/skills.git skills
   ```
   For a guided **pilot user**, point this at the curated `kag-pilot-skills` distribution repo
   instead of the full engine (see `docs/REGISTRATIONS-CHECKLIST.md`).
6. Set your identity so your records are yours, not someone else's:
   ```
   git config user.email "[your-email]"
   ```
   and set a `KAG_OPERATOR_ID` environment variable to the same email.
7. Rename `kag-user-profile.template.json` to `kag-user-profile.json` and fill it in (see
   `docs/GETTING-STARTED.md`). For a guided pilot user, keep `user_role: pilot`.
8. Fill in `career/bullet_library.json` and `career/contact_block.json` with your resume material,
   or have your onboarder help during intake.
9. Edit `CLAUDE.md` to fill in your domains, personal conventions, and identity, and edit this
   `README.md` to remove the template framing. Keep the archetype-fixed blocks in `CLAUDE.md`
   verbatim (Where things live, Operating stance, and the inherited Conventions baseline); they
   encode the `data-store` archetype's fixed choices and are not yours to fill in.
10. Make the initial commit ("Initialize personal knowledge system from template") and push.

See `docs/REGISTRATIONS-CHECKLIST.md` for the accounts and installs to create first.

## Directory structure

```
your-personal-knowledge-system/
├── README.md                           Personal description
├── CLAUDE.md                           Session loading + your domains
├── STATUS.md                           Daily rollup read by the hello brief
├── BACKLOG.md                          Lower-priority items for the hello brief
├── CHANGELOG.md                        Running log
├── .gitignore                          Excludes .claude/ session state
├── kag-user-profile.json               Identity + pilot-mode marker (from the .template)
├── dot-claude/  ->  .claude/           Session hooks; rename on setup
├── docs/                               REGISTRATIONS-CHECKLIST.md + GETTING-STARTED.md
├── skills/                             Submodule -> org skills repo
├── knowledge-base/                     Your personal data stores
│   ├── *.jsonl                         Per-skill stores (job-analysis, chain-checkpoints, ...)
│   ├── drafts/                         Skill #03 prose outputs
│   ├── syntheses/                      Skill #01 synthesis outputs
│   └── recommendations/                Free-form recommendation outputs
├── career/                             Resume-tailoring data (bullets, contact); see career/README.md
├── inbox/                              Mobile/async capture drop zone
└── patches/                            Patch manifests
```

## Privacy

Your personal-knowledge-system repository is yours: your stores, your CLAUDE.md, your domains. Do
not commit content from another user's personal repo into yours, and do not commit firm or client
engagement work into your personal repo. Keep the repo private.

## How skills work

The `skills/` directory is a submodule pointing at the Kosek Advisory Group LLC `skills`
repository, which is private to the org and shared with members (pilot users mount the curated
`kag-pilot-skills` distribution instead). You consume skills; you do not author or modify them here.
To pull in newer skill versions:

```
git submodule update --remote skills
git add skills
git commit -m "Bump skills submodule to [hash]"
```

To iterate on a skill yourself (becoming a contributor to the shared ecosystem), work in the
`skills` repository directly, then bump your submodule reference here.
