# Semantic Release Production CI/CD Pipeline

This repository demonstrates an automated CI/CD pipeline for a production-ready Node.js application using GitHub Actions, Semantic Versioning, and custom changelog generation. It supports automatic version bumps, GitHub release tagging, and a unified changelog that includes commits from both `prod` and `uat` branches.

---

## Key Features

-  **Semantic Versioning** using `semantic-release`
-  **Automated Production Releases** on `prod` branch
-  **Custom Release Rules** based on commit types
-  **CHANGELOG.md** generation for each release
-  **UNIFIED_CHANGELOG.md** script to merge logs across branches
-  **Manual and Triggered Release Support** via `workflow_dispatch`

---

##  Workflow Overview

###  GitHub Actions: `Production Release`

Triggered when:
- Code is pushed to the `prod` branch
- Manually via GitHub Actions UI

**Steps:**

1. **Checkout Code**
2. **Set Up Node.js**
3. **Install Dependencies**
4. **Run Semantic Release**
5. **Generate Unified Changelog**
6. **Push `UNIFIED_CHANGELOG.md` to GitHub**

###  Semantic Release Configuration (`.releaserc.json`)

- Applies to `prod` branch
- Custom `releaseRules` defined for commit types like `feat`, `fix`, `refactor`, `security`, etc.
- Custom `tagFormat`: `v1.2.3-prod`
- Plugins used:
  - `@semantic-release/commit-analyzer`
  - `@semantic-release/release-notes-generator`
  - `@semantic-release/changelog`
  - `@semantic-release/npm` (skip publish)
  - `@semantic-release/git`
  - `@semantic-release/github`

---

##  Commit Guidelines (Conventional Commits)

Use these formats to influence release versions:

| Commit Type | Release Level | Description                  |
|-------------|---------------|------------------------------|
| `feat`      | Minor         | New feature                  |
| `fix`       | Patch         | Bug fix                      |
| `chore`     | Patch         | Maintenance/infra changes    |
| `refactor`  | Patch         | Code refactor                |
| `style`     | Patch         | Code style/formatting        |
| `ci`        | Patch         | CI/CD pipeline changes       |
| `test`      | Patch         | Unit or integration tests    |
| `docs`      | Patch         | Documentation changes        |
| `perf`      | Patch         | Performance improvements     |
| `security`  | Minor         | Security fixes               |
| `BREAKING CHANGE` | Major   | Breaking API/interface change|

---

## Changelog Strategy

### 🔹 `CHANGELOG.md`

- Generated and updated automatically by `semantic-release`
- Includes versioned releases from `prod` only

### 🔹 `UNIFIED_CHANGELOG.md`

- Generated using the `mergechangelog.js` script
- Aggregates commits from `prod` and `uat`
- Categorized by:
  -  Date
  -  Branch
  -  Version
  -  Commit type

---

## Scripts

### `mergechangelog.js`

- Parses commit history and semantic tags
- Categorizes and formats commits across branches
- Generates a unified view of the project’s evolution

### Example Output Structure

<img width="1365" height="582" alt="Screenshot from 2025-07-25 18-23-35" src="https://github.com/user-attachments/assets/c0e244de-1a89-4a6d-83ff-23536bfc4688" />

<img width="1365" height="620" alt="Screenshot from 2025-07-28 11-53-22" src="https://github.com/user-attachments/assets/91f88b82-a7fa-490e-a7a1-ac39827adb17" />

---

##  Project Setup (sample)

Your `package.json` already includes:

- `semantic-release` and its plugins
- `conventional-changelog-angular` for formatting
- Custom scripts for unified changelog generation

---

##  Secrets Required

In GitHub → Settings → Secrets:

| Secret Name      | Description                      |
|------------------|----------------------------------|
| `GH_TOKEN`       | GitHub token for commit/push     |

---

##  Maintainer

**Sweta Gupta**

> Feel free to this repo and fork it if you'd like to create your own versioning system.

---🔖

## Tags

`semantic-release` `github-actions` `changelog` `prod-pipeline` `versioning` `ci-cd` `nodejs`

