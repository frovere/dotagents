---
name: file-pr
description: File a concise pull request. Use when the user asks to file, open, or create a PR.
---

# File PR

## 1. Establish the review scope

Before filing, check whether a PR for this branch already exists. Identify the source branch, repository, and intended target branch from the request, existing PR, and repository or stack configuration. Use the stack parent for a stacked PR; otherwise use the repository's configured default when no other target is specified. Resolve conflicting evidence before publishing.

Review the final aggregate diff locally against the intended target branch to make sure its contents match the goal. Inspect both the diff and commit range; account for unrelated changes before proceeding.

This step is complete when the source, target, existing-PR status, and review scope are known.

## 2. Prepare the title and body

Read and apply [writing-pr](../writing-pr/SKILL.md), the shared source for title conventions, problem-first descriptions, evidence, and completion criteria. Honor the repository's PR template and instructions.

This step is complete when the draft meets writing-pr's completion criterion.

## 3. Publish

Create the PR against the established target branch. If one already exists, reuse it rather than creating a duplicate; update its title or body only within the user's requested scope. Push required commits when authorized; report any permission or remote blocker.

Verify the published PR's source, target, title, and body. Return its URL and disclose any incomplete publication step. A prepared draft alone is not a filed PR.
