# GitHub Actions Workflows

## Auto Merge Main into PR

**File:** `auto-merge-main.yml`

This workflow automatically merges the latest changes from the `main` branch into pull request branches.

### When it runs:
- When a pull request is **opened**
- When new commits are **pushed** to an existing pull request (synchronize)
- When a pull request is **reopened**

### What it does:
1. Checks if the PR is from the same repository (not a fork)
2. Checks if the last commit was made by the bot (to prevent infinite loops)
3. Checks out the PR branch
4. Fetches the latest `main` branch
5. Attempts to merge `main` into the PR branch
6. Pushes the merged changes back to the PR branch

### Important Notes:
- **Fork PRs:** This workflow only runs for PRs from branches in the same repository. For PRs from forks, students will need to manually sync with the main branch.
- **Merge conflicts:** If there are merge conflicts, the workflow will fail with an error message. You'll need to resolve conflicts manually.
- **Infinite loop prevention:** The workflow checks if the last commit was made by `github-actions[bot]` to prevent triggering itself repeatedly.
- The workflow uses `github-actions[bot]` as the committer for automatic merges.

### Why this is useful:
This helps keep student PR branches up-to-date with the main repository, reducing merge conflicts when multiple students are submitting their diagnostics simultaneously. Students working on branches in the main repository will automatically get updates from main, while fork-based PRs will need manual syncing.
