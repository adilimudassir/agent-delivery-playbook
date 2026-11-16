# Adopt the playbook

## New repository

Use the GitHub **Use this template** action, choose the desired owner and visibility, and create your project. Customize PROJECT.md, replace the project introduction in README.md, and retain the reusable method. Start with an empty task index and a single bounded task. The examples are fictional references, not active work or permission.

## Existing repository

1. Read the existing AGENTS.md, CLAUDE.md when present, contributor rules, task tracker, and delivery automation. Preserve any active work and authorization.
2. Add the playbook on an isolated branch. Merge relevant rules into the existing AGENTS.md and PROJECT.md; do not overwrite established instructions wholesale. For Claude Code, merge the `@AGENTS.md` import from [CLAUDE.md](../CLAUDE.md) into the existing entrypoint or use the supplied thin entrypoint.
3. Copy docs, templates, and task conventions into non-conflicting paths. Adjust relative links if the layout changes. Keep the existing project README and link to the method.
4. Choose one canonical task store. Link or migrate existing tasks, retain historical IDs as aliases, and define unique IDs for independently executable checkpoints.
5. Replace long current-progress narratives with short pointers to canonical task handoffs. Archive old records without reinterpreting historical approvals as current permission. Preserve important historical links.
6. Review the actual delivery effects and configure appropriate review tiers. Set role capabilities, model preferences or requirements, permitted substitutes, and limits using [model selection](model-selection.md). Policy changes themselves use high-tier review under the existing applicable rules.
7. Run one real task through selection, implementation, review, and handoff. Adjust fields that do not help the project while preserving clear authority and honest evidence.

Adopt the smallest useful subset. Every project needs an entrypoint, local settings, a bounded task record, and a restartable handoff. Cross-task findings, decision records, and operational checkpoints become useful as complexity grows.

## Codex and Claude setup

Use the [Codex profile](../examples/model-profiles/codex.md) or [Claude / Claude Code profile](../examples/model-profiles/claude.md) for concrete role defaults and supported configuration examples. Record your selected profile, allowed substitutes, and limits in PROJECT.md, then apply the settings in the actual tool. Keep shared working rules in AGENTS.md and project facts in PROJECT.md. Confirm the instruction files and model/effort settings loaded before starting work; the task record must distinguish requested values from reported ones.

## GitHub placement

| Location | Purpose |
| --- | --- |
| A dedicated public template repository | Distributes the reusable file structure and method. |
| A profile README | Introduces the method and links to its repository. It does not install project instructions. |
| A public account-level .github repository | Can provide GitHub's supported default community health files, such as contribution guidance and issue/PR templates. |
| Each adopting repository | Contains its actual AGENTS.md, project settings, task records, and required workflow configuration. |

GitHub's default-community-file mechanism does not distribute arbitrary AGENTS.md or workflow files into repository clones. Agent instruction discovery is tool-specific; confirm that the selected tool reads the installed instructions. For tools without automatic support, explicitly supply the relevant files in the task context.

Template use copies files; it is not an automatic update subscription. Record the adopted playbook version or upstream commit when useful, and review later upgrades before changing local policy. Do not replace an existing project's license merely because you copied this playbook. Retain this playbook's license notice as required for copied material.

## Public reuse

Publish reusable rules and synthetic examples. Keep live resource inventories, personal contact details, credentials, private incident history, and sensitive execution evidence in their proper project locations. Create a clean template history; a renamed copy of a private operational repository can retain its old contents and metadata.

## References

- [GitHub: creating a template repository](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-template-repository)
- [GitHub: creating a repository from a template](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-repository-from-a-template)
- [GitHub: default community health files](https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/creating-a-default-community-health-file)
- [GitHub: managing a profile README](https://docs.github.com/en/account-and-profile/setting-up-and-managing-your-github-profile/customizing-your-profile/managing-your-profile-readme)
- [AGENTS.md format and conventions](https://agents.md/)
