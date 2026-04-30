# PROJECT_SETUP_README.md

## Purpose

This document explains how to set up and use the commercial LLM Wiki project as a local working vault and repo.

It is for:
- the main operator
- future collaborators
- demo preparation
- setup recovery on a new machine

---

## What this file is for

This file explains how to set up the project on your computer.

Use this guide when you need to:

- create or clone the project folder
- open the project in Obsidian
- set up Git
- choose an editor such as VS Code or WebStorm
- understand how Codex or another AI coding assistant can work with the vault

If you are not technical, do not worry about understanding every tool immediately.

Start with Obsidian and Git basics first.
Codex, CLI tools, and automation can come later.

---

# 1. Recommended working model

Use the project like this:

- Obsidian = reading, linking, graph view, vault navigation
- VS Code or WebStorm = editing, diff review, regex cleanup, repo maintenance
- Git = version control and safe checkpoints
- Codex CLI / Codex IDE extension = coding and repo assistance
- Obsidian CLI = programmatic access to the vault from the terminal

Recommended repo model:

```text
company-commercial-wiki/
├── raw/
├── wiki/
├── logic/
├── docs/
├── README.md
├── index.md
└── log.md
```

---

# 2. Initial local setup

## 2.1 Create or clone the project

If starting fresh:

```bash
mkdir company-commercial-wiki
cd company-commercial-wiki
git init
```

If using an existing repo:

```bash
git clone <your-private-repo-url>
cd company-commercial-wiki
```

## 2.2 Recommended branch setup

Keep `main` stable and demo-ready.
Do active work in `dev` or feature branches.

Example:

```bash
git switch -c dev
```

---

# 3. Install Obsidian

Download Obsidian from the official site and install it for your platform.

After install:
1. Open Obsidian
2. Choose **Open folder as vault**
3. Select the project root folder
4. Confirm top-level folders such as `raw/`, `wiki/`, `logic/`, and `docs/` are visible

---

# 4. Enable Obsidian CLI

Obsidian CLI lets you control Obsidian from the terminal.

Requirements:
- use the Obsidian 1.12 installer line
- update to installer version 1.12.7 or newer
- the Obsidian app should be running

Setup:
1. Open Obsidian
2. Go to **Settings → General**
3. Enable **Command line interface**
4. Follow the registration prompt
5. Restart the terminal

Basic commands:

```bash
obsidian help
obsidian
```

---

# 5. Install an IDE

Use one of these:

- VS Code
- WebStorm

Recommended usage:
- Obsidian for vault navigation and backlinks
- IDE for editing, search, diff, and git review

If using WebStorm or VS Code, open the same vault/repo folder you use in Obsidian.

---

## Recommended tool order

For a beginner, use the tools in this order:

1. Obsidian — read and navigate the vault
2. Git — save safe checkpoints
3. VS Code or WebStorm — edit and review files
4. Codex or another AI assistant — help with larger maintenance tasks
5. CLI tools — optional advanced usage

You do not need all advanced tools on day one.

---

# 6. Install Codex

## 6.1 Codex CLI

Install with npm:

```bash
npm install -g @openai/codex
```

Or with Homebrew:

```bash
brew install codex
```

Then run:

```bash
codex
```

You can sign in with your ChatGPT account or an API key when prompted.

## 6.2 Codex IDE extension

OpenAI currently documents official Codex IDE extension downloads for:
- Visual Studio Code
- Cursor
- Windsurf

If you use VS Code, install the official Codex extension there.

If you use WebStorm, treat Codex CLI as the primary official Codex path unless OpenAI later documents a JetBrains extension.

---

# 7. Codex + Obsidian practical model

A simple and safe model is:

- keep the vault as a normal git repo
- open the same repo in Obsidian and your IDE
- run Codex in the repo root
- let Codex work on markdown, logic files, and schemas in the repo
- use Obsidian CLI when you want terminal-level interaction with the vault

Important:
there is no need to force a direct “Codex connects to Obsidian app” model.

A better practical model is:
- Codex works on the repo files
- Obsidian reads the same repo as a vault
- Obsidian CLI provides terminal/vault actions where useful

---

# 8. Recommended git hygiene

Use `.gitignore` for local/editor state.

Recommended entries:

```gitignore
.DS_Store
.idea/
.obsidian/workspace.json
.obsidian/graph.json
.obsidian/cache/
.obsidian/workspace-mobile.json
*.tmp
*.bak
```

Track:
- markdown content
- logic files
- schemas
- docs
- repo metadata you intentionally share

Avoid tracking:
- machine-specific editor state
- temporary UI layout files
- accidental duplicate wrapper files such as `*.md.md` or `*.yaml.md`

---

# 9. Recommended operator docs

These files should exist and stay maintained:

- `README.md`
- `docs/SETUP_OBSIDIAN.md`
- `logic/USER_WORKFLOWS.md`
- `logic/PROMPT_LIBRARY.md`
- `logic/RULES.md`
- `logic/LINT.md`
- `logic/schemas/*.yaml`

Recommended role of each file:

## README.md
High-level project overview for humans.

## docs/SETUP_OBSIDIAN.md
How to open and use the project as a vault.

## logic/USER_WORKFLOWS.md
Short operator workflow map.

## logic/PROMPT_LIBRARY.md
Prompt library with full reusable exact prompts.

## logic/RULES.md
Project rules and governance.

## logic/LINT.md
Review checklists and validation criteria.

## logic/schemas/*.yaml
Structural source of truth.

---

# 10. Recommended README additions

Your main README should include:
- what this project is
- folder structure
- how to open it as an Obsidian vault
- how to initialize git
- what files operators should read first
- how workflows and prompts are split
- where schemas live
- where logs and registries live
- what is considered high-risk content
- how to do a safe review-only pass

Recommended “read first” order for another operator:
1. `README.md`
2. `docs/SETUP_OBSIDIAN.md`
3. `logic/USER_WORKFLOWS.md`
4. `logic/PROMPT_LIBRARY.md`
5. `logic/RULES.md`
6. `logic/LINT.md`

---

# 11. Recommended first terminal commands

```bash
git status
git branch
git switch -c dev
rg "SRC-" wiki/
rg "PROD-" wiki/
rg "PRICE-" wiki/
rg "TERM-" wiki/
```

If Obsidian CLI is enabled:

```bash
obsidian help
```

If Codex CLI is installed:

```bash
codex
```

---

# 12. Best next documentation addition

Besides the current README, add:

- `docs/PROJECT_SETUP_README.md`
- `docs/VAULT_HEALTH_CHECK_PROMPT.md`

These help with:
- onboarding
- nightly review
- handoff to another operator
- keeping the system maintainable without relying on chat memory

---

# 13. Recommended current next step

Run an overall direction review using the vault health prompt before doing more broad edits.

Then:
1. fix only what the review flags
2. verify the fixes
3. commit on `dev`
4. merge to `main` only when stable
