# Word Weasel

**Write better PRs and commit messages.**

Word Weasel is a GitHub Action that helps you write better pull request titles and descriptions by analyzing them for clarity, conciseness, and overall quality.
It provides suggestions to improve your writing, ensuring that your PRs are easy to understand and review.

## Usage

```yaml
# .github/workflows/pull-rqeuest.yml
# Write better PRs and commit messages
name: "Word Weasel"
on:
  pull_request:
    types:
      - opened
      - edited
      - reopened
      # Optional, if you want to include the check in branch protection rules
      # - synchronize
jobs:
  pr-title:
    name: "PR Title"
    runs-on: ubuntu-latest
    timeout-minutes: 1
    if: ${{ github.actor != 'dependabot[bot]' }}
    steps:
      - uses: codingjoe/word-weasel@v1
        with:
          text: ${{ github.event.pull_request.title }}
  pr-body:
    name: "PR Body"
    runs-on: ubuntu-latest
    timeout-minutes: 1
    if: ${{ github.actor != 'dependabot[bot]' }}
    steps:
      - uses: codingjoe/word-weasel@v1
        with:
          text: ${{ github.event.pull_request.body }}
```
