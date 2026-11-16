# Example: a controlled external change

**Fictional planning example.** Names and IDs are illustrative. No environment
exists for this example, and no actions, approvals, test results, or reviewer
verdicts are claimed. This is a pattern for applying the optional checkpoint
record when a task affects a shared service.

| Field | Illustrative value |
| --- | --- |
| Task | T-202 — Rotate a service credential without interrupting requests |
| Status | `backlog` |
| Review tier | `high`, because shared access and live service behavior change |
| Owner / executor | Unassigned |
| Canonical store | One task record with linked checkpoints |

## Outcome and scope

Move one named service and its verified consumers to a replacement credential,
observe continued operation, and retire the previous credential only after the
retained access and recovery paths are established. Account-wide credential
changes and unrelated consumers are outside scope.

Before selecting implementation, establish which consumers share the
credential, whether overlap is supported, how to observe failures, and what a
successful recovery would mean. Unsupported assumptions are blockers to the
dependent step.

## Proposed checkpoints

| ID | Intended outcome | Evidence required before proceeding |
| --- | --- | --- |
| T-202/C1 | Prepare the new credential and scoped delivery path | Named target, permission, consumer inventory, exact candidate, recovery conditions |
| T-202/C2 | Switch the selected consumers | Verified delivery path, applicable reviews, scoped authorization, fresh service baseline |
| T-202/C3 | Retire the old credential and close cleanup | All required consumers verified, observation criteria met, retained recovery access, authorized retirement scope |

The table proposes work; it grants no authority. Related actions can share a
checkpoint when that produces a meaningful review and execution boundary.

## Reviews and verification

A fresh technical reviewer assesses the candidate and actual evidence. A
distinct final verifier then checks that same candidate, the technical decision,
required results, and applicable authorization before the controlled action.
Both are distinct from the implementation authors.

Checks are presently `not_run`. A real record would separate configuration
validation, credential delivery, successful and denied authentication, service
health, recovery evidence, and cleanup verification. Secret values would remain
outside public task or review records.

## Handoff and completion

The current next action is to establish the exact consumer scope and brief the
change. An interruption after a credential is created would require recording
that observed action, its consumers, current authority, and cleanup owner.
Takeover would first confirm the previous executor's state.

The task remains open until its required live checks and cleanup complete. A
merged configuration change or a technical review alone cannot establish the
intended service outcome.
