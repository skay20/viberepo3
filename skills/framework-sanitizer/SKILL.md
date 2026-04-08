# Framework Sanitizer

Use this skill when the task is to audit or sanitize governance drift in the **VibeRepo base repository**.

Primary protocol:
- `docs/especialidades/framework-sanitizer.md`

## When to use
- After editing `AGENTS.md`, `CLAUDE.md`, `README.md`, `FRAMEWORK_CHANGELOG.md`
- After changing framework-level QA, architecture, or operational contracts
- Before merging framework governance changes to `main`

## Workflow
1. Detect mode from `git remote get-url origin`.
2. If this is not the VibeRepo base repo, stop unless the user explicitly asks to sanitize a derived repo.
3. Read the neutral specialty doc and the listed source-of-truth files.
4. Find concrete drifts:
   - outdated file names or paths
   - inconsistent base/derived semantics
   - changelog obligations that point to the wrong file
   - QA or gate docs lagging behind framework changes
5. Fix the smallest set of files needed to restore consistency.
6. Update `FRAMEWORK_CHANGELOG.md`.
7. Verify with targeted searches that stale references are gone.

## Output
- Short findings list
- Files updated
- Verification status
- Remaining risks, if any

## Hard rules
- Do not invent new framework policy when alignment is enough.
- Do not touch product implementation.
- Do not use `CHANGELOG.md` for base-repo governance changes.
