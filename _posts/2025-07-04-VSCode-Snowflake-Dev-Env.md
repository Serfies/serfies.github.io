---
layout: post
title: How To Configure a Local Snowflake Development Environment
subtitle: A guide to configuring a Snowflake development environment with GitHub and Visual Studio Code
gh-repo: serfies/serfies.github.io
gh-badge: [star, fork, follow]
tags: [Snowflake]
comments: true
mathjax: true
author: Andre Serfontein
---

![How To Configure a Local Snowflake Development Environment](/assets/img/2025-07-04-VSCode-Snowflake-Dev-Env.png)

## Local Snowflake Development Environment

This guide contains instructions for data engineers to configure their local Snowflake development environment with Visual Studio Code. Snowflake SQL code linting and auto-formatting will be performed by SQLFluff.

This guide assumes GitHub Enterprise is used as version control system.

## Quick Start

1. [Install Git](#install-git)
2. [Set up Visual Studio Code](#setup-visual-studio-code)
3. [Configure Snowflake SQL linting](#configure-snowflake-sql-linting)
4. [Validate your environment](#validate-environment)
5. [Troubleshoot common issues](#troubleshooting)

## Install Git

Git is required to clone and manage repository content locally. You can authenticate using one of these methods:

### GitHub Desktop (Recommended)

1. Download and install [GitHub Desktop](https://desktop.github.com/download/).
2. Sign in with your Enterprise account.
3. Go to **File → Clone repository**, and enter:

   ```
   https://github.com/ORG/data-products.git
   ```

### HTTPS + Personal Access Token (PAT)

1. Install [GitHub CLI](https://cli.github.com/).
2. Create a PAT with the **repo** scope via GitHub > **Settings > Developer settings > Personal access tokens**.
3. Run:

   ```bash
   gh auth login --hostname github.com
   gh repo clone ORG/repo
   ```

### SSH Key Authentication

1. Follow [GitHub SSH key setup](https://docs.github.com/en/authentication/connecting-to-github-with-ssh).
2. Clone with:

   ```bash
   git clone git@github.com:ORG/repo.git
   ```

## Set up Visual Studio Code

While any editor works, VS Code offers rich support for Git, Snowflake, and SQL tooling.

### Install VS Code

Download and install from [https://code.visualstudio.com/](https://code.visualstudio.com/).

### Recommended Extensions

Install via **Extensions (Ctrl+Shift+X)**:

* **GitHub Pull Requests and Issues** (`GitHub.vscode-pull-request-github`)
* **markdownlint** (`DavidAnson.vscode-markdownlint`)
* **Snowflake SQL Tools** (`Snowflake.snowflake-vscode-extension`)
* **SQLFluff** (`sqlfluff.sqlfluff-vscode`)

## Configure Snowflake SQL linting

Consistent SQL style improves readability and maintainability. This section covers installing and integrating SQLFluff.

### 1. Install Python

Download and install from [https://www.python.org/downloads/](https://www.python.org/downloads/). On Windows, you can install without admin privileges.

### 2. Install SQLFluff and Pre-commit

Create a `.sqlfluff` file in your repo root with:

```ini
[sqlfluff]
dialect = snowflake
exclude_rules = LT04
runaway_limit = 2
large_file_skip_byte_limit = 2000000

[sqlfluff:layout:type:comma]
line_position = trailing

[sqlfluff:rules:capitalisation.keywords]
capitalisation_policy = upper
[sqlfluff:rules:capitalisation.identifiers]
capitalisation_policy = lower
[sqlfluff:rules:capitalisation.functions]
extended_capitalisation_policy = lower
[sqlfluff:rules:capitalisation.literals]
capitalisation_policy = upper
[sqlfluff:rules:capitalisation.types]
extended_capitalisation_policy = upper
```

Install packages and Git hooks:

```bash
pip install sqlfluff pre-commit
pre-commit install
```

### 3. VS Code Settings

Add to `.vscode/settings.json`:

```json
{
  "sqlfluff.configs": "${workspaceFolder}/.sqlfluff",
  "sqlfluff.dialect": "snowflake",
  "sqlfluff.workingDirectory": "${workspaceFolder}",
  "sqlfluff.linter.run": "onType",
  "[sql]": {
    "editor.defaultFormatter": "dorzey.vscode-sqlfluff",
    "editor.formatOnSave": true
  },
  "sqlfluff.format.enabled": true
}
```

## Validate Environment

1. Create a new branch and open a `.sql` file—SQLFluff warnings should appear.
2. Make a small change, commit, and push—confirm the pre-commit hook runs and formats code.

## Troubleshooting

### SQLFluff Extension Access Denied

**Issue:** Endpoint protection blocks `sqlfluff.exe`.

**Solution:**

* Request an exception for `sqlfluff.exe`, or
* Create `sqlfluff.bat` in your Python Scripts folder:

  ```bat
  @echo off
  python -m sqlfluff %*
  ```
* Point VS Code to the batch file:

  ```json
  "sqlfluff.executablePath": "C:/Users/<user>/AppData/Local/Programs/Python/Python313/Scripts/sqlfluff.bat"
  ```

### Pre-commit Hook Failures

* **`sqlfluff-lint` errors:** Code style violations must be fixed before commit.
* **`sqlfluff-fix` warnings:** Complex formatting issues require manual adjustment before auto-fix can complete.