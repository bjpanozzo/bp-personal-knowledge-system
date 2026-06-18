# Getting started

Plain-English first-run guide for a new user of this personal-knowledge-system. No coding
required. If someone set this repo up for you, skip to "Your first session."

## What this is

This is your private workspace. It holds your data (your job applications, your resume material,
your notes). The actual capabilities come from a shared library called `skills/`, which is the
Kosek Advisory Group toolset. You use those skills; you do not edit them.

The headline tool is the **job-application-orchestrator**: paste a job description and it walks
you, step by step and with your approval at each gate, through analyzing the role, tailoring your
resume and cover letter, and tracking the application. That is what you are here to use.

One thing to expect: the feedback here is honest, not just encouraging. If a role is a weak fit or
a resume bullet is thin, Claude will tell you and explain why. That is by design; it is what makes
the output worth trusting.

## Before you start

Make sure the accounts and installs in [REGISTRATIONS-CHECKLIST.md](REGISTRATIONS-CHECKLIST.md)
are done. For a guided onboarding, the person setting you up will have handled the Git and GitHub
parts; you mainly need Claude Pro and the Claude Code desktop app.

## Your first session

1. Open the **Claude Code desktop app**.
2. Open this folder (your `...-personal-knowledge-system` repo) as the working folder.
3. Type `hello` and send it.

You will get a short, friendly orientation with your primary tool front and center, plus the
option to take a fuller tour of the wider toolset if you are curious. From there, to apply to a
job, just say something like:

> apply to this: [paste the full job description]

and follow the prompts. You approve each step; nothing is sent anywhere on your behalf.

## The profile (kag-user-profile.json)

A small file at the root of your repo, `kag-user-profile.json`, tells the brief who you are, what
to put first, and your privacy defaults. Its fields:

| Field | Meaning |
|---|---|
| `user_role` | `pilot` for a guided pilot user |
| `display_name` | Your first name, used in the greeting |
| `operator_id` | Your identity; should match your `KAG_OPERATOR_ID` environment variable (may be your email or an opaque ID) |
| `operator_email` | Your email; should match your Git config (kept for compatibility; `operator_id` is preferred when both are set) |
| `featured_skill` | The skill the brief leads with (default `job-application-orchestrator`) |
| `skill_scope` | `job-search-curated` shows your curated job-search toolkit (the skills bundled in this pilot distribution) |
| `tour_enabled` | `true` offers the full architecture tour as an option |
| `privacy_defaults` | Your privacy posture (see below) |

`operator_id` and `operator_email` are a declaration of who you are; the system still resolves
your real identity from your `KAG_OPERATOR_ID` environment variable (then your Git config). If the
declaration and the resolved identity disagree, the brief surfaces the mismatch rather than
trusting the file.

### privacy_defaults

These tell the skills how to treat your data by default, so nothing assumes another person's
setup. Fields:

| Field | Meaning |
|---|---|
| `self_source_id` | Your own repo's short name (e.g. `jane-personal-knowledge-system`), so skills recognize "this is my own data" |
| `personal_namespace` | Your Git namespace (your GitHub account or org); repos there are masked by default |
| `personal_namespace_classification` | `mask` by default (abstract your data in shared output), or `suppress` to hide it entirely. You cannot set this to `open`: to make one specific repo public, list it in `privacy-source-classifications.json` instead |
| `default_record_gradient` | `default` for normal records; you rarely change this |

Anything not listed in your `knowledge-base/privacy-source-classifications.json` is hidden by
default (the safe choice); `privacy_defaults` cannot loosen that. The full rules live in
`skills/knowledge-base-reference/operator-profile-contract.md`.

## Getting help

- Ask Claude directly in plain English ("how do I ...", "what does this step do?").
- For anything you are unsure about, the person who onboarded you is your first point of contact.
- You will not break anything by exploring. You have no ability to change the shared skills, only
  your own data, and the destructive actions are guarded.
