# python-template

An opinionated [Copier](https://copier.readthedocs.io) template for Python applications.

## Usage

Generate a new project:

```sh
uvx copier copy gh:jedimasterjonny/python-template path/to/my-app
```

Update an existing generated project to the latest template:

```sh
cd path/to/my-app
uvx copier update
```

## What's inside

- **uv** — single-tool dependency management, locked, uv-managed Python
- **src/** layout — forces proper packaging
- **hatchling** build backend — boring, stable, PEP 517
- **strict Python version band** — pinned at generation time
- **ruff** — lint + format with `select = ["ALL"]` and preview rules on; replaces black, isort, flake8, pyupgrade, pydocstyle
- **ty** — Astral's Rust-based type checker; all warn/ignore-default rules escalated to error
- **pytest** — with `pytest-cov`, `pytest-xdist`, `pytest-randomly`, `pytest-timeout`, `pytest-socket`; warnings-as-errors, 100% coverage floor, 10s per-test timeout, network blocked
- **pre-commit** — hygiene hooks + ruff + uv-lock + typos + ty at `pre-commit`, pytest at `pre-push`, conventional-commits at `commit-msg`. Run `uv run pre-commit install` once after generation.
- **GitHub Actions CI** — parallel `pre-commit`, `test`, and `build` jobs; concurrency cancel on push; `uv sync --locked` enforces lockfile integrity.
- **justfile** — canonical commands: `just check` (lint + fmt-check + typecheck + test), plus `sync`, `fmt`, `test`, `build`, `clean`, etc.
- **.editorconfig** — lf line endings, utf-8, 4-space Python indent, 2-space for yaml/json/toml
- **Renovate** — `config:best-practices` preset; auto-merges patch + minor on green CI, tags me for major review
- **GPL-3.0** — `LICENSE` shipped in the wheel via PEP 639 `license-files`

## Repo layout

- `copier.yml` — template questions and validation
- `template/` — the files generated into new projects (`.jinja` suffix = rendered)
