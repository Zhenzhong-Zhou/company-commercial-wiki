# R3 — Workflow / prompt alignment cleanup

## Purpose

Apply a small targeted cleanup pass to keep workflow files, prompt-library structure, and refactor-review prompts aligned.

## Use when

- `logic/USER_WORKFLOWS.md` was updated
- `logic/PROMPT_LIBRARY.md` was reorganized
- prompt IDs or prompt grouping changed
- `R2` review found alignment issues
- you want a small structural cleanup without touching wiki content pages

## Prompt body

```text
Follow:
- logic/SYSTEM_PROMPT.md
- logic/AGENTS.md
- logic/RULES.md
- logic/SKILL.md
- logic/LINT.md
- README.md

Task:
Apply a small workflow/prompt alignment cleanup pass.

Update only these files:
- logic/USER_WORKFLOWS.md
- logic/PROMPT_LIBRARY.md
- logic/prompts/refactor/R2_workflow_prompt_integrity_review.md

Goals:
1. keep `USER_WORKFLOWS.md` and `PROMPT_LIBRARY.md` aligned
2. ensure the default operator path is consistent:
   - B1 — Full maintenance batch
   - F1 — Targeted fix pass
   - K1 — Final verification pass
3. ensure specialized prompts are grouped consistently
4. ensure demo/proof prompts are clearly separated from maintenance prompts
5. ensure R2 describes the current refactored structure accurately
6. remove stale wording, duplicate workflow descriptions, and internal inconsistencies
7. preserve file purpose and readability
8. do not change business knowledge pages

Rules:
- do not invent new business workflows unless clearly needed
- do not modify any wiki content files
- preserve valid file references and prompt IDs
- keep edits concise and structural
- prefer alignment and clarity over expansion

Output:
1. files changed
2. exact alignment fixes applied
3. full revised Markdown for each changed file
4. any remaining structural issues still worth reviewing