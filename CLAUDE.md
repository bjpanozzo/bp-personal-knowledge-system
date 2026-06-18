# CLAUDE.md
## Session loading instructions for [USER]'s Personal Knowledge System

**Repository:** [https://github.com/USER/USER-personal-knowledge-system]
**Owner:** [USER NAME]
**Created:** [DATE]
**Status:** Active

> **Template note:** Replace bracketed placeholders below with your specific information. After filling in, delete this template note and the [TEMPLATE: ...] markers throughout.
>
> This `CLAUDE.md` is a filled-in instance of the `data-store` archetype in the [CLAUDE.md authoring standard](skills/knowledge-base-reference/claude-md-authoring-standard.md). Three blocks are pre-resolved for the personal-knowledge-system (PKS) archetype and should be kept verbatim: **Where things live**, **Operating stance (KAG shared preamble)**, and the inherited **Conventions** baseline. They already encode the archetype-fixed choices (immutable records with supersession, privacy class `private`, skills-submodule paths), so do not turn them back into choices. Fill in only the `[TEMPLATE: Fill in]` personal sections (your domains, your personal conventions, your identity) and replace `[USER]` / `[DATE]`.

---

## Where things live

A one-read map for any operator (human or agent) opening this repo. This repo is content-specific to one operator; the shared engine is mounted as a submodule, not copied.

- **Source of truth (durable deliverable):** the records in `knowledge-base/` (your immutable JSONL stores, plus the `drafts/` and `syntheses/` outputs) and your resume inputs in `career/`. These ARE the deliverable. They are canonical and never "synced to cloud as truth"; the git repo is the source of truth. A store is never disposable scratch.
- **Instructions / SOPs:** this CLAUDE.md, plus each skill's `SKILL.md` in the `skills/` submodule.
- **Deterministic scripts:** the engine's `tools/` inside the `skills/` submodule (stdlib-only, governed). This repo holds your data, not engine code.
- **Disposable scratch:** `.tmp/` (gitignored, regenerable, never a source of truth). Distinct from the stores: scratch is throwaway, the stores are canonical. `inbox/` holds unprocessed captures (pending input, cleared as you process them; not scratch, and not yet a store).
- **Secrets:** `.env` only (none committed; never commit a secret). `kag-user-profile.json` carries identity, not secrets.
- **Shared skills:** the `skills/` submodule, pointing at `Kosek-Advisory-Group-LLC/skills`. Bump the reference deliberately to pull newer skills.

---

## Operating stance (KAG shared preamble)

You are one operator in this repo, working alongside other operators (AI agents and people). Your job is to coordinate, not to do everything by hand.

- **Orchestrate, do not brute-force.** Read the relevant instructions first (this CLAUDE.md, the relevant `SKILL.md` in the `skills/` submodule, and any contract it points to). Prefer existing tools, scripts, and contracts over building something new. Hand deterministic work (validation, transforms, scoring, file operations) to scripts or engines so a long chain of judgment calls does not compound small errors.
- **Keep knowledge current the right way.** Never edit a store record in place; supersede it (write a new record, point the old one at it via a supersession pointer). Historical-accuracy-default queries depend on this immutability.
- **Hygiene.** Secrets live only in `.env` or the platform secret store; never inline a key, never commit one. `credentials.json` / `token.json` stay gitignored. `.tmp/` is disposable scratch, regenerable, never a source of truth. Your stores are never scratch.
- **Know where you are.** This repo is one node in the Kosek Advisory Group (KAG) lattice: a content-specific personal-knowledge-system that mounts the shared engine as a submodule. For sibling repos and this repo's privacy class, see `skills/knowledge-base-reference/kag-repo-registry.md`. This repo's privacy class is `private`; honor it on everything that leaves the repo (do not commit another operator's personal data into yours, and do not surface your stores into shared or client-facing output).
- **Write for the next reader.** A human teammate and a fresh agent should both orient from this file in one read. Define terms on first use. Semi-formal and data-driven; no em-dashes; no canned affirmations ("Perfect", "Great").

---

## What this repo is

Your personal knowledge production system. Holds your stores, your domain inventory, your captured observations, your synthesized outputs, and your conventions. Skills come from the `skills/` submodule, which is the shared Kosek Advisory Group LLC ecosystem; this repo is content-specific to you.

## What this repo is NOT

- Not a shared skill ecosystem (that's `Kosek-Advisory-Group-LLC/skills`)
- Not a client engagement record (that's `kosek-consulting`)
- Not a household personal record (that's a separate private repo if you maintain one)

## Architectural commitments inherited from skills repo

Your data conforms to the skill ecosystem's locked architecture:

1. Content-agnostic at the engine layer
2. Single source of truth per concept
3. Immutable records with supersession pointers
4. Historical-accuracy-default query behavior

You don't override these. If you need different behavior, the conversation goes to the skills repo, not here.

## [TEMPLATE: Fill in] Your domain inventory

Skills route observations into one of seven domains by default. Define your seven (or however many) domains. They should be stable categories that capture how you organize your knowledge work. Examples from Brian's setup: progressive-platform, org-change-deib-consulting, home-systems-energy, relational-psychology-wellbeing, music-neuroscience, science-communication-craft, personal-home-planning.

Your domains:

1. **[domain-slug-1]**: [one-sentence description]
2. **[domain-slug-2]**: [one-sentence description]
3. **[domain-slug-3]**: [one-sentence description]
4. **[domain-slug-4]**: [one-sentence description]
5. **[domain-slug-5]**: [one-sentence description]
6. **[domain-slug-6]**: [one-sentence description]
7. **[domain-slug-7]**: [one-sentence description]

## Conventions

### Voice and tone (inherited; do not drop)

These are the KAG lattice baseline. They are fixed: the Personal conventions section below adds your preferences on top but cannot relax them.

- Semi-formal, data-driven. No canned affirmations ("Perfect", "Great").
- Pushback before compliance on short-sighted ideas; flag clear limitations before spending significant effort.
- Opinion separated from facts under explicit headers when supporting a decision.
- Em-dash forbidden (use commas, colons, parentheses, or sentence breaks). This is a lattice standard, not a per-user choice.

### Update protocol

In-place edit when a change preserves more than ~70% of structure; a structural refactor produces `CLAUDE-v2.md` with a backlink. History lives in git and in patch manifests, not inline: do not accumulate a rolling changelog in the body or footer.

## [TEMPLATE: Fill in] Personal conventions

These personal preferences layer on the inherited baseline in the Conventions section above; where they conflict, the inherited baseline wins (for example, the em-dash ban holds regardless of what you set here).

These shape how Claude writes for you. Fill in or remove sections that don't apply.

- **Tone preferences:** [e.g., conversational, terse, formal, casual]
- **Response length:** [e.g., lean by default, full explanations, somewhere between]
- **Em-dash:** [allowed / forbidden]
- **Decision-supporting format:** [Facts then Opinion / inline / other]
- **Output defaults:** [single recommendation / option menu]
- **Quality bar:** [evidence-based, hand-wavy, somewhere between]
- **Anti-patterns to flag:** [list any patterns Claude should call out when they emerge]

## Directory structure

```
your-personal-knowledge-system/
├── CLAUDE.md                    This file
├── README.md
├── STATUS.md                    Daily rollup read by the hello brief
├── BACKLOG.md                   Lower-priority items for the hello brief
├── CHANGELOG.md
├── .gitignore
├── kag-user-profile.json        Identity + pilot-mode marker (from the .template)
├── .claude/                     Session hooks (from dot-claude/; gitignored)
├── docs/                        Onboarding: registrations + getting started
├── skills/                      Submodule → Kosek-Advisory-Group-LLC/skills
├── knowledge-base/              Your operational stores
│   ├── *.jsonl                  Per-store records
│   ├── drafts/                  Skill #03 prose outputs
│   └── syntheses/               Skill #01 synthesis outputs
├── career/                      Resume-tailoring reference data (consumer-side per TD-015)
│   ├── bullet_library.json      Bullet content, role profiles, ATS metadata
│   ├── contact_block.json       Contact info, cert URLs, career history, education
│   └── README.md                Source-of-truth + maintenance protocol
├── inbox/                       Mobile/async capture drop zone
└── patches/                     Patch manifests
```

## Resume tailoring reference data (career/)

The shared `resume-tailoring` skill (Skill #13, `skills/resume-tailoring/`) reads personal
bullet content and contact information from this repo's `career/` directory rather than from
inside the skills submodule. This keeps personal data out of the shared engine repo per
architectural commitment #1 (content-agnostic by default) and unblocks future consumers (Jessie,
clients, alpha-test users) from inheriting another operator's personal data.

**Files (each consumer maintains their own):**

| File | Purpose | Schema source |
|---|---|---|
| `bullet_library.json` | `bullets` (stable `BK-NNN` IDs with per-bullet `role_targets`, `competencies`, `has_metric`, `ats_keywords`), `about_me_versions`, `taglines`, `role_targets`, and `role_profiles` (role tag to its default tagline and about-me) | Rich schema documented inline in the file's `_doc`; worked example at `skills/resume-tailoring/applications/_synthetic/career/` |
| `contact_block.json` | `contact`, `cert_urls`, the name-banner / cover-letter-sender / certifications-line segment variants, career history (Tier 1/2/3 roles), education, `tech_proficiencies_default`, and `languages_line` | Rich schema documented inline in the file's `_doc`; worked example at `skills/resume-tailoring/applications/_synthetic/career/` |

The onboarding stubs in `skills/templates/personal-repo/career/` ship in this rich schema with bracketed
`[placeholder]` values, so a freshly-copied `career/` already matches what the engine reads. resume-tailoring
refuses to run while any `[bracket token]` remains or `bullets` is empty (the engine's placeholder guard,
TD-051), so an unfilled stub fails loudly at load time rather than rendering a misattributed resume.

**Path resolution.** The engine resolves the `career/` location via (in order):

1. `--references-path <path>` CLI flag on `build_resume.py` / `build_cover_letter.py` /
   `parse_jd.py` / `validate_resume.py` / `applications/<Company>/_acceptance_test.py`
2. `$KAG_REFERENCES` env var (set once at the shell level for sticky resolution)
3. Convention search: walks up from cwd looking for a `career/` directory containing
   `contact_block.json`. When the session opens against this repo's root, this resolves
   automatically.
4. Sibling fallback: `skills/../career/` (works when `skills/` is mounted as a submodule
   of this repo)

There is intentionally no legacy in-repo fallback: the engine repo holds no personal data.
If none of the four resolve, `_engine.resolve_references_dir` raises `FileNotFoundError`
with the chain printed inline.

**Maintenance protocol.**

- This `career/` directory is the **single source of truth** for the consumer's resume-tailoring
  inputs. Updates here propagate to the next engine invocation without code changes.
- New bullets land in `bullet_library.json` with the next available `BK-NNN` ID and
  `status: active`. Never hardcode bullets in per-application `config.json`; keep the library
  canonical so the audit trail is preserved.
- Per TD-011 (coordinated with TD-015): bullets are also mirrored into
  `knowledge-base/evidence-store.jsonl` as `self-claim` evidence records, with the original
  `BK-NNN` preserved as an alias in `extension_metadata.bullet_id`. This mirroring is
  **consumer-side only**: both stores live in this repo; the skills repo is never involved. As a
  new consumer, maintain `bullet_library.json` as the file you edit; treat the evidence-store
  records as the engine-managed mirror, not a second place to hand-edit.
- Updates to `contact_block.json` (phone, email, new certification, address) take effect on the
  next engine run.

**Validation.** After any change to `bullet_library.json` or `contact_block.json`, regenerate a
resume for one saved job description and confirm the output is well-formed and reflects your edit.
The engine resolves your data via `--references-path career/` (or convention search from this
repo's root). Acceptance fixtures that contain real applicant data are kept consumer-side, never
in the shared skills repo.

## Skills you have access to

All skills in the `skills/` submodule are available. For the full, always-current list see
`skills/SKILLS-SUMMARY.md` rather than a copy here (a copy drifts out of date).

If you are set up for a job search (the default pilot scope), these are the ones you will use:

- **#12 job-application-orchestrator** - your front door; it drives the rest
- **#15 job-analysis** - reads a job description and scores fit
- **#13 resume-tailoring** - tailors your resume and cover letter (reads `career/`)
- **#16 salary-negotiation** - offer-stage support
- **#00 capture-and-route** - jot notes and observations
- **#18 cognitive-reframing** - optional support for the emotional side of a job search

The orchestrator also uses #02 evidence-layer, #04 sequencing, and #05 pipeline-tracker under the
hood; you do not call those directly.

Update the submodule periodically to pull in newer skills:
```
git submodule update --remote skills
git add skills && git commit -m "Bump skills submodule"
```

## Known onboarding constraints

Three implicit design assumptions in the engine that new consumers must address explicitly. Documented here per the 2026-05-26 Counterpoint content-agnostic audit (TD-030).

### Single-operator-per-PKS (hard constraint)

This repo is designed for exactly one named operator. Consumer identity resolves via `git config user.email`. The schema-touch gate, LEDGER- records, GOAL- records, and PICKUP- records all carry the operator email as the identity key. If two people share a single PKS repo instance, session ledger queries, goal tracking, and the hello brief will interleave records from both operators with no separation.

**Correct multi-user architecture:** one PKS repo per operator (naming: `<user>-personal-knowledge-system`), each pointing at the same shared `Kosek-Advisory-Group-LLC/skills` submodule. The skills engine is content-agnostic and shared; the stores are per-operator and private.

There is no current migration path for splitting a shared PKS into two. Do not attempt to run two operators against one PKS.

### Career-launch tier calibration (requires initial setup before activating auto-mode)

Skill #12 (job-application-orchestrator) auto-mode thresholds and Skill #15 (job-analysis) 5-dimension fit weights are calibrated to the founding operator's applicant profile. A new operator who activates auto-mode with default gate-config threshold files will receive verdicts calibrated for someone else's background.

**Required before activating auto-mode:**
1. Open `job-application-orchestrator/gate-configs/` and review each threshold file. Override values that do not match your applicant profile.
2. The fit-score calibration-pending flag marks the first 10 records as "uncalibrated." Do not use auto-mode verdicts until the calibration window closes (10 real records processed).
3. If you need UGSP-compliant operations, leave `--compliance-mode on` (the default). If you are using the career-launch tier purely for personal fit assessment and do not need regulatory compliance machinery, see TD-031 for the `--compliance-mode off` path (pending Draft 4 implementation).

### Domain category field schemas (requires definition, not just name substitution)

The `## Your domain inventory` section above asks you to name your domain categories. That is the start, not the end. Skill #00 (capture-and-route) routes observations into per-category stores using field schemas that define the domain-specific attributes for each category. The template fills in the category *names* but not the *field schemas*.

**Required steps:**
1. Define your 7+ domain categories above.
2. Open `skills/capture-and-route/SKILL.md` §Category Schema and read the field schema pattern for any existing category that resembles yours.
3. Author a corresponding field schema block for each of your categories, either by adapting an existing one or writing new fields. These schemas live in your capture-and-route invocation config, not in the engine SKILL.md.

Without this step, observations will route into your categories but domain-specific fields will be empty, degrading synthesis quality and downstream skill outputs.

---

## Identity and pilot mode (kag-user-profile.json)

If this repo has a `kag-user-profile.json` at its root, the hello skill (#14) reads it to greet
you by name and lead with your featured skill. Pilot users get a guided brief that puts the
job-application-orchestrator first and offers the full toolset tour as an option. The file also
carries your `privacy_defaults` (your git namespace and your own repo's self-source), so skills use
your settings rather than another operator's. The fields are documented in
`docs/GETTING-STARTED.md`; the full schema and resolution rules are in
`skills/knowledge-base-reference/operator-profile-contract.md`. Your `operator_id` (and the
compatibility `operator_email`) should match your Git `user.email` and your `KAG_OPERATOR_ID`
environment variable so your records carry your identity.

## Session loading

At session start:
1. Read this CLAUDE.md fully.
2. Identify task class (capture, synthesis, narrative, sequencing, pipeline tracking, etc.)
3. Read the relevant SKILL.md from `skills/` submodule.
4. Sweep `inbox/` if there are unprocessed captures.

## Standing Conventions

Lattice-standard SOPs this repo participates in. The automated part is wired by the `.claude/` session hooks (shipped as `dot-claude/`; rename on setup).

- **Commit auto-logging.** The SessionStart hook (`skills/tools/log_unlogged_commits.sh`) appends a structured entry to `commit-log.jsonl` for each unlogged commit, which the hello brief (#14) reads. A fresh commit produces a log entry the next time the brief renders.
- **Lessons capture.** Engineering-practice lessons live engine-side in the `skills/` submodule's `lessons/`, not here. Your own observations, ideas, and insights are captured into your stores via skill #00 capture-and-route, not a local `lessons/` directory.

## What never to do without explicit instruction

- Delete from any store (synthesis, evidence, projects, constraints, sequences, taxonomies, items, snapshots, coherence-flags)
- Modify a SKILL.md (skills are owned upstream in the org repo, not editable from here)
- Push to `main` from a non-desktop session
- Author bulk fixtures here (those go in the upstream skills repo)

## Cross-references

- **Shared skill ecosystem:** [https://github.com/Kosek-Advisory-Group-LLC/skills](https://github.com/Kosek-Advisory-Group-LLC/skills)
- **Sister personal repos:** [TEMPLATE: list other family members' personal repos if shared awareness is helpful, e.g., Brian's]
- **LLC business:** [https://github.com/Kosek-Advisory-Group-LLC/kosek-consulting](https://github.com/Kosek-Advisory-Group-LLC/kosek-consulting). For engagement work, open a session against that repo, not this one

**Last reviewed:** [DATE]
