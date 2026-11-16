# Model selection guide

Use this guide to choose the capability and reasoning depth for each role in a task. It applies across providers and tools. Configure concrete preferences, permitted substitutes, and limits in [PROJECT.md](../PROJECT.md).

## Choose a tool profile

| Profile | Includes |
| --- | --- |
| [Codex](../examples/model-profiles/codex.md) | Sol / Astra role defaults, a Luna option for routine work, CLI model and effort controls, custom reviewer example, and AGENTS.md loading |
| [Claude / Claude Code](../examples/model-profiles/claude.md) | Haiku / Sonnet / Opus role defaults, model and effort controls, custom reviewer example, and the CLAUDE.md import |
| Generic capability guidance below | Any supported provider, local model, hosted agent, or human reviewer |

These profiles are optional, dated examples. Selecting one in PROJECT.md records policy; apply its settings through supported runtime controls. Neither copying the playbook nor naming a role activates model routing. Projects can mix providers for different roles only within their authorized access, data, and usage limits.

## Choose for the work

1. Identify the role, outcome, uncertainty, failure impact, and acceptance checks. The task's review tier determines which independent roles are required.
2. Confirm that the proposed worker has the needed tools, access, context capacity, and domain capability. Resolve missing evidence or unclear requirements before assuming a larger model will help.
3. Select a suitable model within the project's allowed profile and budget, then choose reasoning effort separately. Start with the lightest configuration demonstrated to meet the quality bar for comparable work.
4. Record the requested settings and what the runtime actually reports. Reassess at a meaningful checkpoint when the task becomes harder, easier, or blocked.

The capability descriptions below are roles in a project policy, not a universal ranking of model brands. A human with the relevant expertise can fill any role; model and effort fields are then `not_applicable`.

## Role and capability matrix

| Role or activity | Capability to select | Starting effort, when available | Raise capability or depth when |
| --- | --- | --- | --- |
| Routine inventory or editorial work | Efficient model with dependable extraction, instruction following, and required tools | Low or medium | Material ambiguity, domain interpretation, or changed rules emerge |
| Coordinator / task planner | General reasoning model that can assess scope, priorities, and dependencies | Medium; high for substantive planning | Requirements conflict, sequencing crosses systems, or several owners share resources |
| Implementer | Strong coding or domain model with reliable tool use | Medium for a routine bounded change; high for substantive work | The change crosses boundaries, has sensitive effects, or requires unfamiliar design decisions |
| Bounded collaborator | A model matched to one clearly defined subtask and its checks | Low or medium for mechanical work; higher for substantive analysis | The subtask develops independent design uncertainty; implementation contributors remain authors |
| Independent technical reviewer | Strong domain reasoning and adversarial analysis; advanced capability for high-impact or unfamiliar changes | High for substantive review | Important interactions, data/access effects, or unresolved correctness questions exceed the reviewer's capability |
| Distinct final verifier | Strong evidence checking and enough domain understanding to assess the final candidate | High for high-tier work | Authorization, candidate identity, recovery, or acceptance evidence requires deeper technical judgment |
| Difficult investigation / architecture | Advanced reasoning suitable for ambiguous, interacting problems | High | A concrete unresolved question remains after substantive investigation and deeper reasoning has a plausible benefit |

Assign only the roles the task needs. Listing a collaborator does not require spawning one. The coordinator may also implement; independent reviewers follow the separation rules in [the review protocol](review-protocol.md). The final verifier must understand the candidate, not merely count completed fields.

## Model and reasoning effort are separate choices

Use the labels actually supported by the chosen product and model. Labels such as `low`, `medium`, `high`, `xhigh`, and `max` are not standardized capability scores across providers or model families.

| Effort band | Useful starting point |
| --- | --- |
| Low | Extraction, simple edits, or mechanical work with clear checks |
| Medium | Bounded problem-solving and routine implementation |
| High | Substantive implementation, planning, technical review, and final verification |
| Extra high / xhigh | Interacting constraints or difficult diagnosis when a lower setting has not resolved the specific problem |
| Maximum / max | Exceptional unresolved work with a stated question, expected benefit, and bounded usage/time allowance |

These are starting recommendations. Evaluate the actual result; a higher setting does not establish correctness. A stronger model at a moderate setting may be a better choice than increasing a less suitable model's effort. Missing files, permissions, requirements, or observations need to be obtained or resolved directly.

## Escalate with evidence

Escalate when a material issue remains: conflicting requirements, uncertain destructive effects, interacting architectural decisions, repeated substantive failures despite a corrected approach, or a review finding the current worker cannot resolve.

Before changing configuration, record the unresolved question, relevant files/evidence, attempted approaches and results, proposed setting, and stop condition. Carry forward the current candidate and findings; do not restart all completed work. Increase effort or model capability for a reason, and stop equivalent retries that add no evidence. Use maximum effort only when the remaining problem warrants it and the configured limits cover it.

Once a difficult design or diagnosis is settled, a suitable general or efficient model can handle bounded implementation, inventory, or editorial follow-up. Retain the acceptance criteria, ownership, and independent review requirements. Model changes do not lower the task's review tier.

## Apply the choice in the actual runtime

This document does not switch models. Use supported model-picker, launch, delegation, or API controls only when the current runtime exposes them. Do not invent a command or imply that a prompt changed an underlying model.

Distinguish a **preference** from a **requirement**:

- For a preference, use an allowed, sufficiently capable substitute when needed and disclose it. Selection within an already authorized profile, data boundary, and budget does not need repeated permission.
- For an exact required model or capability, do not silently substitute. If it is unavailable, record the blocked role and prepare a handoff or request the precise missing decision. Continue independent authorized preparation.
- If selection controls are unavailable, record the requested configuration separately from the current observable runtime. Continue only when that worker meets the task's requirements; otherwise hand the role to a suitable available worker.
- A new provider, data-sharing boundary, paid service, budget increase, or broader task is a separate scope decision. A model preference supplies none of those permissions.

Record model and effort separately: one may be visible while the other is not. Use `unverified` for an actual value the runtime does not expose; record `unsupported` for a control the runtime cannot set. If a provider chooses automatically and does not reveal the resolved model, retain `unverified` rather than inferring a brand from writing style. Optional speed or execution-mode settings are separate from reasoning effort and must also be supported and within limits.

## Preserve independence and handoff

A different model in the author's conversation does not create an independent reviewer. Separate fresh runs can use the same model. A high-tier final verifier remains distinct from the technical reviewer and every implementation author. Give reviewers neutral requirements, the actual candidate, and evidence without a suggested verdict or the implementation conversation.

Use the role table in [the task template](../templates/task.md). Record role, capability, preference/requirement, owner or run, requested model/effort, reported model/effort, metadata source, and any substitution. For a small task, a short equivalent note is sufficient. Keep the next role's capability needs and unresolved runtime limitations in [the handoff](../templates/handoff.md); link the routing record instead of repeating its history.

Periodically compare configurations on representative tasks using the same inputs and acceptance criteria. Consider success, defects, review/rework time, elapsed time, and usage per accepted outcome. Record the date and evidence when changing a project profile. A provider update or a new model name is a reason to reassess suitability, not automatic permission to change the project's selected profile.
