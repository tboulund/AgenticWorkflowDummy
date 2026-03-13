# Agentic Workflows

This repository uses GitHub Copilot agentic workflows to automate routine maintenance tasks.

## daily-repo-status

**Source:** `.github/workflows/daily-repo-status.md`

Generates a daily status report for the repository and publishes it as a GitHub issue.

### Schedule

Runs daily via a scheduled cron trigger, or on demand via `workflow_dispatch`.

### What it does

1. Gathers recent repository activity — issues, pull requests, discussions, releases, and code changes.
2. Analyzes progress, highlights activity, and surfaces recommendations for maintainers.
3. Creates a new GitHub issue titled `[repo-status] <summary>` with the report.
4. Closes any older issues with the same `[repo-status]` prefix to avoid clutter.

### Output

A GitHub issue labeled `report` and `daily-status` containing:

- Recent activity summary
- Progress tracking and goal reminders
- Project status and actionable next steps

---

## daily-doc-updater

**Source:** `.github/workflows/daily-doc-updater.md`

Scans merged pull requests and recent commits from the last 24 hours, identifies undocumented changes, and opens a pull request with documentation updates.

### Schedule

Runs daily at 06:00 UTC, or on demand via `workflow_dispatch`.

### What it does

1. Searches for pull requests merged in the last 24 hours.
2. Reviews each PR's diff to identify new, modified, or removed features.
3. Locates the relevant documentation files and updates them accordingly.
4. Commits the changes to a new branch and opens a pull request for review.

### Output

A pull request labeled `documentation` and `automation`, with title prefix `[docs]`, containing:

- Updates to documentation files reflecting the detected changes
- A description listing the features documented and the PRs that introduced them
- Assigned to `copilot` for review
