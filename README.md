# GitHub Workflows Starter Kit

Gold-standard CI/CD templates for solo developers. Copy any workflow into your repo's `.github/workflows/` and it just works.

## Quick Start

```bash
# Copy a workflow into your project
mkdir -p .github/workflows
curl -o .github/workflows/ci-typescript.yml \
  https://raw.githubusercontent.com/Know-Kname/github-workflows-starterkit/main/workflows/ci-typescript.yml
```

Or clone the whole repo and cherry-pick what you need.

## Available Workflows

| Workflow | File | Triggers | What it does |
|---|---|---|---|
| TypeScript CI | `ci-typescript.yml` | Push to main, PRs | Lint (ESLint), type-check, build, test |
| Python CI | `ci-python.yml` | Push to main, PRs | Lint (Ruff), type-check (mypy), test (pytest) |
| Security Scan | `security-scan.yml` | Push to main, weekly schedule | CodeQL analysis, dependency audit |
| Vercel Preview | `deploy-vercel-preview.yml` | PRs | Deploy preview to Vercel |
| Vercel Production | `deploy-vercel-production.yml` | Push to main | Deploy production to Vercel |
| PR Checks | `pr-checks.yml` | PRs | Label by path, warn on large PRs |
| Stale Bot | `stale-bot.yml` | Daily schedule | Auto-close stale issues/PRs after 30 days |

## Templates

| Template | File | Purpose |
|---|---|---|
| Bug Report | `templates/ISSUE_TEMPLATE/bug_report.md` | Structured bug reports |
| Feature Request | `templates/ISSUE_TEMPLATE/feature_request.md` | Feature proposals |
| Pull Request | `templates/PULL_REQUEST_TEMPLATE.md` | PR description checklist |
| Security Policy | `templates/SECURITY.md` | Vulnerability reporting |
| Contributing Guide | `templates/CONTRIBUTING.md` | How to contribute |

## How to Use

### Step 1: Copy the workflow file

Copy the `.yml` file you want into your repo at `.github/workflows/`.

### Step 2: Add required secrets (if needed)

Some workflows need secrets configured in your repo settings:

| Workflow | Required Secrets |
|---|---|
| Vercel Preview | `VERCEL_TOKEN`, `VERCEL_ORG_ID`, `VERCEL_PROJECT_ID` |
| Vercel Production | `VERCEL_TOKEN`, `VERCEL_ORG_ID`, `VERCEL_PROJECT_ID` |

Go to **Settings → Secrets and variables → Actions → New repository secret** to add them.

### Step 3: Copy templates (optional)

Copy the `templates/` contents into your repo's `.github/` folder:

```bash
cp -r templates/ISSUE_TEMPLATE .github/ISSUE_TEMPLATE
cp templates/PULL_REQUEST_TEMPLATE.md .github/PULL_REQUEST_TEMPLATE.md
cp templates/SECURITY.md SECURITY.md
cp templates/CONTRIBUTING.md CONTRIBUTING.md
```

### Step 4: Push and watch it work

Commit, push, and check the **Actions** tab in your repo.

## Customization

Each workflow has comments explaining what to change. Common customizations:

- **Node version**: Change the `node-version` matrix (default: `[20, 22]`)
- **Python version**: Change the `python-version` matrix (default: `["3.11", "3.12"]`)
- **Stale days**: Change `days-before-stale` in `stale-bot.yml`
- **PR size threshold**: Change the line count in `pr-checks.yml`

## Recommended Branch Protection Rules

For your `main` branch, enable these in **Settings → Branches → Branch protection rules**:

1. **Require a pull request before merging**
2. **Require status checks to pass before merging** (select your CI workflow)
3. **Require branches to be up to date before merging**
4. **Do not allow bypassing the above settings** (even for admins)

## License

MIT - Use these workflows however you want.
