# Handoff — {{task_id}}

Copy this section into the canonical task record. `tasks/handoff.md` should
point to that record; it should not become a second detailed task history.

| Field | Value |
| --- | --- |
| Canonical task | Path or issue URL |
| Status | One of the configured lifecycle statuses |
| Updated | ISO 8601 timestamp with timezone |
| Current / next owner | Person or agent / run identifier |
| Reason for handoff | Completion, pause, interruption, transfer, or context limit |

## Verified position

- Intended outcome:
- Last completed step and what its evidence actually establishes:
- Current working branch / PR and known revision:
- Review and verification evidence references; unavailable checks:
- External actions performed, with observed outcomes, if any:

Distinguish prepared content, merged source, published or deployed artifacts,
and observed live behavior. Do not infer completion from a commit title or a
closed PR.

## What remains

- Remaining acceptance criteria:
- Exact blocker, decision, or dependency:
- Next action, expected result, and responsible owner:
- Relevant findings, existing dispositions, and revisit triggers:

## Permission and ownership

- Existing authorization and its scope:
- Active pause or stop condition:
- Actions awaiting a separate decision:
- Path / resource claim retained, transferred, or released; coordination link:
- Previous executor confirmed stopped, or its state remains unknown:

## Resume safely

- Working directory, uncommitted work, and files to preserve:
- Running processes, pending jobs, or uncertain actions to reconcile:
- Evidence or environment state that must be refreshed before continuing:
- Next role's capability/model requirement, routing-record reference, and any unresolved substitution or runtime limitation:
- Whether the next role requires a new independent run or a human reviewer:
- Recovery or cleanup still due, its owner, and trigger:

Use `none` only when checked and `unknown` when not established. A new session
should be able to identify its next permitted action without reading the entire
conversation. Finishing this task does not select the next task automatically.
