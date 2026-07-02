---
name: codex-operating-workflow
description: Use for repo tasks, workflow setup, planning, verification, handoff, tool routing, and questions about how Codex should operate. Classifies work into lanes, routes tools, requires verification for meaningful changes, and avoids heavy process for tiny quick answers.
---

# Codex Operating Workflow

Use this skill at the start of repo work, workflow setup, implementation planning, verification, handoff, or tool-routing decisions.

## Core Rule

Classify the lane first. Use the lightest workflow that honestly covers the request. Do not add logs, subagents, or heavyweight planning to tiny quick-answer tasks.

## Intake Lanes

| Lane | Use When | Required Output |
| --- | --- | --- |
| Quick answer | Simple explanation, command output, path lookup, or one-shot read-only answer. | Direct answer with file or command evidence when relevant. |
| Read-only audit | Review, inventory, risk check, or planning where no repo files should change. | Findings first, then evidence and deferred checks. |
| Docs change | Markdown, runbook, workflow, checklist, or planning artifact update. | Diff, placeholder scan, secret-value scan, and commit when requested or part of plan. |
| Code/config change | Source, package config, scripts, app behavior, or repo settings change. | Plan, scoped edit, relevant tests, diff, and rollback note. |
| Security-sensitive change | Auth, secrets, DRM, authorization, webhooks, crypto, dependency risk, or data exposure. | Threat/risk framing, security scan or targeted review, tests, and no secret values printed. |

## Tool Routing

- Use official Superpowers skills for brainstorming, planning, execution, debugging, TDD, review, and completion gates when those skills are available.
- Use `codebase-memory-mcp` first for code discovery when callable; use `rg` for strings, configs, docs, and non-code files.
- Use Context7 for current library, framework, SDK, CLI, and cloud-service docs before changing or explaining those APIs.
- Use Mem0 for durable context when callable and the task needs cross-session memory.
- Use Codex Security for repository, diff, or finding-level security work.
- Use browser/chrome tooling for browser-visible proof, UI checks, localhost checks, screenshots, and user-facing flows.
- Use GitHub tools for PR, issue, CI, or remote repository work.
- Do not route through stale duplicate process surfaces such as `superpowers-mcp-augment`, `ultipowers`, stale Serena hooks, or disabled local MCPs.

## Standard Flow

1. Read project instructions such as `AGENTS.md` before planning or implementation.
2. Classify the lane and state it when the task is more than a quick answer.
3. Gather current evidence from files, git, and tools before asking questions.
4. Plan before mutation for docs, code/config, tooling, and security-sensitive changes.
5. Keep edits scoped and preserve unrelated user changes.
6. Verify with commands that match the changed surface.
7. Report changed paths, verification result, deferred checks, and rollback.
8. Commit only when requested, when the plan requires it, or when the task's phase explicitly calls for it.

## Subagent Policy

Use subagents for independent audits, large searches, disjoint implementation tasks, or review of completed diffs and verification evidence. Avoid subagents for quick answers, small single-file edits, or work where the next local step depends immediately on the result.

Subagent prompts must include scope, no-secret rules, expected output, and whether file edits are allowed.

## Verification Gates

| Change Type | Minimum Verification |
| --- | --- |
| Read-only audit | `git status --short` when repo cleanliness matters; cite inspected files or commands. |
| Docs change | `git diff -- <changed-docs>`, placeholder scan, secret-value scan. |
| Tooling/config change | Config parse, MCP/plugin list if relevant, fresh-thread verification when tool exposure may change. |
| Code/config change | Relevant unit, type, lint, build, or test commands from repo docs or package scripts. |
| UI/browser change | Relevant automated checks plus browser-visible proof or screenshot when feasible. |
| Security-sensitive change | Targeted tests plus Codex Security scan or documented risk review. |

## Reporting

Persistent logs are required for commits, multi-step work, tool/plugin/MCP/config changes, security-sensitive work, deferred verification, and phase or milestone closure.

Persistent logs are not required for quick answers or one-command read-only checks.

## Rollback Rules

- Prefer disable/archive before deletion.
- Do not delete backups or sensitive artifacts without explicit approval.
- For docs-only commits, rollback is usually `git revert <commit>`.
- For config/tooling changes, record backup path and exact restore action.
- For source changes, record tests and any data or migration rollback needed.

## Templates

Use reference templates when the task needs an auditable artifact:

- `references/templates/task-brief.md`
- `references/templates/verification-record.md`
- `references/templates/handoff-report.md`
- `references/templates/phase-log-entry.md`
