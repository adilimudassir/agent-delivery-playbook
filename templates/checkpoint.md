# Checkpoint {{task_id}}/C{{number}} — {{bounded external outcome}}

Use this optional record for a meaningful boundary in work affecting shared
state, environments, access, data, publication, or live services. Keep it inside
or linked from the canonical task. Unrelated local edits do not need checkpoints.

| Field | Value |
| --- | --- |
| Parent task | Canonical reference |
| Checkpoint state | Proposed / prepared / reviewed / executed / verified / blocked / paused |
| Executor | One named person or agent / run |
| Target | Environment, service, resource scope, and shared consumers |
| Updated | ISO 8601 timestamp with timezone |

Checkpoint states describe preparation and observed progress; none grants
authority. The parent task retains its own lifecycle status.

## Intended action and boundaries

- Exact action and intended result:
- Inputs and immutable candidate artifact / source identifiers:
- Expected effects, relevant cost or downtime, and exclusions:
- Dependencies and current evidence:
- Access required and its scope:
- Shared-resource ownership and coordination record:
- Automation triggered by push, merge, publish, or workflow execution:

## Before execution

- Human authorization reference covering this action and target:
- Required technical review and distinct final verification references:
- Artifact digest and exact candidate identity checked by those reviews:
- Conditions that must remain true; freshness limits and observation times:
- Expected pre-change state and how concurrent changes are excluded:
- Stop conditions and who receives an escalation:

Add domain-specific controls only when applicable, such as state locking,
migration compatibility, target identity, data retention, or rollout stages.
Read-only descriptions do not make an operation read-only if it writes locks,
creates sessions, changes external state, or triggers automation.

## Recovery and cleanup

- Recovery steps, their limits, and how they were established:
- Conditions under which recovery is already authorized:
- Recovery actions requiring additional authority:
- Cleanup owner, trigger or deadline, and verification of completion:

## Execution and verification

- Start / finish times and actual executor:
- Final preflight result and evidence:
- Actual executed artifact, target, and result:
- Post-change acceptance checks and results:
- Evidence for service, data, or user-visible behavior as applicable:
- Remaining cleanup, risks, or failed / unperformed checks:

After a failed, interrupted, or uncertain action, reconcile the actual outcome
before retrying or handing over. Preserve evidence, stop dependent mutations,
and use the authorized recovery path when its conditions hold. A configuration
revert alone does not prove recovery of data or service.
