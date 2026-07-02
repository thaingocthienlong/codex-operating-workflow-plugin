# Codex Operating Workflow Plugin

Private Codex plugin marketplace for a portable operating workflow skill.

## What It Provides

- `codex-operating-workflow` skill for lane selection, tool routing, verification, reporting, and rollback.
- Reusable templates for task briefs, verification records, handoff reports, and phase logs.
- No MCP servers, hooks, apps, or background automation.

## Install From A Clone

From any device with this repository cloned:

```powershell
codex plugin marketplace add .\.agents\plugins
codex plugin add codex-operating-workflow@personal
codex plugin list
```

Start a fresh Codex thread after install so the skill list reloads.

## Starter Prompt

```text
Use codex-operating-workflow for this repo task. Classify the lane first, route tools, verify, and report rollback.
```
