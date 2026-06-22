<p align="center"><img src="assets/powerup.svg" alt="Power-up" width="120"></p>

# A 1-Up for your coding agents.

Reusable skills and a curated Claude Code setup for building agent tooling with practical conventions.

## Claude Code setup

[`.claude/settings.json`](.claude/settings.json) enables a curated bundle of official Claude Code plugins for authoring and maintaining agent tooling — skills, plugins, `CLAUDE.md` files, and project config. Claude Code reads it automatically when you start an agent from the repo root.

| Plugin | Does |
| --- | --- |
| [claude-code-setup](https://github.com/anthropics/claude-plugins-official/tree/main/plugins/claude-code-setup) | Analyze a codebase and recommend tailored Claude Code automations — hooks, skills, MCP servers, and subagents. |
| [claude-md-management](https://github.com/anthropics/claude-plugins-official/tree/main/plugins/claude-md-management) | Maintain and improve `CLAUDE.md` files — audit quality, capture session learnings, keep project memory current. |
| [plugin-dev](https://github.com/anthropics/claude-plugins-official/tree/main/plugins/plugin-dev) | Develop Claude Code plugins — expert skills for hooks, MCP integration, commands, agents, and validation. |
| [skill-creator](https://github.com/anthropics/claude-plugins-official/tree/main/plugins/skill-creator) | Create, improve, and benchmark agent skills, including evals and variance analysis. |

All plugins come from the official [`claude-plugins-official`](https://github.com/anthropics/claude-plugins-official) marketplace.

### Recommended user-scope plugin

[`superpowers`](https://github.com/anthropics/claude-plugins-official/tree/main/plugins/superpowers) — workflow discipline (brainstorming, subagent-driven development, systematic debugging, and red/green TDD) — is best enabled at **user scope** rather than per-repo, so it applies across all your projects. Enable it from the official marketplace with `/plugin`.

## Skills

Reusable agent skills — drop into a project's `skills/` directory.

| Skill | Does | Use it when |
| --- | --- | --- |
| [lazyboy](skills/lazyboy/SKILL.md) | Forces the laziest solution that actually works — simplest, shortest, most minimal, without becoming negligent. Based on [ponytail](https://github.com/DietrichGebert/ponytail) by DietrichGebert (MIT; see [third-party notices](THIRD_PARTY_NOTICES.md)). | You want an agent to stop over-engineering (YAGNI, KISS, rule of three, fewest files). |

## How to use

1. Start a coding agent from the repo root so it discovers `.claude/settings.json` and the bundled skills.
2. Approve the plugin marketplace and enabled plugins when Claude Code prompts you.
3. Drop individual skills (like [`skills/lazyboy`](skills/lazyboy/SKILL.md)) into another project's `skills/` directory as needed.
