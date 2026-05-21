# Python stack

This project uses the Astral toolchain:

- **uv** — package and project manager (deps, venvs, scripts, tools)
- **ruff** — linter and formatter
- **ty** — type checker

## Commands

- Install / sync deps: `uv sync`
- Run a script: `uv run <script.py>`
- Run a tool without installing: `uvx <tool>`
- Add a dependency: `uv add <pkg>` (use `--dev` for dev-only)
- Lint: `uvx ruff check`
- Format: `uvx ruff format`
- Type check: `uvx ty check`
- Tests: `uv run pytest`

## Conventions

- Manage Python and dependencies through `uv` — do not invoke `pip`, `python -m venv`, or `pyenv` directly.
- Run `ruff check --fix` and `ruff format` before committing.
- All new code is type-annotated; `ty check` must pass.
- Prefer `pathlib.Path` over `os.path`, `logging` over `print`, and explicit imports over `*`.
