# {{task_id}} — {{concrete outcome}}

Copy this record to `tasks/items/` or to the configured issue body. Keep only one
authoritative copy, as selected in [PROJECT.md](../PROJECT.md). Replace all
placeholders, adjust links for the destination, and remove optional sections
that do not apply. In an issue body, link paths to the relevant repository files.

| Field | Value |
| --- | --- |
| Status | `backlog` |
| Responsible owner | Unassigned |
| Review tier | `light`, `standard`, or `high`; include the reason |
| Updated | ISO 8601 timestamp with timezone |
| Canonical record | Repository path or issue URL |
| Goal / parent task | Goal and optional parent ID |
| Working branch / PR | Reference, or not created |

Allowed statuses: `backlog`, `ready`, `in_progress`, `in_review`, `blocked`,
`paused`, `done`, `cancelled`. `ready` means eligible to start; it does not grant
permission. Apply the [operating method](../docs/operating-method.md).

## Outcome and scope

**Problem:** What is wrong or needed, and who is affected?

**Intended outcome:** One observable result.

**Included:** The smallest bounded set of changes needed for that result.

**Excluded:** Nearby work that is useful but outside this task.

## Acceptance criteria

- [ ] Observable criterion, with a check that can establish it.
- [ ] Required documentation, recovery, or cleanup criterion, when applicable.

## Readiness and dependencies

| Dependency or constraint | Current evidence | Effect on this task |
| --- | --- | --- |
| Dependency ID, prerequisite, or none | Reference and observation time | Required before a named step, or advisory |

Record relevant findings and valid dispositions by reference. Explain any new
condition that makes an earlier decision need reconsideration.

## Authorization

- Authorizing person or configured standing policy:
- Exact instruction or durable reference, and date:
- Covered actions, targets, environment, and limits:
- Current pause or stop condition, if any:
- Later actions that need a separate decision:

An issue request, task status, reviewer verdict, or this template is not an
authorization. Preserve valid permission within its recorded scope.

## Work claim

- Implementer and session / run identifier:
- Allowed paths; paths owned by other work:
- Shared resources and sole executor, if applicable:
- Coordination record and acknowledged owner:
- Claimed at; last confirmed at; release or transfer condition:

One writer owns each overlapping path; one executor owns each shared mutation
scope. A local record alone does not reserve remote resources or exclude another
session. Confirm the previous executor's state before takeover.

## Plan

### Role and model plan

Use only the roles this task needs, following [model selection](../docs/model-selection.md).
For a small task, a concise note can replace this table. Humans use `not_applicable`.

| Role / owner or run | Capability; preference or requirement | Requested model / effort | Reported model / effort; metadata source | Substitution or limitation |
| --- | --- | --- | --- | --- |
| Implementer; assign required reviewers separately | Task-appropriate capability | Record the selected configuration | `unverified` until exposed; assess each value separately | None recorded |

Record the reason and bounded scope for escalation. A role prompt is not a model
switch, and a model change does not establish review independence.

### Work steps

1. Prepare the bounded change and establish the relevant baseline.
2. Implement and run the acceptance checks.
3. Obtain the applicable review decision, complete authorized delivery, and
   verify the intended outcome.

## Verification and evidence

| Check | Result | Environment / revision | Evidence and observation time |
| --- | --- | --- | --- |
| Acceptance check | `not_run` | To be recorded | To be recorded |

Use `passed`, `failed`, `not_run`, `waived`, or `not_applicable` with a reason. Record the
actual command or procedure and limitations. A deferred or unavailable check
does not pass. Link review records that identify the exact candidate; do not
try to put a commit's own final hash inside that commit.

## Decisions and findings

- Applicable decisions / deferrals:
- Findings discovered, severity, impact, and follow-up owner:
- Review record references and unresolved items:

## Current handoff

- Last verified achievement and evidence:
- Remaining work or exact blocker:
- Next concrete action and next owner:
- Authorization that remains valid; actions still awaiting a decision:
- Workspace, branch, uncommitted changes, and active processes to preserve:
- Claim retained, transferred, or released:
- Next role's capability/model requirement; routing record and unresolved runtime limitations:

Update this section on pause, interruption, transfer, and completion. Put a
pointer in `tasks/handoff.md`; keep the detailed state here.

## Optional operational checkpoints

Include only when actions affect shared state, environments, access, data,
published artifacts, or live services. Link one
[checkpoint record](checkpoint.md) per meaningful execution boundary, with a
unique child ID such as `{{task_id}}/C1`. Define recovery, verification, and
cleanup before execution. Keep sensitive evidence in an approved private
location and link only a sanitized reference.
