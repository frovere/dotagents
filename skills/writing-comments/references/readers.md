# Reader and task

Adapt to the responsibility the person owns in this conversation. A coworker can be deciding product behavior in one thread and reproducing a bug in another. John Doe and Jane Doe below are fictional examples, not saved coworker profiles.

## Match tone to role and relationship

Use an explicitly stated role or responsibility when available. Otherwise infer only the responsibility demonstrated by this thread. Formal job titles, seniority, authority, and technical fluency require evidence; a role does not establish all four.

| Role in this task | Tone and emphasis | Useful response to request |
|---|---|---|
| Product or design | Conversational and concrete; explain user-visible behavior, recommendation, and tradeoffs | Choose or confirm the remaining behavior |
| QA or testing | Collaborative and precise; give setup, steps, expected results, and coverage limits | Retest and report the observed result |
| Engineering or technical reviewer | Direct and evidence-based; explain the relevant contract, cause, fix, or dependency | Review a finding, implement a change, or confirm compatibility |
| Lead or delivery coordinator | Concise and outcome-focused; state readiness, impact, blocker, owner, and next step | Prioritize, coordinate, or decide the unresolved dependency |

These are starting points, not fixed levels of formality or technical knowledge. Follow the established conversation and the user's stated relationship. A familiar peer thread can be casual while remaining precise. A manager's title alone does not justify a formal tone. Mixed audiences need a shared outcome first, followed by separate actions for the people who own them.

When adapting a comment, preserve facts and uncertainty; change emphasis, explanation, and the requested response. Prefer the current request over an established person-specific preference when they conflict.

## QA: make retesting executable

For a retest request to John Doe, give the exact build or branch, how to obtain the current changes, relevant environment or device coverage, reproducible steps, and expected behavior.

Explain operational timing in terms the tester can use. If a cache affects the result, verify the current duration and refresh trigger before prescribing a wait.

Separate an intended behavior from a regression by linking the accepted product decision and giving a short example. State whether the evidence is automated, manual, or still pending.

## Product: make the choice answerable

For a decision request to Jane Doe, write directly from the user to the recipient in the requested language. Explain what the end user experiences, provide a recommendation and tradeoff, then identify the choice that remains.

For multiple questions, group a copyable answer template at the end, such as `Q1: A`. Use visual evidence when it makes the choice clearer. Let the thread determine whether a casual greeting fits.

For a follow-up, show what changed since the last agreed decision and ask for confirmation only if a decision is actually open. Record an accepted decision as accepted.

## Release or cross-team handoff: make readiness precise

For a build handoff to John Doe, provide the installable artifact, relevant changes in related systems, short test steps, and remaining validation. Keep automated E2E and manual QA distinct.

Identify ownership from the current task. Keep service delivery, client implementation, and product agreement distinct when they have different owners. State which coordination or publication step is pending.

## Developer or PR reviewer: answer the technical concern

Use the relevant contract, code, fix commit, or PR link. For a valid finding, explain the resulting behavior and material verification. For an intentional behavior or already-fixed finding, give the reason and supporting reference.

Read the finding against the current code and accepted contract before replying, including bot findings. Reply in the existing review thread when that is the requested surface. Resolving that thread is a separate action.

## Cross-team clarification: seek shared understanding

When evidence leaves room for misunderstanding, use a curious, collaborative tone. State what you read or observed, explain the difference, and ask for confirmation. Keep verified facts direct; uncertainty belongs to the unresolved claim. Frame the request around reaching a shared contract rather than assigning blame or presuming work is missing.

For example: “Jane Doe, el requisito menciona un país de residencia, pero no lo veo en la respuesta documentada. ¿Ese dato llega por otro servicio o estoy interpretando mal el contrato?”

For several gaps, keep each question and its supporting evidence together; use separate comments when requested. Direct product-scope decisions and technical-contract questions to the people responsible for them. If a scope change is needed, identify what should be reflected in the requirements and mockup so implementation and QA share the same reference.

## Unknown reader

Use the task and thread to choose the amount of detail. A neutral, direct comment is sufficient when personal preferences are unknown. Clarify identity only when it affects delivery, such as an ambiguous account mention.

## Maintaining reader guidance

Add an actual coworker's preference only from an explicit instruction or a repeated, source-backed correction. Record its scope and source in the project's designated context when authorized. Keep reusable examples fictional and resolve account identifiers through the destination's directory. Treat one task-specific request as an example, not a permanent fact about the person.
