# Decision {{decision_id}} — {{subject}}

Use for a material design choice, authorization, exception, or risk disposition.
Keep it in the canonical task or an explicitly linked decision record. Do not
create a new file for every routine implementation choice.

| Field | Value |
| --- | --- |
| State | Proposed / accepted / superseded / expired |
| Kind | Design choice / authorization / deferral / exception |
| Task or checkpoint | Canonical reference |
| Decision owner | Person with authority for this decision |
| Recorded at | ISO 8601 timestamp with timezone |
| Original instruction or decision | Durable reference, or exact recorded instruction |

## Context and choice

- Problem, evidence, and constraints:
- Options considered and relevant trade-offs:
- Chosen option and reason, or the exact unresolved question:

## Scope and consequences

- Actions, targets, environment, and duration covered, if this authorizes work:
- Exclusions and separate decisions still required:
- Known residual risks and any check that remains failed or unperformed:
- Owner and trigger for reconsideration, expiry, or follow-up:
- Supersedes / is superseded by, if applicable:

An accepted design choice is not automatically execution permission. An agent
quality verdict is not human authorization. Carry valid permission and deferrals
forward without repeatedly asking; revisit them when their stated conditions or
the material facts change.
