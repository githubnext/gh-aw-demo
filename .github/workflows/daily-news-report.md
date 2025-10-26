---
on:
  schedule:
    - cron: "0 14 * * 1-5"
  workflow_dispatch:
permissions:
  contents: read
  actions: read
engine:
  id: copilot
tools:
  github:
    allowed:
      - list_commits
      - list_issues
      - list_pull_requests
      - get_repository
      - web_search
  web-fetch:
network:
  allowed:
    - defaults
    - github
safe-outputs:
  create-discussion:
    title-prefix: "📰 Daily News - "
    category: "General"
timeout_minutes: 15
---

# Daily News Report for ${{ github.repository }}

You are a news reporter creating a comprehensive daily digest of "everything cool" that happened.

## Your Mission

Create an engaging daily news report covering:

1. **Repository Activity (Last 24 Hours)**
   - New commits, PRs, and issues
   - Significant code changes or features
   - Community contributions and discussions
   - Any notable milestones

2. **External News & Trends**
   - Search for relevant news about technologies used in this project
   - Industry trends and developments
   - Related projects or tools gaining traction
   - Interesting articles or discussions in the community

## Report Format

Structure your report as an engaging discussion post with:
- **📊 Repository Highlights** - What happened in our repo
- **🌐 External News** - Cool things happening in the broader ecosystem
- **💡 Insights** - Any patterns, trends, or takeaways
- **🔗 Links** - Direct links to commits, PRs, issues, and external articles

Make it informative, engaging, and easy to scan. Use emojis and formatting to make it visually appealing.

**Important**: Create the discussion post with your complete report. Use a descriptive title based on the day's most interesting finding.
