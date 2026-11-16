# Task records

## One authority for each fact

| Fact | Canonical location |
| --- | --- |
| Project settings and global pause, if any | PROJECT.md |
| Current goals and scheduling priority | roadmap.md |
| Task scope, status, acceptance, permission, and current handoff | The task record: Markdown by default, or its issue body when configured |
| Active shared claim | Configured shared registry/coordinator acknowledgement; link from the task |
| Exact-candidate verdict | External review receipt bound to that candidate |
| Cross-task finding and disposition | findings.md; task-specific findings may remain in the task |
| Historical events | Linked task history or archive |

The handoff index and roadmap are navigation aids. Do not maintain competing status, permission, or next-action copies there. If records disagree, inspect the authoritative source and current evidence before proceeding; do not guess from the most convenient summary.

## IDs and task files

Use `G-001` for a goal, `T-001` for a bounded task, `T-001/C1` for an optional checkpoint, and `F-001` for a finding. A coordinator allocates IDs in a shared project to prevent collisions. Keep existing IDs as aliases when adopting this convention.

In Markdown mode, copy [the task template](../templates/task.md) to `tasks/items/T-001-short-title.md` and fix relative links for the new location. A task file remains its canonical record after completion, preserving stable links. Archive only superseded narrative when useful; keep the final outcome and evidence pointers in the task.

In issue mode, use the same schema in the issue body, with repository URLs for links. Repository indexes link the issue. An issue's open/closed state alone is insufficient: retain the playbook status and checkpoint fields. Public issue authors can request work; they do not automatically control repository or operational authorization.

## Status and checkpoints

Statuses are `backlog`, `ready`, `in_progress`, `in_review`, `blocked`, `paused`, `done`, and `cancelled`, as defined by [the operating method](../docs/operating-method.md). Checkpoint IDs identify separately controlled steps, not extra parent task statuses. Record current checkpoint, implementation/review/delivery/verification position, and exact next action within the task.

Store authorization references and review receipts with enough context to resume without the original chat. When those records are private, use authorized durable locations and summarize limitations publicly. Never treat an inaccessible receipt as a verified pass.

## Keep startup small

Maintain [handoff.md](handoff.md) as links to current task handoff sections plus a short orientation. Aim for one screen; read detailed history only when needed. Use [roadmap.md](roadmap.md) to choose work. Use [findings.md](findings.md) for issues that span tasks, without forcing unrelated repairs into every task.
