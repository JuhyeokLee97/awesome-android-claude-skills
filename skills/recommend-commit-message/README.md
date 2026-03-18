# recommend-commit-message

Analyze staged git changes and recommend 2–3 commit messages following Conventional Commits.
Includes **Android-specific path hints** for Clean Architecture layer detection.

## What it does

- Reads `git diff --staged` to understand what changed
- Warns about unstaged changes (without stopping)
- Analyzes recent commit history to match your project's scope and style
- Detects Android stack signals (Compose, Hilt, Room, multi-module) for smarter type hints
- Recommends 2–3 commit message candidates with reasoning
- Generates a commit body when the subject alone is insufficient
- Suggests commit splitting when changes have multiple independent purposes

## Android Path Hints

Automatically suggests the right `type` based on file paths:

| Path pattern | Suggested type |
|--------------|----------------|
| `**/presentation/**` (ViewModel, State) | `feat`, `fix`, `refactor` |
| `**/presentation/**` (Composable, Screen) | `feat`, `design` |
| `**/domain/usecase/**` | `feat`, `refactor` |
| `**/data/repository/**` | `feat`, `fix`, `refactor` |
| `**/data/remote/**` | `feat`, `fix` |
| `**/di/**`, `**/*Module.kt` | `feat`, `refactor`, `chore` |
| `**/designsystem/**`, `**/ui/theme/**` | `design`, `feat` |
| `*.gradle*`, `libs.versions.toml` | `build`, `chore` |
| `**/*Migration*.kt`, `**/migrations/**` | `feat`, `fix`, `chore` |
| `.github/workflows/**`, `.travis.yml`, `.gitlab-ci.yml` | `ci` |
| `*Test.kt`, `*Spec.kt` | `test` |

## Installation

```bash
cp -r . /your-project/.claude/skills/recommend-commit-message/
```

## Usage

```
# Stage your changes first
git add <files>

# English (default)
/recommend-commit-message

# Korean
/recommend-commit-message KOR

# Supported: ENG | KOR | JPN | CHN | ESP | POR | FRA | DEU
```

## Output Example

```
### Analysis Summary
2 files changed — Added token refresh logic to LoginViewModel; updated AuthRepository interface

---

### Candidate 1 ✅ (Recommended)
```
feat(auth): add token refresh logic to LoginViewModel
```
> Why: Presentation layer change introducing new behavior; scope matches module path

---

### Candidate 2
```
feat(login): implement token refresh on session expiry
```
> Why: Alternative scope using feature name instead of module name
```

With `KOR` argument, Analysis Summary, Why explanations, subject lines, and bodies are written in Korean. `type`, `scope`, and format keywords remain English.

## Language

Supports 8 output languages via argument: `ENG` (default), `KOR`, `JPN`, `CHN`, `ESP`, `POR`, `FRA`, `DEU`.

`type`, `scope`, and Conventional Commits format are always English regardless of language setting.
