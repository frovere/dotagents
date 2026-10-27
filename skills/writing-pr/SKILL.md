---
name: writing-pr
description: PR writing — use when drafting or editing a pull request title or body, including when another skill files the PR.
---

# Writing a PR title and body

Explain the problem briefly, show the final effect, and include only the evidence needed to review it confidently. Drafting or editing text does not itself authorize publishing it.

## Context

Read the original request, the final aggregate diff against the intended target branch, and any repository PR template or instructions. Look at recently merged PRs and Git history for title and tone conventions. When a `CONTEXT.md` exists, read relevant domain definitions and preserve that shared terminology; simplify the explanation around it.

Only the final aggregate squash-merge result matters for commentary. Describe what changes relative to the target branch, rather than intermediate commits, abandoned refactors, or how much smaller the PR became during development.

## Title

PR titles usually become commit messages, so follow the repository's title conventions. Prefer a concise, human-readable title that explains why the change matters:

BAD
> ❌ perf (server): negotiate permessage-deflate on the websocket

GOOD
> ✔︎ perf (server): cut websocket frame size by 70%+ with gzipping

Use quantitative claims only when supported by measurements.

## Body

Open with a simple explanation of the problem based on the user's original prompt, then briefly explain the solution. Prefer a short opening and bullets for supporting text over an implementation inventory:

BAD
> ❌ Removed implicit workspace carry-over from every "new thread" entry point (cmd+n / cmd+shift to, sidebar v1/v2 buttons, command palette). New threads inherit only the project from context; branch, worktree, and env mode always come from the configured defaults. Deleted buildContextualThreadOptions, startNewThreadInProjectFromContext, and the v1 sidebar's seed-context machinery.

GOOD
> ✔︎ My "new worktree" default was ignored when starting new threads on existing worktrees.
> Super unintuitive. Now your preferences always apply.

Match the repository's tone; the example illustrates problem-first writing, not a required level of informality.

## Evidence by change type

Choose the format that explains the change most directly. A small fix may need only a few sentences.

- **Visual changes:** when the change produces an observable UI difference, show a before/after table with uploaded images or videos. This includes indirect changes with visible effects. If media is unavailable, state the limitation rather than inventing links or attachments.
- **Benchmarks:** show a before/after table with the target branch as baseline and the final PR as candidate. Include units and measurement conditions so the comparison is meaningful. If measurements are unavailable, disclose the gap and keep performance claims unquantified.
- **API or usage changes:** use minimal code samples showing the new behavior or before/after usage. Internal snippets and code references are useful when they explain a non-obvious mechanism.
- **Complex flow or state changes:** use a focused Mermaid codeblock diagram when it explains relationships more clearly than prose.
- **High-risk or wide-scope changes:** expand only as needed to explain the design, compatibility, rollout, and rollback implications. A technical-blog-style explanation can be appropriate when context, storytelling, snippets, or diagrams materially help review.

**Attachments:** when drafting or publishing a PR body or comment with local images or videos, read [GitHub CLI attachments](references/attachments.md) for Markdown placement and `--attach` upload instructions.

Omit routine "I ran tests" boilerplate. Include verification evidence, failed checks, or unverified behavior when material to the reviewer's decision, or when the repository template requires it.

## Completion

The title and body accurately describe the final diff against the intended base, explain why it matters, include evidence appropriate to the change, and disclose material limitations. Claims and attachments are verifiable; intermediate development history is omitted.
