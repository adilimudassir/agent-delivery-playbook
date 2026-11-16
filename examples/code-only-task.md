# Example: a code-only bug fix

**Fictional planning example.** Names and IDs are illustrative. No work is
authorized, implemented, reviewed, or tested by this file. The example shows a
compact record, not a live task to add to a project's queue.

| Field | Illustrative value |
| --- | --- |
| Task | T-101 — Keep a zero quantity in an item total |
| Status | `backlog` |
| Review tier | `standard`, because runtime behavior changes |
| Owner | Unassigned |
| Canonical store | One Markdown task record |

## Outcome and scope

An item-total helper incorrectly replaces an explicit quantity of zero with its
default quantity. Preserve zero while continuing to default an omitted quantity.
Change only that helper, its direct callers if required, and focused tests. Tax,
currency rounding, and UI redesign are outside this task.

## Acceptance

- Explicit zero quantity produces a zero item total.
- Omitted quantity keeps the documented default behavior.
- Positive quantity and invalid-input behavior remain covered by relevant checks.

## Readiness, permission, and claim

Inspect the actual helper and caller contract before selecting implementation.
There is no recorded authorization or claim. For real work, record the user's
bounded implementation request and allocate the helper and test paths to one
writer. Confirm whether a push or merge triggers any external action before
including it in the delivery scope.

## Planned work and evidence

1. Reproduce the zero-quantity failure with a focused check.
2. Correct default handling and run the relevant regression checks.
3. Obtain an independent technical review of the final candidate.

All checks are `not_run`; no reviewer has issued a verdict. The completed record
would link actual check output and a review identifying the exact base and head.
A separate final verifier is not required by the standard tier unless the
project's configuration adds that requirement.

## Handoff

The next action is to inspect the bounded bug and establish readiness. A real
task would record its current branch, findings, permission, and next owner.
Code-only acceptance can finish after the authorized repository delivery and
required verification. A later production rollout is a separate task or an
explicitly included checkpoint; it is not implied by a code merge.
