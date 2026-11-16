# Model profile: Claude / Claude Code

**Guidance checked: 2026-11-16.** This is a proposed project policy for Claude Code, with a separate note for Claude chat. Adopt or adapt it in [PROJECT.md](../../PROJECT.md); including this example does not select it or change the current runtime. The [generic selection guide](../../docs/model-selection.md) governs capability, substitutes, limits, and honest reporting.

## Proposed role assignments

These assignments are this playbook's starting recommendations, not provider requirements. Treat them as preferences unless the project explicitly makes a setting mandatory. Use only the roles required by the task and its [review tier](../../docs/review-protocol.md).

| Role or activity | Preferred Claude Code model | Starting effort | When to reconsider |
| --- | --- | --- | --- |
| Coordinator / task planner | `sonnet` | `medium` | Use `opus` with `high` for ambiguous scope, architecture, or interacting dependencies |
| Implementer | `sonnet` | `medium` | Raise to `high` for substantive debugging; use `opus` when the remaining problem needs stronger reasoning |
| Bounded implementation collaborator | `sonnet` | `medium` or `high` to match the subtask | Reassess when the subtask develops design uncertainty; the collaborator remains an implementation author |
| Routine inventory or mechanical edits | `haiku` | `low`, when supported; otherwise the model's supported default | Use `sonnet` when interpretation or correctness demands more judgment |
| Independent technical reviewer | `opus` in a separate fresh run | `high` | Consider `xhigh` for a concrete unresolved interaction or consequential risk |
| Distinct final verifier | `sonnet` in another fresh run | `high` | Use `opus` when acceptance evidence or candidate effects require deeper technical judgment |
| Difficult investigation / architecture | `opus` | `high` | Consider `xhigh` after substantive investigation; use `max` only for a bounded unresolved question within existing limits |

A suitable human may fill any role. A routine helper is not a substitute for a required reviewer. The final verifier must be distinct from the technical reviewer and every implementation author. Record an allowed substitution and its reason; keep an unavailable mandatory role pending rather than silently downgrading it.

## Identifiers and availability

As checked on the date above, the official Claude Code model list includes these full IDs:

| Family | Full model ID |
| --- | --- |
| Sonnet 5.5 | `claude-sonnet-5-5` |
| Opus 5.5 | `claude-opus-5-5` |
| Haiku 5.5 | `claude-haiku-5-5` |

Source: [Claude Code model configuration](https://support.claude.com/en/articles/11940350-claude-code-model-configuration).

The `sonnet`, `opus`, and `haiku` aliases currently select these versions on the Anthropic API. Other providers and older Code versions can resolve differently; aliases change over time. Use a full ID when the project requires a particular version. Source: [model aliases](https://code.claude.com/docs/en/model-config#model-aliases).

Check `/model` for the choices available to the current account. Organization settings and sign-in method affect defaults and availability. Source: [models, usage, and limits](https://support.claude.com/en/articles/14552983-models-usage-and-limits-in-claude-code).

Record the requested alias or ID separately from the runtime-reported model. Use `unverified` if the resolved model is not exposed. Availability does not establish permission to move project data to a different provider or increase spending.

## Apply settings in Claude Code

Example terminal launches for an adopted profile:

```bash
claude --model sonnet --effort medium
claude --model opus --effort high
```

Within a running Claude Code session, the following are interactive commands, not shell commands:

```text
/model
/effort high
/effort status
/status
```

`/model` opens the model picker; `/status` reports the current model. Launch flags apply to terminal sessions. Source: [Claude Code model configuration](https://support.claude.com/en/articles/11940350-claude-code-model-configuration).

Current 5.5 models support `low`, `medium`, `high`, `xhigh`, and `max`; Claude Code defaults them to `medium`. Support and defaults vary by model. `CLAUDE_CODE_EFFORT_LEVEL` overrides session effort choices. Unsupported levels can resolve downward, and organization caps apply. `--effort` sets session effort; `/effort status` reports it. Interactive model/effort choices normally persist; press `s` in the picker for session-only changes. `max` normally lasts only for the session and is not accepted in persisted `effortLevel` or `modelSettings`. Sources: [setting your model](https://code.claude.com/docs/en/model-config#setting-your-model), [effort controls](https://code.claude.com/docs/en/model-config#adjust-effort-level).

Before assigning work, compare requested settings with the observable result. Record unsupported controls, actual substitutions, and limits. Do not describe a model or effort as verified merely because a prompt requested it. The commands above have been checked against documentation; this repository does not execute them during adoption.

## Optional reviewer definition

For a project that chooses Claude Code subagents, the following is an example file to add deliberately at `.claude/agents/delivery-reviewer.md`. This playbook does not install an executable agent configuration.

```markdown
---
name: delivery-reviewer
description: Independently reviews a specified delivery candidate and reports findings.
tools: Read, Grep, Glob
model: opus
effort: high
---

Review the supplied task, acceptance criteria, base and candidate revisions,
complete diff, relevant context, and validation evidence. Follow AGENTS.md,
PROJECT.md, and docs/review-protocol.md. Obtain missing context before deciding.
Report findings with evidence and return pass, changes_requested, or
pending_evidence. State checks you could not perform. Do not edit the candidate.
```

Custom agent files support a model alias, full ID, or `inherit`, plus supported `effort` values. Invocation choices and environment settings can override the definition; forced subagent model settings can also change selection. `/tasks` shows a running subagent's model and effort. Ordinary subagents start with fresh context plus delegation and applicable instructions; forks inherit the parent conversation. Worktree isolation defaults to the default branch rather than the parent's `HEAD`. Source: [custom subagents](https://code.claude.com/docs/en/sub-agents#choose-a-model), [context](https://code.claude.com/docs/en/sub-agents#manage-subagent-context), [frontmatter](https://code.claude.com/docs/en/sub-agents#frontmatter-reference).

The sample's `Read`, `Grep`, and `Glob` tools permit inspection, not test execution, Git commands, or edits. Supply the complete diff and revision evidence as readable artifacts, or use an authorized executor to produce missing evidence. A passing inspection cannot stand in for an unperformed required test. Add tool access only through a deliberate project decision consistent with the review protocol.

### Check the review assignment

Give each reviewer a neutral packet containing the task, applicable rules, acceptance criteria, full base/head identifiers, complete diff, material context, and actual validation results. Confirm that its files match the named candidate, especially if a separate worktree is used. Ask it to identify missing evidence before issuing a verdict.

Use a new ordinary subagent or a fresh session that did not author the candidate. Do not forward the implementation conversation as the review packet or use a fork as the independent reviewer. Record each run's identity, requested and reported settings, and evidence source in the [task routing record](../../templates/task.md). Launch the distinct final verifier after technical review and required dispositions. A model switch, fresh label, or stronger setting alone does not satisfy independence.

## Share repository instructions

Current Claude Code can read `AGENTS.md` automatically when project/ancestor `CLAUDE.md` or `CLAUDE.local.md` files do not take precedence. This requires v2.1.277 or later and can depend on settings/plugin availability. A root `CLAUDE.md` containing `@AGENTS.md` is an explicitly supported bridge for other cases; the import does not duplicate an already loaded file. Check `/context all` for loaded instructions. Source: [AGENTS.md support and shared instructions](https://code.claude.com/docs/en/memory#share-one-file-with-other-coding-tools).

Keep operating rules in `AGENTS.md` and the bridge thin. When adopting into a project that already has `CLAUDE.md`, merge the actual import into that file without overwriting the adopter's instructions. Reconcile any conflict. Add local Claude guidance only where the tool needs it; select a model profile through `PROJECT.md`.

## Claude chat

Claude chat uses the model menu beside the send button to select the model and effort; changes apply to the next response. Choices may be restricted by the organization. Source: [chat model and effort settings](https://support.claude.com/en/articles/8664678-change-the-model-effort-and-thinking-settings).

Apply the same role and evidence policy, using controls actually exposed in that surface. Provide the relevant instructions and candidate evidence explicitly; do not assume the Code commands or repository-loading behavior apply to chat.
