# Project configuration

This is the only place for project-specific working settings. Replace these starter values during adoption. Settings describe permitted workflows; they do not create credentials, authorization, enforcement, or evidence.

## Identity and scope

| Setting | Starter value |
| --- | --- |
| Project | Agent Delivery Playbook; replace when adopting |
| Purpose | Reusable instructions and templates for accountable project delivery |
| Stack | Markdown and GitHub issue-form YAML |
| Maintainer / decision authority | Repository owner or their explicitly designated delegate |
| Timezone | UTC for durable records; include an explicit timezone in scheduled actions |
| Allowed scope | The selected task's named files and effects |
| Excluded scope | Other repositories, external systems, and unrelated work unless selected |
| Default branch | main; verify in the adopting repository |

## Commands and evidence

| Activity | This repository | Configure for an adopting project |
| --- | --- | --- |
| Setup | No application installation required | Exact setup command and prerequisites |
| Validation | Check relative links, Markdown rendering, YAML syntax, and cross-document consistency | Exact commands, expected results, meaningful tests |
| Build | Not applicable: documentation/template repository | Build command and artifacts |
| Run | Not applicable | Development entrypoint |
| Delivery | Reviewed repository publication | Push/merge/workflow effects and release steps |
| Live verification | Not applicable to the playbook itself | Health checks, targets, freshness, and owners |

Record which checks were actually performed. If a required command or acceptance check is unspecified, resolve it before claiming success; do not invent a passing command.

## Task and coordination settings

| Setting | Default |
| --- | --- |
| Canonical task store | Markdown in tasks/items/ |
| Alternative task store | GitHub issue bodies, only after an explicit project decision and migration of authority |
| Task identifiers | T-001; optional checkpoints T-001/C1; goal G-001; finding F-001 |
| Branch convention | task/T-001-short-description |
| Selection mode | Supervised: report or brief until work is explicitly selected; no automatic queue advancement |
| Concurrency registry | Single worker: task record. Multiple workers: an acknowledged coordinator assignment or shared task issue, linked from the record |
| Handoff index | tasks/handoff.md; links and brief orientation only |
| Evidence location | Sanitized PR/issue receipts; authorized durable restricted storage for confidential evidence |

Issue intake is a request. In Markdown mode, link the accepted issue to its canonical task file and avoid maintaining a second scope/status narrative. In issue mode, use the task schema in the issue body and keep only links in repository indexes. See [task conventions](tasks/README.md).

## Review and delivery policy

- Use the [review tiers](docs/review-protocol.md); raise the tier when effects warrant it.
- Light-tier self-check fallback: **disabled** by default. If enabled deliberately, disclose it on each affected task; it never qualifies as independent review.
- Standard tier: independent technical review. High tier: independent technical review plus a distinct final verifier.
- Implementation authority: the user's or maintainer's concrete task instruction, with scope recorded. Contributors cannot authorize changes to systems they do not control.
- Repository publication/merge authority: explicit instruction or recorded maintainer delegation. Do not infer it from a review verdict.
- External actions: name action, target, environment, executor, and limits. Reuse valid authorization; request a new decision only for uncovered effects or changed conditions.
- Project-wide pause: none by default. Record an actual global pause in this section with scope, authority, date, and resumption condition. Task-only pauses belong in the task record.
- Enforcement: **not configured by these files**. Inspect and record actual repository rules, CI, access controls, and environment protections separately when relevant.

## Model selection and capabilities

Follow [the model selection guide](docs/model-selection.md). Use its capability-based defaults until this project deliberately selects concrete models. The optional [Codex](examples/model-profiles/codex.md) and [Claude / Claude Code](examples/model-profiles/claude.md) profiles are examples to adopt or adapt, not required providers.

| Setting | Starter policy |
| --- | --- |
| Selected profile | Generic role/capability guidance; no named-model profile selected |
| Role preferences | Configure coordinator, implementer, collaborators when useful, technical reviewer, and final verifier when required |
| Preference or requirement | Preferences unless a user instruction or project decision explicitly requires an exact model/capability |
| Allowed models / providers | Those already exposed and authorized in the current tool; verify task suitability and data boundaries |
| Permitted substitutes | Record acceptable alternatives when selecting a named profile; do not silently substitute for a requirement |
| Reasoning effort | Select supported labels using the guide and the task's complexity; record requested and reported values separately |
| Usage / time limits | Existing user/tool/project limits apply; define task-specific limits when needed, without assuming extra spending authority |
| Selection control | Use available runtime controls; if unavailable, record the limitation and follow the guide's fallback rules |
| Maximum-effort escalation | A concrete unresolved question after substantive investigation, expected benefit, and a bounded allowance within existing limits |

Record actual human or agent identities for independent roles. Use `unverified` when a model or effort value is not exposed; record an unsupported control separately. A role prompt does not switch models. Routine choices within an authorized profile and limits do not require repeated permission.

## Additional project context

Add links to architecture, domain rules, service ownership, restricted evidence locations, and nested instructions only when the project needs them. Keep current task history out of this file.
