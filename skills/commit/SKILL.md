---
name: commit
description: Use when creating, amending, or drafting git commits.
license: MIT
---

# Commit

Create atomic commits for the requested changes. Only commit. Never push unless explicitly instructed.

For a draft-only request, inspect the changes and return the proposed message
without staging or committing anything.

## Atomic commits

Organize commits by purpose, not chronology.

Each commit must:

- contain one coherent, irreducible change;
- be as small as possible while remaining valid on its own;
- include the tests, documentation, migrations, generated files, and dependency metadata required by that change;
- build and pass its relevant checks on its own;
- have a purpose clear from its message alone.

Split independent purposes. Keep interdependent changes together even when they span several files. Do not split by file count.

Do not create checkpoint commits such as `wip`, `fix typo`, or `more fixes`.
When a change completes an existing local commit, fold it into that commit.
If this applies, read [`references/rewrite-local-history.md`](references/rewrite-local-history.md) before changing history.

## Commit messages

Use:

`<type>(<scope>): <summary>`

- `type` is required. Use `feat` for features and `fix` for bug fixes. 
  Other common types are `build`, `ci`, `docs`, `refactor`, `chore`, `test`, and `perf`.
- `scope` is optional. Infer a short noun from the affected area and match scopes used by recent commits when the repository has a consistent vocabulary.
- `summary` is required. Uncapitalize it, use the imperative mood, keep it at most 72 characters, and omit the trailing period.
- A body is optional. Separate it from the subject with a blank line and wrap it at 72 characters. Keep it concise.
- Use the subject for what changed. Use the body for motivation, constraints, or a rejected alternative that the diff cannot explain.
- Omit implementation narration, breaking-change markers, footers, and sign-offs.
- Never include secrets, PII, customer or organization names, user emails, or
  private ticket contents. Describe the technical symptom instead.

## Process

### 1. Establish the boundary

Treat caller-provided paths or globs as a hard boundary. Treat other arguments as guidance for commit grouping and wording.

Inspect:

```sh
git status --short
git diff
git diff --cached
git log --oneline --decorate -20
```

When choosing a scope, inspect the repository's recent subject vocabulary:

```sh
git log -n 50 --pretty=format:%s
```

Limit diff commands to caller-provided paths when present.

Record which changes were already staged. Preserve that boundary unless staged
and unstaged hunks serve the same purpose. Never silently add unstaged work to
a pre-staged unit.

Account for every staged and unstaged change inside the boundary. Leave changes
outside it untouched. Ask before including a file or hunk whose ownership is
unclear.

### 2. Plan the history

Group changes by purpose.

For each proposed commit, identify:

1. its single purpose;
2. the files and hunks that serve that purpose;
3. its required tests and supporting artifacts;
4. whether it is new work or belongs to an existing commit;
5. the checks that prove the commit works on its own.

Use `git show`, `git log -- <path>`, and `git blame` when history can clarify where a change belongs. Ask when it remains ambiguous. Do not guess.

A change belongs in an existing commit when it corrects, completes, tests, or documents that commit's purpose. A distinct purpose becomes a new commit.

### 3. Stage one unit

Use path staging when whole files belong together:

```sh
git add <paths>
```

Use patch staging when a file contains more than one purpose:

```sh
git add -p <paths>
```

Review the exact payload:

```sh
git diff --cached
```

If changes were already staged, review them before adding anything else. 
A pre-existing index is a candidate commit, not permission to stage the rest.

The staged diff must contain one planned unit and all artifacts required by that unit. 
Unstage and regroup it if the purpose needs an unrelated clause to describe.

### 4. Verify and commit

Run the relevant checks against the isolated commit, not merely against the final working tree. 
Temporarily stash remaining work or use another worktree when necessary to test the commit by itself.

Commit with:

```sh
git commit -m "<subject>"
```

Use separate `-m` arguments for message paragraphs. Never encode paragraph
breaks as literal `\n` sequences.

When a body is needed:

```sh
git commit -m "<subject>" -m "<body>"
```

Repeat the planning, staging, and verification steps for each independent unit.

### 5. Audit the result

Inspect:

```sh
git status --short
git log --oneline --decorate -10
git show --stat HEAD
```

Finish only when:

- every requested change is committed exactly once;
- each resulting commit has one purpose;
- each commit includes its required supporting artifacts;
- each commit passes its relevant checks on its own;
- no unrelated work was committed;
- the worktree contains only intentionally uncommitted changes;
- no commit was pushed.
