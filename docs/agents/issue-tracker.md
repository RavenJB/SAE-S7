# Issue tracker: GitHub

[GitHub Issues for RavenJB/SAE-S7](https://github.com/RavenJB/SAE-S7/issues) is the source of truth for tickets, including scope, acceptance criteria, assignees, blockers, decisions and closure. Link the relevant mission specs from `spec/` in the issue body.

## GitHub workflow

- **Publish:** Create one issue per work item with `gh issue create --repo RavenJB/SAE-S7 --title "..." --body-file <file>`. Publish blockers first and apply the label requested by the skill.
- **Fetch:** Read the issue and discussion with `gh issue view <number> --repo RavenJB/SAE-S7 --json number,title,body,labels,assignees,state,comments`.
- **List:** Use `gh issue list --repo RavenJB/SAE-S7` with `--state`, `--assignee` or `--label` as needed.
- **Link work:** Use native GitHub sub-issues and dependencies. In `gh` versions without the linking flags, use `gh api`. The `sub_issues` endpoint takes the child's numeric database ID as `sub_issue_id`. The `dependencies/blocked_by` endpoint takes the blocker's numeric database ID as `issue_id`. Get it with `gh api repos/RavenJB/SAE-S7/issues/<number> --jq .id`. If native links are unavailable, add `Part of #<parent>` or `Blocked by: #<blocker>` to the issue body. An issue is ready to start when its blockers are closed. [Sub-issues API](https://docs.github.com/en/rest/issues/sub-issues) · [Dependencies API](https://docs.github.com/en/rest/issues/issue-dependencies)
- **Close:** Link the PR with `Closes #<number>` when its merge to the default branch completes the issue. For work without a PR, close the issue after recording the acceptance evidence.

**PRs as a request surface: no.**

## Trello visual tracking

Use the [SAE S7 board](https://trello.com/b/Or6FywJJ/sae-s7) with four lists: `À faire`, `En cours`, `À valider`, `Terminé`.

- Create the GitHub issue first. Add one Trello card named `#<number> <title>` with the GitHub issue URL. Reuse an existing card for the same issue.
- Move the card as work starts, goes for review or is accepted. Move it to `Terminé` once the GitHub issue is closed. Keep detailed ticket updates on GitHub.
- If Trello is unavailable, publish and update tickets on GitHub and catch up on the board when access returns.
