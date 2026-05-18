# Semantic Commit Message

A complete guide to **Semantic Commit Message** — a convention for writing consistent, structured, and easy-to-understand commit messages.

> © [Dezkrazzer](https://github.com/Dezkrazzer)

## 📋 Table of Contents

- [Introduction](#introduction)
- [Commit Format](#commit-format)
- [Commit Types](#commit-types)
- [Usage Examples](#usage-examples)
- [Best Practices](#best-practices)
- [Tools & Integration](#tools--integration)
- [Benefits](#benefits)

## Introduction

Semantic Commit Message is a convention for writing commit messages that follow a specific, structured format. This standard helps to:

- **Read commit history** more easily
- **Automate** versioning and changelog generation
- Improve **team collaboration**
- Keep change **tracking** structured and clear

## Commit Format

The standard format for Semantic Commit Message is:

```
<type>(<scope>): <subject>

<body>

<footer>
```

### Explanation:

| Part | Description |
|------|-------------|
| **type** | The kind of change (feat, fix, docs, etc.) |
| **scope** | The part/module affected (optional) |
| **subject** | A short description of the change (imperative, lowercase) |
| **body** | Detailed explanation of the change (optional) |
| **footer** | Additional info such as issue numbers (optional) |

### Example Format:

```
feat(authentication): add login feature with OAuth

Add OAuth 2.0 integration to improve security.
Users can sign in with Google or GitHub accounts.

Closes #123
```

## Commit Types

| Type | Name | Description | Example |
|------|------|-------------|---------|
| **feat** | Feature | Adds a new feature | `feat: add login feature` |
| **fix** | Bug Fix | Fixes a bug or error | `fix: fix crash when uploading large images` |
| **docs** | Documentation | Changes to documentation (README, Wiki) | `docs: update installation instructions in README` |
| **style** | Style | Code style changes (formatting) without logic changes | `style: remove extra spaces in header` |
| **refactor** | Refactor | Code restructuring without adding features or fixing bugs | `refactor: simplify payroll calculation logic` |
| **perf** | Performance | Improvements to performance | `perf: optimize DB query for user list` |
| **test** | Test | Add or fix tests | `test: add unit tests for payment module` |
| **chore** | Chore | Small tasks, dependency updates, build scripts | `chore: update discord.js to v14` |
| **build** | Build | Changes to build system (npm, gradle, gulp) | `build: add css minify script` |
| **ci** | CI | Changes to CI configuration (GitHub Actions, Jenkins) | `ci: fix deploy script to vercel` |
| **revert** | Revert | Revert a previous commit | `revert: revert commit a2b3c4` |

## Usage Examples

### 1. New Feature

```
feat(user-profile): add user profile page

- Adds a profile page showing user information
- Users can edit their profile picture
- Adds follow/unfollow functionality

Closes #45
```

### 2. Bug Fix

```
fix(checkout): fix error in payment form

Fixes an issue where the payment form did not submit when using Safari.
The bug was caused by an email validation incompatible with Safari.

Closes #89
```

### 3. Documentation Update

```
docs(README): update project setup instructions

- Add clear system requirements
- Improve confusing installation steps
- Add a troubleshooting section
```

### 4. Refactoring

```
refactor(auth): move authentication logic out of controller

Moved authentication logic from `UserController` to `AuthService` to
improve reusability and testability.
```

### 5. Performance Improvement

```
perf(database): use connection pooling for DB queries

Reduced response time from 200ms to 50ms by implementing connection
pooling in the database layer.
```

### 6. Testing

```
test(payment): add test cases for payment gateway

- Test successful payment
- Test failed payment
- Test timeout handling
- Test refund process
```

### 7. Dependency Changes

```
chore(dependencies): upgrade React from v17 to v18

- Update all React dependencies
- Fix breaking changes in components
- Update testing library versions
```

### 8. CI/CD Configuration

```
ci(github-actions): add workflow for automated testing

Adds a GitHub Actions workflow that:
- Runs linter on every pull request
- Runs unit tests automatically
- Generates coverage report
```

## Best Practices

### ✅ Do

- **Use the imperative mood**: "add" not "added" or "adding"
- **Do not capitalize** the first letter of the subject: `feat: add feature` not `feat: Add feature`
- **Do not use a period** at the end of the subject: `feat: add feature` not `feat: add feature.`
- **Separate subject from body** with a blank line
- **Wrap body** at 72 characters
- **Explain what and why**, not how
- **Reference issues** in the footer: `Closes #123`, `Fixes #456`
- **Make atomic commits**: one logical change per commit

### ❌ Don't

```
# ❌ Bad - non-descriptive
git commit -m "update code"

# ❌ Bad - missing type
git commit -m "add login page"

# ❌ Bad - invalid type
git commit -m "add(feature): login page"

# ❌ Bad - too many changes in one commit
git commit -m "feat: add login, dashboard, and payment"
```

### ✅ Good

```
git commit -m "feat(auth): add login page with OAuth"
git commit -m "fix(checkout): fix email validation in payment form"
git commit -m "docs: update README with setup instructions"
```

## Tools & Integration

### Commitizen

Tool to help craft semantic commit messages:

```bash
npm install -g commitizen
npm install --save-dev cz-conventional-changelog

# Use it with
git cz
```

### Husky + Commitlint

Automate commit message validation:

```bash
npm install husky commitlint --save-dev

npx husky install
npx husky add .husky/commit-msg 'npx --no -- commitlint --edit "$1"'
```

File: `commitlint.config.js`
```javascript
module.exports = {
	extends: ['@commitlint/config-conventional'],
};
```

### Pre-commit Hook

Validate before committing:

```bash
npm install --save-dev @commitlint/cli
```

### Git Aliases

Create aliases to simplify common commands:

```bash
git config --global alias.com 'commit -m'
git config --global alias.f 'fetch'
git config --global alias.p 'push'
```

## Benefits

### 📊 Automated Changelog

With semantic commit messages, changelogs can be generated automatically:

```markdown
## [1.2.0] - 2024-01-15

### Added
- feat: add login feature with OAuth
- feat(dashboard): add analytics widget

### Fixed
- fix: fix crash when uploading large images
- fix(checkout): fix email validation in payment form

### Changed
- refactor: simplify payroll calculation logic
```

### 🔄 Automated Versioning

Using Semantic Versioning (MAJOR.MINOR.PATCH):

- **MAJOR**: for breaking changes
- **MINOR**: for new backward-compatible features
- **PATCH**: for bug fixes

### 🔍 Better Code Review

Reviewers can more easily understand the intent of changes from clear commit messages.

### 📝 Cleaner History

Commit history becomes more organized and easier to trace:

```bash
git log --oneline
```

### 🔄 Easier Bisecting

Finding the commit that introduced a bug is easier with consistent commit conventions.

## References

- [Conventional Commits](https://www.conventionalcommits.org/)
- [Semantic Versioning](https://semver.org/)
- [Commitizen](http://commitizen.github.io/cz-cli/)
- [Commitlint](https://commitlint.js.org/)

---

**Created to help teams understand and implement Semantic Commit Message effectively.** ✨

