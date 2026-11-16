# Operating method

This document defines the reusable process. [PROJECT.md](../PROJECT.md) supplies local settings, [task records](../tasks/README.md) hold current work, and [session start](session-start.md) interprets the user's intent.

## 1. Define one bounded outcome

A task has a concrete outcome, an owner, scope and exclusions, dependencies, acceptance criteria, a review tier, and a current next action. Use [the task template](../templates/task.md). Small tasks can express these in a few paragraphs. Use a [checkpoint](../templates/checkpoint.md) only when one task contains separately controlled execution steps. Split independently selectable work into separate task IDs.

Select work from goals, dependencies, impact, and existing commitments. Numerical order and priority are not dependencies. An unrelated finding does not block authorized work. Reuse still-valid evidence instead of repeating a completed foundation.

Before implementation, identify relevant findings, recommend action, and explain the effect of deferral. Carry forward valid dispositions. A waived check remains waived; it does not become a pass. Revisit a disposition when its evidence, impact, scope, or agreed review point changes.

## 2. Keep state, permission, and evidence separate

| Task status | Meaning and transition requirement |
| --- | --- |
| backlog | Outcome is proposed; scope or readiness may still need work. |
| ready | Scope, acceptance, dependencies, and execution path are sufficiently understood. This is eligibility, not permission. |
| in_progress | Work is authorized within recorded scope and an effective ownership claim exists. |
| in_review | A candidate and its available validation evidence are ready for the applicable review. |
| blocked | A dependency, access gap, missing evidence, or decision prevents the next required action; name the owner and unblock condition. |
| paused | Work was deliberately stopped; record who paused it, what is affected, and how it may resume. |
| done | All acceptance, delivery, verification, and required cleanup for the selected outcome are complete. |
| cancelled | Work was explicitly withdrawn; record partial effects, cleanup, and why it ended. |

The normal path is `backlog → ready → in_progress → in_review → done`. Return to `in_progress` for corrections or authorized delivery after review. Any unfinished task may become blocked or paused. Record the prior phase and exact restart action; resume only after the cause is resolved and permission and ownership are valid. A cancellation cannot erase real effects or recovery obligations.

Within the task, record implementation, technical review, final verification when required, repository delivery, external execution, and acceptance evidence separately. A merged change can satisfy a code-only task. It does not satisfy an outcome that also requires deployment, runtime checks, data recovery, or temporary-access cleanup.

## 3. Reuse authorization within its bounds

A clear request to implement a bounded change is authority for the requested work and necessary ordinary preparation. Record the concise brief and proceed when scope and permission are clear. Do not manufacture a second approval gate simply because no template was filled out beforehand.

For actions needing a separate decision, prepare the concrete candidate, evidence, affected target, and recovery plan first. Name the missing decision and why existing authority does not cover it. Existing valid authorization persists across routine steps and sessions. Silence, elapsed time, task readiness, issue assignment, and technical review do not expand it.

Record who authorized what, the instruction/reference and time, target and environment, executor if constrained, limits, and any later decision points. A later pause overrides permission for the affected scope. A clear authorized resume can lift that pause; reconcile interrupted effects before proceeding. A material change in scope, target, artifact, risk, or conditions requires reevaluation and only the additional permission that is actually missing.

Classify actions by their effects:

| Action | Handling |
| --- | --- |
| Local reading, editing, and validation | Perform within task scope and tool permissions. Inspect commands for external effects. |
| Commit, push, PR, merge, workflow trigger | Follow recorded repository authority and account for triggered automation. |
| Read-only external observation | Use scoped authorized access; record target and observation time when relevant. |
| Artifact uploads, locks, sessions, probes | Account for storage/access/runtime effects; include them in the relevant scope. |
| Shared service, state, data, access, spending, or release changes | Use named checkpoints and [operational controls](operational-changes.md) appropriate to the actual impact. |

Routine steps already covered by a selected task continue without repeated questions. A bounded batch may be authorized explicitly, with task IDs, limits, stop conditions, and delivery authority. Outside such a batch, finishing a task does not select the next one.

## 4. Claim work and protect concurrent changes

Record the task/checkpoint, owner or agent run, branch/worktree, allowed paths, shared resources, claim time, last confirmation, and release/handoff state. Before claiming overlapping work, inspect the configured shared registry and obtain the coordinator's acknowledged assignment or the current owner's handover. Resolve conflicting claims before writing.

Use isolated task branches or worktrees. One worker owns each changed path at a time; shared mutable resources have one executor. Separate branches do not isolate a database, deployment target, or infrastructure state. Issue assignments and comments coordinate people; native locks, deployment queues, or serialized executors enforce exclusion where needed.

A stale timestamp, absent heartbeat, or disappeared session is a reason to investigate, not permission to take over. Establish the prior executor's status and reconcile uncertain effects. A sole-worker local record permits local coordination only; it does not reserve a remote resource. If a shared claim cannot be established, continue non-conflicting preparation and report the blocked mutation.

## 5. Implement, validate, and review

Use [the model selection guide](model-selection.md) to assign suitable capabilities and reasoning effort to the roles this task actually needs. Record the role plan, actual run identities, and observable settings in the task. Model changes preserve scope, ownership, and the required review independence.

Keep changes coherent and within acceptance criteria. Preserve unrelated work and existing data. Record material decisions and findings with evidence. Escalate a critical issue immediately, stop affected unsafe steps, and continue independent authorized work. Use already-authorized containment or recovery when its conditions hold; broader action needs its own decision.

Use checks that can expose the change's concrete failure modes. Report commands, results, source revision, environment, and limitations. Distinguish static checks, tests, builds, simulations, live observations, and recovery exercises. Do not report a planned or skipped check as completed.

Follow [review rules](review-protocol.md). Reviewers are read-only toward the candidate and external systems. The implementer or authorized executor produces evidence that requires writes. Correct findings or obtain a valid scoped disposition; unresolved evidence and residual risk stay visible.

## 6. Deliver, verify, and close

Before delivery, verify the candidate, applicable review decisions, current authorization, effective ownership, and relevant evidence freshness. Map the reviewed source/artifact to what is actually merged or executed. If the candidate changes, apply the review protocol again.

If execution fails or its outcome is uncertain, pause dependent mutations and inspect actual effects before retrying. A retry can duplicate a completed action. Use the authorized recovery path where applicable, and record what recovery actually proves.

Mark done only when the selected outcome's acceptance criteria, review, authorized delivery, post-action checks, and required cleanup are complete. Split or defer remaining work only by an explicit scope decision; keep unfulfilled criteria and retained risks visible. Finish with a concise result and [handoff](session-start.md#handoff-and-closeout), release ownership, and recommend the next eligible task without automatically starting it.
