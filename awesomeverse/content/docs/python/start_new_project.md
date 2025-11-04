---
title: "Start New Project"
layout: docs
weight: 100
---

This is a small personal notebook of tools and steps I used or found useful when starting a new Python project — written down so I can reuse them later. 🚀🧰📝

Below are short, practical steps (with commands) and one-line explanations for each. Feel free to skip or adapt any step to your workflow. ✅

1) Install Poetry — dependency and packaging manager

```shell
pip install poetry
```

Use Poetry to manage virtual environments, dependencies, and packaging. You can also use the official installer from https://install.python-poetry.org if you prefer. 🛠️

2) Create a new project (using Poetry)

```shell
poetry new my_new_awesome_project
cd my_new_awesome_project
```

Create a new package skeleton with a recommended layout (tests, package dir, pyproject.toml). I'm assuming Poetry here — replacing the earlier `pip new` with `poetry new` for a standard flow. ✨

3) Add runtime dependencies

```shell
poetry add pydantic pydantic-settings
```

pydantic: runtime data validation and settings management. pydantic-settings: structured app configuration. Useful for typed configs and safer models. 🧩

4) Add development and security tools

```shell
poetry add -D ruff pip-audit pytest pytest-cov bandit pre-commit
```

- ruff: fast linter/formatter
- pip-audit: dependency security auditing
- pytest + pytest-cov: testing and coverage
- bandit: security static analysis
- pre-commit: run linters/formatters automatically before commit

These go to dev-dependencies (-D) so they don't end up in production packages. 🔒🧪

5) Initialize git and basic repo files

```shell
git init
# create README, LICENSE, .gitignore, etc.
```

Start version control early. Add a concise README and a LICENSE file so others (and future you) know the project's purpose and license. 🧾

6) Use the "src" layout (recommended)

Example project tree using the recommended `src/` layout — this helps avoid accidental imports of local modules during tests and keeps packaging clean. 📁

```text
my_new_awesome_project/
├── pyproject.toml
├── src/
│   └── my_new_awesome_project/
│       ├── __init__.py
│       └── core.py
├── tests/
│   └── test_basic.py
└── .github/workflows/ci.yml
```

Quick tips:
- Keep tests outside `src/` so pytest imports the installed package, not local files. 🧪
- Put config and defaults in `config.py` or use `pydantic-settings` and document env vars in `.env.example`. 🔧
- Add small helper scripts in `scripts/` and keep CI config under `.github/workflows/`. 🤖

7) Install and enable pre-commit hooks

```shell
# after adding pre-commit in dev deps
pre-commit install
pre-commit run --all-files
```

