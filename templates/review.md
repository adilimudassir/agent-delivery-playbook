# Review — {{task_id}} / {{checkpoint or candidate}}

Use this as the body of a review comment or a separate evidence record. Store a
completed record **outside the commit it evaluates**. Adjust links for the
destination; in a comment, link paths to the relevant repository files. This
template grants no authority to merge, publish, deploy, or change an environment.

## Review identity

| Field | Value |
| --- | --- |
| Stage | Light review / technical review / final verification / configured self-check |
| Task and review tier | Canonical task reference and `light`, `standard`, or `high` |
| Reviewer | Person or agent / run identifier |
| Recorded at | ISO 8601 timestamp with timezone |
| Independence | Relationship to every implementation author; fresh review context |
| Requested model / effort | Chosen profile settings, or `not_applicable` for a human |
| Runtime-reported model | Actual value and metadata source, or `unverified` |
| Runtime-reported effort | Actual value and metadata source, or `unverified`; assess separately from model |
| Substitution / control limitation | Allowed alternative and reason, or `unsupported` control; do not silently replace a requirement |

A self-check must be labelled as a self-check. It meets a light-tier review
requirement only when the project explicitly allows that fallback. It does not
replace an independent technical reviewer or a distinct final verifier.

## Candidate and evidence

- Canonical task, acceptance criteria, and applicable instructions:
- Exact base and head commits, or immutable candidate artifact identifiers:
- Actual diff and relevant surrounding code or content:
- Checks executed or inspected, results, timestamps, and evidence references:
- Required evidence that is missing or stale:
- Limits of this review:

For an execution checkpoint, also identify the target environment, execution
inputs, artifact digest, relevant live observations, and required freshness
conditions. Do not publish credentials, raw private state, or sensitive logs.

## Findings

| ID / severity | Location | Effect | Required correction or disposition |
| --- | --- | --- | --- |
| None, or finding ID | Path / resource / criterion | Concrete consequence | Correction or authorized disposition reference |

Distinguish a recommendation from a failed prerequisite. Accepting residual risk
does not change an unperformed or failed check into a pass.

## Decision

- Verdict: `pass`, `changes_requested`, or `pending_evidence`.
- Reason and evidence supporting that verdict:
- Findings resolved; remaining findings and recorded dispositions:
- Candidate and checkpoint to which the decision applies:

For a high-tier final verification, also record:

- The technical decision for this candidate and any explicitly authorized
  exception; preserve failed or missing checks as such.
- Evidence that the final verifier is distinct from the technical reviewer and
  every implementation author.
- Actual required checks and their results, not only the implementer's summary.
- Whether recorded human authority covers the proposed action and target.
- Required execution, recovery, and cleanup readiness.

If the candidate, base, inputs, authorization, or material conditions change,
reassess under the [review protocol](../docs/review-protocol.md) and record the
applicable new decision. Do not carry a verdict to a different candidate by
assumption. Record the mapping from the reviewed candidate to the revision
actually merged, published, or executed.
