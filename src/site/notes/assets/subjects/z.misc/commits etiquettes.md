---
{"dg-publish":true,"permalink":"/assets/subjects/z-misc/commits-etiquettes/","dg-note-properties":{}}
---

#misc 

## Conventional Commits

Common format:

```text
type(scope): short description

optional longer explanation

optional footer
```

Example:

```text
feat(auth): add login form validation
```

---

## Main commit types

| Type       | When to use                                        | Example                                     |
| ---------- | -------------------------------------------------- | ------------------------------------------- |
| `feat`     | New feature for the user/app                       | `feat(cart): add coupon support`            |
| `fix`      | Bug fix                                            | `fix(api): prevent crash on empty response` |
| `docs`     | Documentation only                                 | `docs(readme): add installation steps`      |
| `style`    | Formatting only, no logic change                   | `style(app): fix indentation and spacing`   |
| `refactor` | Code cleanup/restructure without changing behavior | `refactor(users): extract validation logic` |
| `perf`     | Performance improvement                            | `perf(list): reduce database queries`       |
| `test`     | Add or update tests                                | `test(auth): add login edge cases`          |
| `build`    | Build system, dependencies, packaging              | `build(deps): upgrade vite to v7`           |
| `ci`       | CI/CD config changes                               | `ci(github): run tests on pull request`     |
| `chore`    | Maintenance, small non-feature changes             | `chore: update editor config`               |
| `revert`   | Undo a previous commit                             | `revert: remove broken payment flow`        |

---

## Simple rule of thumb

Ask:

1. Does it add a feature? → `feat`
2. Does it fix a bug? → `fix`
3. Is it only docs? → `docs`
4. Is it only formatting? → `style`
5. Does it improve code without changing behavior? → `refactor`
6. Does it make something faster? → `perf`
7. Is it tests only? → `test`
8. Is it dependencies/build tooling? → `build`
9. Is it GitHub Actions/CI? → `ci`
10. Is it small maintenance? → `chore`

If unsure, use:

```text
chore: describe maintenance change
```

or:

```text
refactor: describe code cleanup
```

---

## Scope

The scope is optional and says what part changed.

Examples:

```text
feat(auth): add password reset
fix(navbar): correct mobile menu height
docs(readme): update setup instructions
```

Good scopes:

```text
auth, api, ui, navbar, cart, db, config, tests, readme
```

Keep scopes short and consistent.

---

## Breaking changes

If your change breaks existing behavior, mark it clearly.

Option 1:

```text
feat(api)!: change user endpoint response format
```

Option 2:

```text
feat(api): change user endpoint response format

BREAKING CHANGE: users endpoint now returns data inside `items`.
```

Use this when old code may stop working.

---

## Good commit message examples

Good:

```text
feat(auth): add email validation on signup
fix(cart): prevent negative quantities
docs(readme): add Linux setup steps
refactor(utils): simplify date formatting
test(api): add tests for user creation
```

Bad:

```text
update code
fix stuff
changes
wip
asdf
```

---

## Commit message rules

Keep subject line short:

```text
feat(cart): add checkout button
```

Use imperative mood:

```text
add button
```

Not:

```text
added button
adds button
```

Think:

```text
If applied, this commit will...
```

Example:

```text
If applied, this commit will add checkout button.
```

---

## When to commit

Commit when you finish one small logical change.

Good:

```text
one feature = one commit
one bug fix = one commit
one refactor = one commit
```

Avoid mixing:

```text
feat + fix + refactor + formatting in one commit
```

If you accidentally mixed changes, you can split later with:

```bash
git add -p
```

---

## Branch naming

Use clear branch names.

Examples:

```text
feat/login-page
fix/navbar-mobile
docs/readme-setup
refactor/user-service
```

Good format:

```text
type/short-description
```

Examples:

```bash
git checkout -b feat/login-page
git checkout -b fix/cart-total-bug
git checkout -b docs/update-readme
```

---

## GitHub workflow for your own repos

Simple flow:

```bash
git checkout main
git pull
git checkout -b feat/my-feature

# make changes

git status
git add -p
git commit -m "feat(scope): add my feature"
git push -u origin feat/my-feature
```

Then open a Pull Request if you want review, or merge if it is your own repo.

---

## GitHub workflow for contributing to others

1. Fork the repo.
2. Clone your fork.
3. Add upstream remote.
4. Create branch from latest upstream main.
5. Make small commits.
6. Push to your fork.
7. Open Pull Request.

Commands:

```bash
git clone https://github.com/YOUR_USERNAME/repo.git
cd repo

git remote add upstream https://github.com/ORIGINAL_OWNER/repo.git

git fetch upstream
git checkout main
git merge upstream/main

git checkout -b fix/my-fix
```

Before opening PR:

```bash
git fetch upstream
git rebase upstream/main
```

Then push:

```bash
git push -u origin fix/my-fix
```

---

## Pull request tips

Keep PRs small.

Good PR:

```text
Fixes one bug
Adds one feature
Updates one doc page
```

Bad PR:

```text
Fixes bug, reformats whole project, upgrades dependencies, changes architecture
```

PR title example:

```text
fix(cart): prevent negative item quantity
```

PR description example:

```text
## Problem
Cart allowed negative quantities.

## Solution
Added validation to force minimum quantity of 1.

## Testing
Added unit tests and tested manually.
```

---

## Useful Git habits

Check what changed before committing:

```bash
git status
git diff
```

Stage selectively:

```bash
git add -p
```

Amend last commit only if not pushed yet:

```bash
git commit --amend
```

Undo unstaged changes to a file:

```bash
git checkout -- file.txt
```

Or in newer Git:

```bash
git restore file.txt
```

Unstage a file:

```bash
git restore --staged file.txt
```

View log cleanly:

```bash
git log --oneline --graph --decorate
```

---

## Rebasing vs merging

For personal/contributor branches, rebasing keeps history clean:

```bash
git fetch origin
git rebase origin/main
```

But avoid rebasing shared public branches if you are not sure.

Rule of thumb:

```text
Rebase local/personal branches.
Merge or squash into main.
Do not rebase branches others are using.
```

---

## Squash commits

For GitHub PRs, squash merging is often easiest:

```text
feat(auth): add login page
```

It turns many messy commits into one clean commit.

Useful when your commits are like:

```text
fix
fix again
oops
tests
```

But still write good local commit messages. It helps review.

---

## Semantic versioning connection

Conventional commits often connect to versions:

| Commit type | Version bump |
|---|---|
| `fix` | patch, e.g. `1.0.1` |
| `feat` | minor, e.g. `1.1.0` |
| breaking change | major, e.g. `2.0.0` |

Example:

```text
feat(api)!: remove old users endpoint
```

This may mean version goes from:

```text
1.4.2 → 2.0.0
```

---

## Repo management tips

Every repo should have:

```text
README.md
.gitignore
LICENSE
```

For code projects, also useful:

```text
CHANGELOG.md
CONTRIBUTING.md
```

---

## README basics

Include:

```text
What the project does
How to install
How to run
How to test
Screenshots if useful
```

Simple README structure:

```md
# Project Name

Short description.

## Features

- Feature 1
- Feature 2

## Installation

Commands here.

## Usage

Commands here.

## Development

Commands here.

## License

MIT
```

---

## `.gitignore` tips

Never commit:

```text
node_modules/
venv/
__pycache__/
.env
build/
dist/
.cache/
*.log
```

Generate ignore files:

```text
https://www.toptal.com/developers/gitignore
```

---

## Environment variables

Never commit secrets.

Bad:

```text
.env
api keys
tokens
passwords
database credentials
```

Use:

```text
.env.example
```

Example:

```env
DATABASE_URL=
API_KEY=
```

If you accidentally commit a secret:

1. Remove it from history.
2. Rotate/revoke the secret immediately.

---

## Issues and labels

Use issues for:

```text
bugs
feature ideas
questions
tasks
```

Good issue title:

```text
Navbar overlaps content on mobile
```

Bad issue title:

```text
UI broken
```

Use labels:

```text
bug
enhancement
documentation
good first issue
help wanted
```

---

## Contributing checklist

Before opening PR:

```bash
git status
git diff
git log --oneline
```

Make sure:

```text
Branch is up to date
Tests pass
Code runs
No debug prints
No unrelated formatting changes
Commit messages are clear
PR description explains the change
```

---

## Recommended commit style to start using now

Use this default:

```text
type(scope): short imperative summary
```

Examples:

```text
feat(ui): add dark mode toggle
fix(form): validate email field
docs(readme): add local setup guide
refactor(api): simplify error handling
test(utils): add date parser tests
chore: update dependencies
```

If no scope is needed:

```text
fix: correct typo in config loader
```

---

## Small practical habit

Before every commit, ask:

```text
Can this commit message be understood by someone else in 6 months?
Does this commit contain only one logical change?
Would I be comfortable seeing this in release notes?
```

If yes, you are doing well.