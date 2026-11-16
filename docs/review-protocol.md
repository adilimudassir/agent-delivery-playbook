# Review and evidence

Review establishes quality against a specified candidate and outcome. Permission establishes who may perform which action. Neither is a substitute for the other.

## Proportionate review

| Tier | Classification | Required review |
| --- | --- | --- |
| Light | Wording, formatting, or presentation; no changed requirements, commands, permissions, behavior, or decision rules | One fresh reader. A declared self-check fallback is allowed only if PROJECT.md explicitly enables it. |
| Standard | Ordinary behavior changes, APIs, dependencies, nontrivial refactors, or analytical logic | One independent technical reviewer and meaningful validation. |
| High | Access/security boundaries, sensitive data, irreversible operations, shared runtime/state, release machinery, or operating/review policy | Independent technical reviewer followed by a distinct final verifier, plus applicable execution evidence. |

Classify by effects, not file extension. A permission change in Markdown is high tier; a typo in a deployment guide may be light if it changes no command or meaning. Projects may require stricter controls. Record the tier and reasoning in the task.

## Roles and independence

- **Coordinator:** selects or recommends within the user's scope, manages claims and dependencies, and keeps handoff pointers current. Can also implement.
- **Implementer:** prepares the change, evidence, and fixes. May delegate non-overlapping implementation; every contributor remains an implementation author.
- **Technical reviewer:** a human or separate agent run that did not author the candidate. Independently examines requirements, complete diff, surrounding code, and evidence.
- **Final verifier:** for high tier, a different human or agent run from the technical reviewer and every implementation author. Confirms the final candidate, review dispositions, applicable authority, checks, and delivery readiness.
- **Decision authority / executor:** the person authorized to decide, and the actor authorized to execute. An agent review verdict does not create either authority.

A new label, role prompt, or model name in one conversation is not a new independent review. An agent review should start with a fresh context packet rather than the implementation conversation. Give neutral requirements and evidence, without a suggested verdict. Different independent runs may use the same model. Record actual run/person identity and any unavailable controls.

Select capable reviewers using [the model selection guide](model-selection.md) and the project's chosen profile. Record requested and reported model/effort separately. More reasoning or a stronger model does not replace the required independent run or human reviewer.

If an independent role is unavailable, say so and retain the candidate as pending review. Continue useful authorized preparation. Do not claim a pass or lower the tier to bypass the gap. An explicit maintainer exception must state scope, reason, residual risk, and what remains unverified; it cannot override platform or host access restrictions.

## Review packet

Provide the task and acceptance criteria, applicable instructions, canonical scope, base and head revisions, complete diff and relevant context, validation commands/results, material decisions, and relevant findings. For external execution also include target/environment, exact artifact/digest, inputs, freshness constraints, effective executor, authorization, stop conditions, and recovery.

The reviewer is read-only toward the candidate and external systems. Local non-mutating inspection is allowed. Checks requiring writes, locks, sessions, or runtime effects belong to an authorized executor; reviewers assess the resulting evidence.

## Findings and verdicts

Record severity, location, impact, evidence, and a concrete correction. Use P0 for an immediate critical issue, P1 for serious impact requiring a decision before affected delivery, P2 for an ordinary issue, and P3 for a minor improvement. Severity guides priority; the acceptance criteria determine whether a check is a prerequisite.

Valid verdicts are `pass`, `changes_requested`, and `pending_evidence`. Link resolved findings and accepted dispositions. Required failed or missing evidence cannot be described as passed. A permitted exception is recorded separately as a qualified delivery decision, with the unsatisfied check still visible.

After fixes, reassess the actual final candidate. For high tier, the final verifier acts only after a technical pass or a specifically authorized, documented exception. Reviewers must not invent that exception or approve their own authored corrections.

## Exact candidate and fresh evidence

Use [the review template](../templates/review.md). Bind each verdict to full base/head revisions, relevant artifact digests, target, evidence references, and time. Store the receipt outside the commit being assessed: a PR review/body receipt, task issue, or authorized durable evidence store. A temporary local file is not durable cross-machine evidence; disclose that limitation until it is retained accessibly.

Any changed head, integration base, relevant artifact, input, target, or expired observation requires reevaluation. A reviewer may focus on the delta, interactions, and affected checks, but the new decision must cover and identify the complete new candidate. Unchanged action counts or filenames are not proof of an unchanged change.

Immediately before merge or execution, recheck candidate identity and applicable decisions. For merge/squash/rebase, record how the reviewed content maps to the resulting revision. Content or integration changes require reassessment. High-impact execution additionally requires the reviewed artifact and fresh state/live conditions described in [operational changes](operational-changes.md).

## Evidence honesty and enforcement

Record actual results and limitations. Static validation, a build, a simulation, an application check, and a recovery drill prove different things. Use `not_run`, `failed`, `passed`, `waived`, or `not_applicable` with a reason. Report requested model settings separately from runtime-observed settings; do not claim unsupported model switching.

These files are process guidance. They do not install branch rules, CI checks, reviewer permissions, environment gates, or cloud access boundaries. Inspect actual enforcement when it matters. A shared GitHub identity can record separate agent runs, but it does not become multiple GitHub reviewers or satisfy a rule requiring different accounts.
