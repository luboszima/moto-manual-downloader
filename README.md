<p align="center">
  <a href="https://github.com/astral-sh/uv" target="blank"><img src="https://github.com/astral-sh/uv/blob/8674968a17e5f2ee0dda01d17aaf609f162939ca/docs/assets/logo-letter.svg" height="100" alt="uv logo" /></a>
  <a href="https://pre-commit.com/" target="blank"><img src="https://pre-commit.com/logo.svg" height="100" alt="pre-commit logo" /></a>
  <a href="https://github.com/astral-sh/ruff" target="blank"><img src="https://raw.githubusercontent.com/astral-sh/ruff/8c20f14e62ddaf7b6d62674f300f5d19cbdc5acb/docs/assets/bolt.svg" height="100" alt="ruff logo" style="background-color: #ef5552" /></a>
  <a href="https://bandit.readthedocs.io/" target="blank"><img src="https://raw.githubusercontent.com/pycqa/bandit/main/logo/logo.svg" height="100" alt="bandit logo" /></a>
  <a href="https://docs.pytest.org/" target="blank"><img src="https://raw.githubusercontent.com/pytest-dev/pytest/main/doc/en/img/pytest_logo_curves.svg" height="100" alt="pytest logo" /></a>
</p>

<p align="center">
  <a href="https://docs.docker.com/" target="blank"><img src="https://www.docker.com/wp-content/uploads/2022/03/Moby-logo.png" height="60" alt="Docker logo" /></a>
  <a href="https://github.com/features/actions" target="blank"><img src="https://avatars.githubusercontent.com/u/44036562" height="60" alt="GitHub Actions logo" /></a>
</p>

# moto-manual-downloader

Download PDF manuals for any motorcycle

[![CodeQL](https://github.com/luboszima/moto-manual-downloader/workflows/codeql/badge.svg)](https://github.com/luboszima/moto-manual-downloader/actions/workflows/codeql.yml)
[![GitHub CI](https://github.com/luboszima/moto-manual-downloader/workflows/ci/badge.svg)](https://github.com/luboszima/moto-manual-downloader/actions/workflows/ci.yml)
[![GitHub license](https://img.shields.io/github/license/luboszima/moto-manual-downloader)](https://github.com/luboszima/moto-manual-downloader)

---

## Table of Contents

- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [What's in the box ?](#whats-in-the-box-)
- [Testing](#testing)
- [Docker](#docker)
- [Conventional Commits](#conventional-commits)

---

## Prerequisites

This project uses [asdf](https://asdf-vm.com/) for tool version management. The required versions are specified in the `.tool-versions` file:

- [Python](https://www.python.org/downloads/) **3.13.5**
- [pre-commit](https://pre-commit.com/#install) **4.2.0**
- [uv](https://docs.astral.sh/uv/getting-started/installation/) **0.7.21**
- [task](https://taskfile.dev/) **3.44.0**
- [shfmt](https://github.com/mvdan/sh) **3.11.0**
- [shellcheck](https://www.shellcheck.net/) **0.10.0**
- [docker](https://docs.docker.com/get-docker/) (_optional_)

You can install all required tools with:

```bash
asdf install
# or
task dependencies
task install
# or
bash scripts/dependencies_linux.sh # or dependencies_darwin.sh
bash scripts/install.sh
```

---

## Installation

1. Clone the git repository

   ```bash
   git clone https://github.com/luboszima/moto-manual-downloader.git
   ```

2. Go into the project directory

   ```bash
   cd luboszima/moto-manual-downloader
   ```

3. Checkout working branch

   ```bash
   git checkout <branch>
   ```

4. Enable pre-commit hooks

   ```bash
   pre-commit install
   ```

   > **Note:** A pre-commit hook is set up to enforce [Conventional Commits](https://www.conventionalcommits.org/) for commit messages.

5. Configure Python environment

   ```bash
   uv python install
   uv venv
   source .venv/bin/activate
   ```

---

## What's in the box ?

### uv

[uv](https://github.com/astral-sh/uv) is an extremely fast Python package and project manager, written in Rust.

**pyproject.toml file** ([`pyproject.toml`](pyproject.toml)): orchestrate your project and its dependencies
**uv.lock file** ([`uv.lock`](uv.lock)): ensure that the package versions are consistent for everyone
working on your project

For more configuration options and details, see the [configuration docs](https://docs.astral.sh/uv/).

### pre-commit

[pre-commit](https://pre-commit.com/) is a framework for managing and maintaining multi-language pre-commit hooks.

**.pre-commit-config.yaml file** ([`.pre-commit-config.yaml`](.pre-commit-config.yaml)): describes what repositories and
hooks are installed

For more configuration options and details, see the [configuration docs](https://pre-commit.com/).

### ruff

[ruff](https://github.com/astral-sh/ruff) is an extremely fast Python linter, written in Rust.

Rules are defined in the [`pyproject.toml`](pyproject.toml).

For more configuration options and details, see the [configuration docs](https://github.com/astral-sh/ruff#configuration).

### mypy

[mypy](http://mypy-lang.org/) is an optional static type checker for Python that aims to combine the benefits of
dynamic (or "duck") typing and static typing.

Rules are defined in the [`pyproject.toml`](pyproject.toml).

For more configuration options and details, see the [configuration docs](https://mypy.readthedocs.io/).

### bandit

[bandit](https://bandit.readthedocs.io/) is a tool designed to find common security issues in Python code.

Rules are defined in the [`pyproject.toml`](pyproject.toml).

For more configuration options and details, see the [configuration docs](https://bandit.readthedocs.io/).

### docformatter

[docformatter](https://github.com/PyCQA/docformatter) is a tool designed to format docstrings to
follow [PEP 257](https://peps.python.org/pep-0257/).

Options are defined in the [`.pre-commit-config.yaml`](.pre-commit-config.yaml).

---

## Testing

We are using [pytest](https://docs.pytest.org/) & [pytest-cov](https://github.com/pytest-dev/pytest-cov) to write tests.

To run tests:

```bash
uv run pytest tests
```

<details>

<summary>Output</summary>

```text
collected 1 item

tests/test_python_boilerplate.py::test_hello_world PASSED
```

</details>

To run tests with coverage:

```bash
uv run pytest tests --cov=src
```

<details>

<summary>Output</summary>

```text
collected 1 item

tests/test_python_boilerplate.py::test_hello_world PASSED

---------- coverage: platform linux, python 3.13.5-final-0 -----------
Name                                 Stmts   Miss  Cover
--------------------------------------------------------
src/python_boilerplate/__init__.py       1      0   100%
src/python_boilerplate/main.py           6      2    67%
--------------------------------------------------------
TOTAL                                    7      2    71%
```

</details>

---

## Docker

### Build

To build the docker `production` image using [`Dockerfile`](Dockerfile):

```bash
docker build . -t my-python-application:latest
```

To build the docker `development` image using [`Dockerfile`](Dockerfile):

```bash
docker build . --target development -t my-python-application:dev
```

### Run

To run the python app example inside Docker:

```bash
docker run -it --rm my-python-application:latest # or :dev for development
```

<details>

<summary>Output</summary>

```text
Hello World
```

</details>

### Execute command inside container

```bash
docker run -it --rm my-python-application:latest bash
```

---

## Conventional Commits

This project uses [Conventional Commits](https://www.conventionalcommits.org/) for commit messages. A pre-commit hook is configured to enforce this standard. Please make sure your commit messages follow the Conventional Commits specification (e.g., `feat: add new feature`, `fix: correct a bug`).

If you try to commit with a message that does not follow the convention, the pre-commit hook will block the commit.

---
