# career/

Consumer-side reference data for the `resume-tailoring` skill (#13). Your bullets and contact
information live here, in your own personal-knowledge-system repo, never inside the shared
`skills/` submodule. This keeps your personal data out of the shared engine and is required by
the ecosystem's content-agnostic architecture.

## Files

| File | Purpose |
|---|---|
| `bullet_library.json` | Your resume bullets (stable `BK-NNN` IDs, each with `role_targets`, `competencies`, `has_metric`, `ats_keywords`), plus `about_me_versions`, `taglines`, and `role_profiles` (which map a role tag to its default tagline and about-me text) |
| `contact_block.json` | Your contact block, `cert_urls`, the name-banner / cover-letter-sender / certifications-line segment variants, career history (Tier 1/2/3 roles), education, default tech proficiencies, and languages line |

Both files ship as onboarding stubs in the **rich schema the engine actually reads**: every value is a
bracketed `[placeholder]` you replace during onboarding, inside the full structure the engine consumes.
The inline `_doc` field in each file is the field-by-field guide. For a complete, filled, fictional
worked example, see `skills/resume-tailoring/applications/_synthetic/career/`.

## How the skill finds this directory

The engine resolves `career/` in this order:

1. `--references-path <path>` flag on the skill's scripts
2. `$KAG_REFERENCES` environment variable (set once for sticky resolution)
3. Convention search: walks up from the current directory looking for a `career/` directory that
   contains `contact_block.json`. When you open a session at this repo's root, this resolves
   automatically.
4. Sibling fallback: `skills/../career/`

If none resolve, the engine raises a clear `FileNotFoundError` with the search chain printed.

## Maintenance

- This directory is the single source of truth for your resume-tailoring inputs. Edit here; the
  next run picks up the change with no code edits.
- New bullets get the next free `BK-NNN` ID and `status: active`. Keep the library canonical
  rather than hardcoding bullets into individual applications, so your audit trail stays intact.
- Updates to `contact_block.json` (new phone, new certification, new role) take effect on the
  next run.
- Until you fill these stubs in, resume-tailoring refuses to run: it raises a placeholder error
  while any `[bracket token]` remains or the `bullets` list is empty. That guard is intentional. It
  stops the engine from generating a resume that carries `[Full Name]` or someone else's identity.
  Replace the bracketed values with your own and the next run proceeds.

## Privacy

Everything in this directory is yours and stays in your repo. Do not copy another person's
`career/` data into yours, and do not commit yours anywhere but your own private PKS repo.
