# Python agent starter kit

This starter kit gives Claude Code and Codex the same Python project expectations: use `uv` for dependency and script execution, `ruff` for linting and formatting, and `ty` for type checking.

## Files

- `CLAUDE.md` - Claude Code project instructions.
- `.claude/settings.json` - Claude Code permissions and plugin marketplace setup.
- `AGENTS.md` - Codex project instructions.
- `.codex/config.toml` - Codex project config.
- `.codex/rules/default.rules` - Codex command rules that mirror the Claude Code Bash allow-list.

## Use with Claude Code

Copy `CLAUDE.md` and `.claude/settings.json` into the root of a Python project. Claude Code reads `CLAUDE.md` as project guidance and uses `.claude/settings.json` for shared settings such as allowed Bash command prefixes and enabled plugins.

The bundled Claude setup allows:

- `git *`
- `uv *`
- `uvx *`

It also enables the Claude plugins listed in `.claude/settings.json`, including Astral tooling and Pyright LSP support.

## Shared plugin callout

The plugin overlap between this starter kit's Claude Code setup and the local Codex plugin ecosystem is:

| Capability | Claude Code plugin | Codex plugin |
| --- | --- | --- |
| Superpowers workflow skills | `superpowers@claude-plugins-official` | `superpowers@openai-curated` |

The other Claude Code plugins in `.claude/settings.json` are intentionally Claude-specific in this kit:

- `claude-md-management@claude-plugins-official`
- `pyright-lsp@claude-plugins-official`
- `skill-creator@claude-plugins-official`
- `astral@astral-sh`

Codex still gets the same Python workflow expectations through `AGENTS.md`, `.codex/config.toml`, and `.codex/rules/default.rules`, but those files do not install or enable Claude Code marketplace plugins.

## Use with Codex

Copy `AGENTS.md` and the `.codex/` directory into the root of a Python project. Codex reads `AGENTS.md` for project guidance. Codex reads `.codex/config.toml` and `.codex/rules/default.rules` only after you trust the project.

The Codex config uses `approval_policy = "on-request"` and `default_permissions = ":workspace"` so Codex can work inside the active workspace while still asking for approval when it needs to leave the normal sandbox. The rules file allows the same command families as the Claude setup:

- `git`
- `uv`
- `uvx`

Codex plugin setup is intentionally not copied from Claude Code. Claude Code's `extraKnownMarketplaces` and `enabledPlugins` keys do not map directly to Codex `config.toml`; install Codex plugins separately with `codex plugin` when a project needs them.

## Expected workflow

1. Install or sync dependencies with `uv sync`.
2. Make changes using `uv run <script.py>` or `uvx <tool>`.
3. Run `uvx ruff check --fix` and `uvx ruff format`.
4. Run `uvx ty check`.
5. Run tests with `uv run pytest`.
