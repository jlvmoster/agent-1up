# agent-1up

A collection of reusable agent skills and a curated Claude Code setup for coding agents. It is a content repository — Markdown and JSON, no application code, build, or test suite.

## Layout

- `skills/<name>/SKILL.md` — distributable skills meant to be dropped into another project's `skills/` directory.
- `.claude/settings.json` — the curated plugin bundle (`enabledPlugins`), marketplace sources, and read-only-git permissions that apply when working in this repo.
- `README.md` — user-facing docs, including a plugin table and a skills table.
- `THIRD_PARTY_NOTICES.md` — attribution and license text for skills derived from external work.

## Conventions

- **Stay minimal**: this is a tiny repo (one skill). Apply the rule of three before adding repo automation (hooks/agents/internal skills) — prefer on-demand commands and the enabled plugins (`skill-creator`, `plugin-dev`, `claude-md-management`) over standing infrastructure.
- **SKILL.md frontmatter**: every `skills/*/SKILL.md` has `name` (matching its directory), a `description`, and — for derived skills — a `license` field. Write descriptions in third person: what it does, then when to use it, with concrete trigger phrases.
- **Plugins come from the official marketplace**: enable plugins as `name@claude-plugins-official` and declare the marketplace in `extraKnownMarketplaces`. Verify the exact plugin name against the local manifest (`~/.claude/plugins/marketplaces/<marketplace>/.claude-plugin/marketplace.json`) before adding it — a typo (e.g. `skills-creator` vs `skill-creator`) silently disables the plugin.
- **Attribution**: a skill based on external work needs both a `license:` field and a matching `THIRD_PARTY_NOTICES.md` entry (full license text for MIT/BSD/Apache).
- **Git permissions are read-only by design**: `.claude/settings.json` allows only read-only git subcommands. Mutating git operations prompt — do not broaden this to a `git *` wildcard.
- **Keep the README in sync**: when `enabledPlugins` or `skills/` changes, update the matching README table by hand.

## Conductor portability

This repo is developed in Conductor, where each workspace is a temporary, randomly-named git worktree. Never commit an absolute path that points inside a workspace directory — it breaks in the next workspace. Use relative paths or `${CLAUDE_PROJECT_DIR}`.

## Verifying changes

There are no tests. Validate `settings.json` edits with `python3 -m json.tool .claude/settings.json`.
