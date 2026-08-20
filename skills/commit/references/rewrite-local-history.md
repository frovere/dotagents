# Rewrite local history

Use this process when a change belongs in an existing commit.

## Establish the frozen boundary

Rewrite only local history. Treat commits reachable from a shared or
remote-tracking branch as frozen.

Choose the boundary in this order:

1. a base explicitly supplied by the user;
2. the current branch's upstream;
3. the base branch reported by an existing pull request;
4. user clarification.

Inspect an upstream with:

```sh
git rev-parse --abbrev-ref --symbolic-full-name '@{upstream}'
```

List the rewrite candidates:

```sh
git log --oneline <base>..HEAD
```

Also check each proposed target against remote-tracking branches:

```sh
git branch -r --contains <target>
```

The target is eligible only when it appears in `<base>..HEAD` and no remote-tracking branch contains it. 
If remote state is missing, stale, or ambiguous, ask before rewriting. 
Never guess the base or rewrite eligibility.

Never rewrite a published commit without explicit user instruction.

## Choose the route

Use the simplest route that matches the change:

| Situation | Route |
| --- | --- |
| The change belongs in `HEAD` | Amend `HEAD` |
| An already-written change belongs in older local commits | Fixup and autosquash |
| The change must be authored in an older commit's context | Edit during rebase |
| Only an existing message needs correction | Reword during rebase |

## Amend `HEAD`

Confirm that the change belongs in `HEAD`:

```sh
git show --stat HEAD
git show HEAD
```

Stage only the matching change and inspect it:

```sh
git add <paths>
git diff --cached
```

Keep the message when it still describes the complete commit:

```sh
git commit --amend --no-edit
```

Use `git commit --amend` without `--no-edit` when the commit's purpose or scope
changed.

## Fixup older commits

Use fixups when working-tree changes already exist and belong in one or more
older local commits.

For each target:

1. Stage only the hunks belonging to that target.
2. Inspect `git diff --cached`.
3. Create the fixup:

```sh
git commit --fixup <target>
```

Repeat until every intended change has one target. Inspect the resulting `fixup!` commits and verify their mappings before rewriting.

A rebase needs a clean working tree. Stash unrelated tracked and untracked work instead of creating a temporary checkpoint commit:

```sh
git stash push -u -m "before atomic commit rewrite"
```

Autosquash from the parent of the oldest target:

```sh
GIT_SEQUENCE_EDITOR=true git rebase -i --autosquash <oldest-target>^
```

Using the oldest target avoids guessing the branch base for the rebase range.

Restore the stash after the rewrite:

```sh
git stash pop
```

If restoration conflicts, stop and resolve it. Git retains the stash when the pop does not complete cleanly.

## Edit an older commit in context

Use an edit stop when the change must be authored or tested against the older commit's original tree.

Start from the target's parent:

```sh
git rebase -i <target>^
```

Change the target action from `pick` to `edit`. When Git stops:

1. make the change;
2. stage only that change;
3. run the relevant checks;
4. amend the commit;
5. continue the rebase.

```sh
git add <paths>
git commit --amend
git rebase --continue
```

## Reword an older commit

Start an interactive rebase from the target's parent:

```sh
git rebase -i <target>^
```

Change the target action from `pick` to `reword`, then write the corrected message using the main skill's message rules.

## Conflicts

Changing an older commit replays every descendant. Conflicts near lines touched by later commits are expected.

When a conflict occurs, follow the `resolving-merge-conflicts` skill if available. 
Continue only after resolving every unmerged path and verifying the staged resolution.

## Verify the rewrite

Inspect:

```sh
git status --short
git log --oneline --decorate <base>..HEAD
```

Run the relevant checks against every rewritten commit. Finish only when:

- every rewritten commit remains atomic;
- every rewritten commit works on its own;
- each change appears in its intended target;
- no `fixup!` commits remain;
- unrelated stashed work has been restored;
- no frozen commit was rewritten.
