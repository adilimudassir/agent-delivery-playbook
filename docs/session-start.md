# Session start, task commencement, and handoff

Use intent and immediate context. These are conversation conventions, not shell commands or an unattended scheduler.

## Command meanings

| Request | Response |
| --- | --- |
| Begin / start / status | Orient, report verified progress, and identify eligible work. No new implementation is selected by this phrase alone. |
| Next task / begin next task | Recommend the next eligible task and present a concise brief. Mention unfinished work and relevant findings. |
| Choose T-001 / start T-001 with no clear implementation context | Present the task's scope and decision. |
| Implement T-001 / fix this bug / build this feature | Record a bounded brief and execute the clearly authorized work. Ask only for material missing scope or uncovered effects. |
| Proceed / approved | Resolve against the immediately preceding concrete proposal. Reuse it when unambiguous; clarify only an unresolved material target. |
| Resume T-001 | Check prior permission, pause conditions, ownership, and interrupted effects, then continue covered work. An authorized explicit resume can lift the corresponding pause. |
| Skip F-001 and implement T-001 | Record the finding disposition and continue if real dependencies permit. Do not silently implement F-001. |
| Complete T-001 through T-003 | Treat as a bounded batch when scope is clear. Preserve each task's dependencies, external-action limits, and stop conditions. |
| Pause / stop | Stop at the next safe boundary, preserve work, and record the exact position. Do not start further mutations. |

If a requested change is already clear and authorized, record the brief while doing the work. The document is a durable record, not a reason to repeat the user's instruction back as a permission question.

## Opening sequence

1. Read root instructions, PROJECT.md, the short handoff index, and the selected task. Read relevant nested instructions. When selecting work, read the roadmap and applicable findings.
2. Inspect branch, full revision, working tree, shared claims, and available issue/PR/check evidence. Preserve uncommitted work. State access limitations; old recorded evidence is not a fresh observation.
3. Establish the last task's actual result, unfinished checkpoint, current permission, and next owner. Do not infer live success from a commit message or merged PR.
4. Recommend work that advances a current goal and has satisfied dependencies. If none is eligible, identify the concrete unblock action. Do not require fresh production access merely to discuss task choices.

Keep the opening report brief:

> Last work: task, verified outcome, and evidence. Current position: remaining work, owner, permission, and blockers. Recommended next action: task/checkpoint, reason, relevant findings, and any actual decision needed.

On resumption, verify that referenced evidence remains accessible and sufficiently fresh for the next action. Reconcile the previous executor before taking over. Read history only when needed to resolve a discrepancy or understand a decision.

Check the selected model profile and the next role's capability requirements. Reuse valid choices within scope; record runtime limitations or changed settings without requesting the same authorization again.

## The implementation brief

Explain the outcome, why it is selected, included/excluded scope, dependencies, review tier, planned checks, relevant findings, and intended delivery. Add risk, cost, target, downtime/window, recovery, and executor only where they matter. Record existing authorization and identify uncovered decisions explicitly.

Include the required roles and their proposed capability/model/effort using [model selection](model-selection.md). Distinguish preferred settings from mandatory requirements and confirm which controls the runtime exposes. Use only the roles required by the task; humans need no model settings.

The brief may be a small task file or a canonical issue body. Do not duplicate it across both. For a new finding, give separate work its own ID when it can be independently selected. Prefer links to stable evidence over repeating large plans or logs.

## Handoff and closeout

Update the current handoff section in the canonical task after a meaningful checkpoint, completion, interruption, or pause. Use [the handoff template](../templates/handoff.md). It must answer:

- What outcome was requested, and what is actually verified?
- Which branch, revision, PR/artifact, and evidence describe the current position?
- What is incomplete, uncertain, blocked, or awaiting a decision?
- What permission remains valid, and what pause or limits apply?
- Who owns the next action, which paths/resources are claimed, and has the former owner released them?
- What capability or model requirement does the next role have, and is any runtime limitation or substitution unresolved?
- What exactly should the next worker do after checking current state?

Record actions that may still be running and uncertain external effects before a retry. Include uncommitted paths or a safe recovery location when work is not committed. Do not put secrets or sensitive artifacts in the handoff.

Keep [tasks/handoff.md](../tasks/handoff.md) as a compact pointer index to active task handoffs. The task record owns mutable status, permission, and next action. Archive superseded narratives under the task or a linked history file; archived instructions describe past events and do not authorize current work.

Store an exact-commit review receipt outside the commit it evaluates. A handoff can refer to an earlier immutable commit or external receipt; adding its own future final hash would change that hash again.

The completion report leads with the intended outcome and checks, then remaining risks and follow-up owners. State whether the result is prepared, reviewed, merged, executed, or verified. End with a recommendation; advance only within an already-authorized batch.
