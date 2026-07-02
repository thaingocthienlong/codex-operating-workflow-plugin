# Verification Record

## Scope Verified

Describe the change or claim being verified.

## Commands

| Command | Expected Result | Actual Result |
| --- | --- | --- |
| `git status --short` | Clean or only intended files shown. |  |
| `git diff -- <changed-files>` | Diff contains only intended changes. |  |

## Tooling Checks

| Check | Expected Result | Actual Result |
| --- | --- | --- |
| Config parse | Parses successfully. |  |
| Hook parse | Parses successfully. |  |
| Tool/plugin list | Expected enabled/disabled state shown. |  |

## Test Or Review Evidence

- Record relevant lint, typecheck, unit, build, browser, security, or docs checks.

## Gaps Or Deferred Checks

- Record any check not run and why.

## Result

Choose one: passed, failed, blocked, deferred.
