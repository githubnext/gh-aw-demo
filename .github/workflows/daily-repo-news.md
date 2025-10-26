---
on:
  schedule:
    - cron: "0 16 * * 1-5"  # 8 AM PST (4 PM UTC), weekdays only
  workflow_dispatch:
permissions:
  contents: read
  issues: read
  pull-requests: read
  discussions: read
  actions: read
engine:
  id: copilot
tools:
  github:
    allowed:
      - list_issues
      - list_pull_requests
      - list_commits
      - get_issue
      - pull_request_read
safe-outputs:
  create-discussion:
    title-prefix: "📰 Daily Repo News - "
    category: "General"
timeout_minutes: 10
---

# Daily Repository News Digest

Generate an engaging daily news report for the **${{ github.repository }}** repository.

## Your Task

Gather and summarize activity from the **last 24 hours** including:

1. **Pull Requests**
   - New PRs opened
   - PRs merged
   - PRs with significant activity or discussion

2. **Issues**
   - New issues opened
   - Issues closed or resolved
   - Issues with notable updates

3. **Commits**
   - Significant commits to main branch
   - Notable code changes

## Format

Create a discussion post with:
- 📊 A quick stats summary (X PRs, Y issues, Z commits)
- 🎯 Highlights of the most important activity
- 💬 Any interesting discussions or decisions
- Keep it concise and engaging - team update style

Use emojis and clear formatting to make it scannable and fun to read.

**Note**: If there's no activity in the last 24 hours, create a brief "quiet day" update instead.
