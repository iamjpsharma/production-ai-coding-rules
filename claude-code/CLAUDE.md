# Project Engineering Rules (`CLAUDE.md`)

## 1. Execution & Cost Guardrails
- **Max 3 Retries:** NEVER retry a failing test, build, or linter command more than 3 times without stopping to report the exact root cause and asking the user.
- **Missing Environment / Auth:** If an environment variable, API key, or system binary is missing, halt immediately instead of guessing workarounds or mocking secrets.
- **Context Hygiene:** Remind the user to run `/compact` after completing a major feature or switching tasks so context does not bloat.

## 2. Code & Refactoring Discipline
- Read the target file and its callers before proposing edits.
- Keep diffs minimal and surgical; do not refactor unrelated modules unless explicitly asked.
- Never silently delete failing tests or relax assertions to make a suite pass.

## 3. Verification Mandate
- Every code change must be verified by running the relevant unit test or type-check command after the final edit.
- Report only observed test results and exact file paths.
