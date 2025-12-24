# Git & GitHub Workflow Rules

This document defines the **required workflow** for contributing to repositories in **Acsys Investments Pvt Ltd**.  
It is written to be clear, enforceable, and easy to follow for day‑to‑day development.

> **Goal:** keep `main` stable, make changes reviewable, and ensure work is traceable to Issues/Projects.

## Core rules (non‑negotiable)

1. **Never push directly to `main`.**
2. **Every change must be made on a branch** and merged via a **Pull Request (PR)**.
3. **PRs must have:**
   - a clear title
   - a meaningful description (what/why/how-tested)
   - a link to a GitHub **Issue** and/or **Project** item when applicable
4. **PRs must be reviewed** before merging (at least 1 reviewer unless stated otherwise).
5. **No secrets in Git.** Do not commit tokens, keys, passwords, `.env` files.

---

## Repository expectations (minimum standard)

Each repository should contain:

- `README.md` — setup, run, test instructions
- `.gitignore` — appropriate for the project

---

## Branching model

### Default branch
- `main` is the default branch.
- `main` must remain stable and deployable.

### Always branch from the latest `main`
Before starting work:

```bash
git checkout main
git pull origin main
```

Then create a branch:

```bash
git checkout -b <branch-name>
```

---

## Branch naming convention (required)

### Format

```text
type/short-description
```

### Allowed `type` values

- `feature/` — new functionality
- `fix/` — bug fix
- `hotfix/` — urgent production/staging fix
- `chore/` — refactor, maintenance, tooling, dependencies
- `docs/` — documentation-only changes
- `test/` — test-only changes

### Examples (good)

- `feature/add-login-api`
- `fix/null-check-profile`
- `hotfix/payment-timeout`
- `docs/update-setup-guide`
- `chore/upgrade-dependencies`

### Examples (not allowed)

- `final`
- `newfeature`
- `branch1`
- `nikita-changes`

---

## Commit guidelines

### Commit messages
- Write clear messages that explain **what changed**
- Keep commits small and focused
- Avoid “wip”, “final”, “temp”, “changes”

✅ Good:

```bash
git commit -m "Add validation to signup form"
git commit -m "Fix crash when response is empty"
```

Optional (recommended for consistency): conventional commits

- `feat: ...`
- `fix: ...`
- `docs: ...`
- `chore: ...`
- `refactor: ...`
- `test: ...`

Example:

```bash
git commit -m "feat: add OTP login flow"
```

---

## How to push your changes

### Case A — You have **Write** access (most common workflow)

1) Create and commit on your branch  
2) Push branch:

```bash
git push -u origin <branch-name>
```

Example:

```bash
git push -u origin feature/add-login-api
```

3) Open a PR (see next section)

---

## Pull Requests (PRs)

### When to open a PR
- When the work is ready for review and merge
- Or earlier as a **Draft PR** if you want feedback while still working

### How to create a PR (GitHub UI)
1. Go to the repository on GitHub
2. Click **Pull requests**
3. Click **New pull request**
4. Choose:
   - **base**: `main`
   - **compare**: your branch (`feature/...`, `fix/...`, etc.)
5. Click **Create pull request**

---

## PR title rules

PR titles must be clear, short, and actionable.

✅ Good:
- `Add OTP login flow`
- `Fix crash when response is empty`
- `Update deployment steps`

❌ Bad:
- `Fix`
- `Updates`
- `Final changes`
- `My work`

---

## PR description rules (required)

Every PR must include:

1. **What changed**
2. **Why**
3. **How tested**
4. **Screenshots** (if UI change)

### Copy/paste PR description template

```md
## What changed
- 

## Why
- 

## How tested
- 

## Screenshots (if applicable)
-
```

### Example (filled)

```md
## What changed
- Added OTP verification endpoint
- Updated login UI to support OTP input

## Why
- Required for secure authentication

## How tested
- Unit tests: `npm test`
- Manual testing on staging
```

---

## Linking PRs to Issues and Projects (traceability)

### Link PR to a GitHub Issue (recommended)
In the PR description, use:

```md
Fixes #123
```

This automatically:
- links the PR to the issue
- closes the issue when the PR is merged

You can also use:
- `Closes #123`
- `Resolves #123`

### Link PR to a GitHub Project
On the PR page, right sidebar:
- **Projects** → select the correct project board

If you don’t see Projects, ask an admin/maintainer to enable it.

---

## Reviews & merging

### Review expectations
- PRs should be reviewed before merging
- Keep PRs small enough to review effectively
- Respond to review comments and push updates to the same branch
- Use discussions to resolve disagreements (don’t argue in code)

### Merge expectations
- Prefer **Squash and merge** for a clean history (unless repo policy says otherwise)
- Maintainers/admins handle merges unless explicitly delegated

---

## Keeping your branch up to date

If `main` has moved ahead and you need updates:

```bash
git checkout main
git pull origin main
git checkout <branch-name>
git merge main
```

Resolve conflicts if any, then push:

```bash
git push
```

---

## Common “do not” list

🚫 Do not:
- push directly to `main`
- force-push to shared branches
- commit secrets (tokens, passwords, keys, `.env`)
- mix unrelated refactors with feature work in the same PR
- open PRs without description/testing notes

---

## Quick checklist (before opening a PR)

- [ ] Branch created from latest `main`
- [ ] Branch name follows `type/short-description`
- [ ] Commits are clear and focused
- [ ] PR title is meaningful
- [ ] PR description includes what/why/how-tested
- [ ] Linked to Issue/Project when applicable
- [ ] No secrets committed
- [ ] Ready for review

---

## Enforcement notes (GitHub Free orgs)

Depending on your GitHub plan and repository visibility, some enforcement features (rulesets/branch protections) may not apply.  
Regardless of tooling, the **process above is mandatory** and is enforced through:
- access control (who has write access)
- code reviews
- maintainers’ responsibility

---

## Help / Contact

For access requests, reviews, or workflow questions, contact:
- **Maintainers/Admins:** nikitasharma@acsysindia.com
