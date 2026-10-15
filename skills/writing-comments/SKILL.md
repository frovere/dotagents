---
name: writing-comments
description: Use when asked to write, draft, revise, leave, or reply to a comment on the user's behalf in a ticket, issue, PR, or external discussion thread. Adapt the message to the recipient's role, the next action, and the destination conversation.
license: MIT
---

Write a comment the recipient can act on, in the user's voice, with claims supported by the available evidence.

## Establish the assignment

Read the requested ticket or PR thread, its relevant replies, and any linked decision that changes the answer. Confirm the exact destination: issue, parent issue, existing comment thread, or PR review thread. Follow repository tracker instructions when resolving an unspecified destination.

Identify the reader, their role in this task, the requested outcome, and whether the user requested a draft, an edit, or publication. Use an explicitly known role first; infer task ownership from the conversation when needed, without treating it as a confirmed job title. Reuse information and authorization already supplied. Ask only when an unresolved choice changes the meaning, recipient, destination, or permitted action.

Read [readers.md](references/readers.md) when adapting a comment to a coworker role or a particular task. Its John/Jane Doe examples are fictional; determine the actual recipient and role from the current request and conversation.

## Choose the comment language

Read the language of the destination ticket, issue, PR, or discussion. Here, **destination thread** means the conversation receiving the comment, not the agent chat. Prefer the human conversation being replied to; use the issue or PR's main prose when no relevant replies exist. Code, identifiers, quoted material, and isolated messages are weaker signals than the ongoing discussion.

An explicit language requested for the comment takes precedence. Otherwise, use the destination conversation's language. If it differs from the agent chat, briefly recommend that language in the agent chat, then continue with it without requiring a separate confirmation. If the user explicitly requested another comment language, preserve that request and mention the destination-language recommendation only when useful.

If the destination is unavailable or its language is unclear, use the user's requested comment language or the agent chat's language as a fallback, and make a material assumption visible. Ask only when the choice would prevent a usable comment.

This language choice applies only to the comment and material authored for it, such as diagram labels or an attachment caption. Keep status updates, explanations, and other conversation with the user in the agent chat's established language. Preserve code, identifiers, and intentional quotations.

## Gather the evidence that changes the message

Check the source needed for the claim: implementation and relevant PR head for a fix; agreed product reply for intended behavior; test output for verification; build or deployment evidence for release availability. Earlier drafts and historical summaries are pointers to inspect, not proof of current state.

Keep implemented, pushed, merged, deployed, automated verification, and manual QA distinct. Include only the distinctions material to this reader's next action. If a required source is unavailable, mark that specific claim as unverified and draft the supported part.

For stacked PRs, identify which PR contains the fix and whether it is present in the PR receiving the reply. For a product follow-up, distinguish an open proposal from an accepted decision and from delivered behavior.

## Compose for the next action

Match tone to the coworker's role, the user's working relationship with them, and the destination conversation. Role determines the useful emphasis; explicit preferences and the thread determine formality and technical depth. When writing on the user's behalf, address the recipient directly and attribute personal choices to the user only when supported by the request or record.

Lead with what the reader needs to know or do. Add the minimum explanation and evidence needed to act. Use steps for testing, a small comparison for a choice, and a direct answer for a review finding. Preserve established domain terms; explain their user-visible consequences when needed.

Use the relevant shape, without forcing headings or empty sections:

- **Retest:** exact build or branch, setup, actions and expected results, then remaining coverage and the requested report.
- **Decision:** concrete situation, recommendation and tradeoff, then the unanswered choice. For several decisions, group a copyable answer template at the end.
- **Implementation handoff:** current behavior, missing work, dependency or owner, and the requested next action.
- **Review reply:** disposition, reason, and the relevant fix or contract evidence. Say where a later stacked PR supplies the fix.
- **Reference update:** one sentence and the relevant link may be enough.

Choose a visual only when it resolves a concrete ambiguity. Read [delivery.md](references/delivery.md) before preparing media: use native diagram rendering when supported, otherwise an available image renderer or authorized drawing integration.

## Deliver

For a draft, return the complete proposed text and identify any unresolved mention, attachment, or evidence. Keep it unpublished.

For authorized publication or editing, read [delivery.md](references/delivery.md), perform the requested action, and verify its result. A request to comment does not itself request an issue status, assignee, description, or thread-resolution change.

Finish with the comment permalink when available and any material delivery limitation. If publication has an uncertain outcome, inspect the destination before retrying to avoid duplicates.

## Completion

The recipient can identify the next action, the supporting evidence, and any limit affecting that action. The draft or published comment matches the requested voice, language, destination, and scope. Published mentions and media have the level of verification reported to the user.
