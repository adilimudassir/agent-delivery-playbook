# Model profile: Codex

**Optional project profile.** These are the playbook's proposed role defaults, not OpenAI requirements or an automatic router. Select or adapt this profile in [PROJECT.md](../../PROJECT.md). The [general guide](../../docs/model-selection.md) governs capability, escalation, limits, and truthful runtime records.

Documentation checked: **2026-11-16**. Recheck the actual client and account before adopting a model or control. Examples below target current Codex CLI/local configuration; hosted products can expose different controls.

## Suggested role mapping

| Role / work | Preferred model | Requested reasoning effort | Escalation or qualification |
| --- | --- | --- | --- |
| Coordinator / task planning | GPT-6.1 Sol (`gpt-6.1-sol`) | `high` | Consider Astra when scope or architectural decisions remain difficult |
| Routine inventory / editorial work | GPT-6.1 Sol | `medium` | An explicitly permitted GPT-6 Luna (`gpt-6-luna`) at `high` is an option for clear, mechanical work |
| Implementation | GPT-6.1 Sol | `high` | Consider `xhigh` for difficult interactions; use Astra when the unresolved problem warrants stronger analysis |
| Bounded implementation collaborator | GPT-6.1 Sol | `medium` or `high` | Match the subtask; count the collaborator as an implementation author |
| Independent technical reviewer | GPT-6 Astra (`gpt-6-astra`) | `high` | Use a separate fresh run and the complete review packet |
| Distinct final verifier | GPT-6.1 Sol | `high` | Use another fresh run; prefer Astra if the acceptance decision needs deeper technical judgment |
| Difficult investigation / architecture | GPT-6 Astra | `high` | Consider `xhigh`, then `max` only for a concrete unresolved question after substantive investigation |

The role mapping is deliberately conservative for substantive delivery and review. Calibrate it on representative project tasks, including repair and review costs. Exact model requirements, permitted substitutes, and usage limits belong in PROJECT.md. An unavailable preferred reviewer does not permit a silent downgrade or removal of independent review.

The [official model catalog](https://learn.chatgpt.com/docs/models) documents the named models and account-dependent availability. The [Sol](https://developers.openai.com/api/docs/models/gpt-6.1-sol) and [Astra](https://developers.openai.com/api/docs/models/gpt-6-astra) API references describe their API reasoning controls; an API option does not establish support in every Codex surface.

## Select and verify the session settings

In the Codex CLI, `/model` opens the available model picker. Current clients also support a direct session choice:

```text
/model gpt-6.1-sol --reasoning=high
/status
```

The picker is account/workspace-specific. Check its confirmation and `/status`; record effort separately if the runtime does not expose it there. See [the official CLI command reference](https://learn.chatgpt.com/docs/developer-commands?surface=cli).

For reusable local defaults, merge these keys into the appropriate Codex configuration rather than overwriting an existing file:

```toml
# Example .codex/config.toml in an adopting project
model = "gpt-6.1-sol"
model_reasoning_effort = "high"
```

User defaults live in `~/.codex/config.toml`; trusted projects can supply `.codex/config.toml`. Other configuration layers can take precedence. Available effort values depend on the selected model and client. See [configuration basics](https://learn.chatgpt.com/docs/config-file/config-basic) and [the configuration reference](https://learn.chatgpt.com/docs/config-file/config-reference).

Use `xhigh` or `max` only under the escalation policy. This profile does not require Ultra or a particular orchestration mode. A more intensive setting does not satisfy a review gate by itself.

## Optional reviewer agent

Current local Codex clients support project agents in `.codex/agents/*.toml`. For example, an adopter can create `.codex/agents/delivery-reviewer.toml`:

```toml
name = "delivery_reviewer"
description = "Independently assess a named delivery candidate."
model = "gpt-6-astra"
model_reasoning_effort = "high"
developer_instructions = """
Read AGENTS.md, PROJECT.md, and the review protocol.
Require the task, acceptance criteria, base/head revisions, and evidence.
Inspect the actual candidate and relevant context without editing it.
Report findings, unperformed checks, and a verdict tied to that candidate.
Do not treat the author's suggested conclusion as review evidence.
"""
```

This file selects model settings when that custom agent is invoked; merely writing a role name in a prompt does not prove a switch. Custom agents inherit the parent's permission and tool environment. These instructions are not a technical read-only boundary. See [the official subagent guide](https://learn.chatgpt.com/docs/agent-configuration/subagents).

Supply a neutral review packet in a fresh run. A fork carrying the implementation conversation does not meet this playbook's fresh-context review rule. Verify the actual checkout/commit rather than assuming a new thread or worktree contains the candidate. High-tier work still needs a distinct final verifier after technical review. If the host cannot provide a suitable fresh run, use a separate session or human reviewer.

## Load the repository instructions

Codex discovers `AGENTS.md` guidance from the project root toward the working directory; `AGENTS.override.md` and higher-level instructions can affect the resulting chain. Start in the intended repository, check applicable nested guidance, and confirm the loaded instructions. See [instruction discovery](https://learn.chatgpt.com/docs/agent-configuration/agents-md).

The repository's [AGENTS.md](../../AGENTS.md) points to PROJECT.md, current task records, commencement, review, and model selection. Record requested and runtime-reported model/effort in the task and review receipts. Use `unverified` for unexposed actual values, and preserve unresolved selection limitations in the handoff.
