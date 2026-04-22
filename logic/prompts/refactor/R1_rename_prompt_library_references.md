# R1 — Rename prompt library references

## Purpose

Update internal references after renaming or reorganizing the prompt library system.

## Prompt body

```text
Follow:
- logic/SYSTEM_PROMPT.md
- logic/AGENTS.md
- logic/RULES.md
- logic/SKILL.md
- logic/LINT.md

Update only these files:
- [exact file list]

Goals:
- rename all intended references from the old prompt-library path/name to the new one
- update wording so “prompt library” is used consistently where appropriate
- update title/header content where needed
- preserve all workflow-to-prompt references
- do not change the meaning of workflows, rules, or setup instructions
- do not modify any other files

Rules:
- do not invent new workflows or prompts
- preserve existing IDs, filenames, and valid wikilinks except for the intended rename / refactor
- keep wording concise and structurally consistent
```