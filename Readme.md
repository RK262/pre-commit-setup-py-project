# Pre-commit setup for Python Projects

This repository contains steps used for setting pre-commit.

## Table of Contents
1. [What is pre-commit](#PreCommitAbout)
2. [How to install](#HowToInstall)
3. [Add a pre-commit configuration](#PreCommitConfiguration)
4. [Install and run git hook scripts](#InstallGitHookScripts)
5. [Pre commit config example](#PreCommitConfigExample)
6. [Conventional Commit](#ConventionalCommits)

## What is pre-commit <a name="PreCommitAbout"></a>
A framework for managing and maintaining multi-language pre-commit hooks.
Git hook scripts are useful for identifying simple issues before submission to code review. We run our hooks on every commit to automatically point out issues in code such as missing semicolons, trailing whitespace, and debug statements. By pointing these issues out before code review, this allows a code reviewer to focus on the architecture of a change while not wasting time with trivial style nitpicks.

## How to install <a name="HowToInstall"></a>
You can Install using pip
```
$ pip install pre-commit
```
Or, in your python project add the following to your requirements.txt (or requirements-dev.txt):
```
pre-commit
```
Check `pre-commit` version:
```
$ pre-commit --version
```

## Add a pre-commit configuration <a name="PreCommitConfiguration"></a>
- create a file named with name `.pre-commit-config.yaml` in project root directory.
- To generate a sample `pre-commit-config` configuration file , use command `pre-commit sample-config`

## Install and run git hook scripts <a name="InstallGitHookScripts"></a>
- run `pre-commit install` to set up the git hook scripts
```
$ pre-commit install
pre-commit installed at .git/hooks/pre-commit
```
- To run against all files
```
$ pre-commit run --all-files
```

## Pre commit config example <a name="PreCommitConfigExample"></a>

```
repos:
- repo: https://github.com/compilerla/conventional-pre-commit
    rev: "v3.4.0"
    hooks:
      - id: conventional-pre-commit
        stages: [commit-msg]
        args: [feat, fix, chore, ci, docs,test]
-   repo: https://github.com/pre-commit/pre-commit-hooks
    rev: v2.3.0
    hooks:
    -   id: check-yaml
    -   id: end-of-file-fixer
    -   id: trailing-whitespace
-   repo: https://github.com/psf/black
    rev: 22.10.0
    hooks:
    -   id: black
```

## Conventional Commit <a name="ConventionalCommits"></a>
Conventional Commits provide a standardized way of writing commit messages to improve readability and automate release management.
```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]

- type: Defines the purpose of the commit.
- scope (optional): Provides context about what part of the codebase was changed (e.g., ui, api, auth).
- description: A short explanation of what was done.
- body (optional): Longer description, often explains the reasoning behind the change.
- footer (optional): Contains additional information like BREAKING CHANGE or references to issues or pull requests.

```
### Types
* `feat` : A new feature for the user.
```
$ feat(api): add authentication endpoint
```
* `fix` : A bug fix.
```
$ fix(ui): fixed some issue.
```
* `chore` : Maintenance tasks that don't modify source code (e.g., updating dependencies)
```
$ chore(deps): update dependency version
```
* `docs` : Documentation changes (e.g., README, inline docs)
```
$ docs(README): update installation instructions
```
* `style` : Changes that do not affect the meaning of the code (e.g., formatting, white-space)
```
$ style: improve code formatting
```
* `refactor` : A code change that neither fixes a bug nor adds a feature (e.g., code structure changes).
```
$ refactor(auth): simplify login logic
```
* `test` : Adding or updating tests.
```
$ test(api): add unit tests for user login
```
* `perf` : A change that improves performance.
```
$ perf(database): improve query performance
```
* `build` : Changes that affect the build system or external dependencies (e.g., pypi).
```
$ build: update npm scripts for build
```
* `ci` : Changes to CI configuration files and scripts (e.g. GitHub Actions).
```
$ ci: add linting step in CI pipeline
```
* `revert` : Reverts a previous commit.
```
$ revert: revert commits xyz
```
* `BREAKING CHANGE` : Indicates that the change introduces an API-breaking change. Usually follows a feat or fix commit but can be standalone.
```
$ feat(auth): add OAuth2 support BREAKING CHANGE: authentication method now requires OAuth2 tokens
```
