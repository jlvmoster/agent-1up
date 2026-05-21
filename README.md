<p align="center"><img src="assets/powerup.svg" alt="Power-up" width="120"></p>

# A 1-Up for your coding agents.

Drop-in starter kits for pairing coding agents with practical stack conventions.

Each stack includes agent instructions plus tool-specific config so a project can start with the same defaults across Claude Code and Codex.

## Available stacks

| Stack | Includes | Use it when |
| --- | --- | --- |
| [Python](stacks/python/README.md) | `CLAUDE.md`, `.claude/settings.json`, `AGENTS.md`, `.codex/config.toml`, `.codex/rules/default.rules` | You want `uv`, `ruff`, and `ty` defaults for Python projects. |

## How to use a stack

1. Open the stack README.
2. Copy the files for your agent workflow into the root of your project.
3. Adjust any project-specific commands, permissions, or plugins.
4. Start your agent from the project root so it can discover the instructions and config.

For the Python starter kit, use [stacks/python/README.md](stacks/python/README.md).
