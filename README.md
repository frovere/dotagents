# dotagents

A collection of agent skills.

## Install

Install the skills with:

```sh
npx skills add frovere/dotagents
```

Available skills:

- [`commit`](skills/commit/SKILL.md): create atomic Git commits with consistent messages.
- [`file-pr`](skills/file-pr/SKILL.md): file a concise pull request.
- [`writing-comments`](skills/writing-comments/SKILL.md): draft and publish comments on your behalf, matching the recipient's role, the destination conversation's language, and the available delivery capabilities.
- [`writing-pr`](skills/writing-pr/SKILL.md): write pull request titles and bodies with clear context and review evidence.

## Attribution

The `commit` skill is based on the original `commit` skill in
[mitsuhiko/agent-stuff](https://github.com/mitsuhiko/agent-stuff). It also
draws from:

- the `commit` skill in [getsentry/skills](https://github.com/getsentry/skills)
  for draft-only behavior and commit-message guardrails against sensitive data
  and literal `\n` paragraph breaks;
- the `maintain-atomic-commits` skill in
  [paulinevos/claude-stuff](https://github.com/paulinevos/claude-stuff) for the
  atomic commit and local history rewrite workflow.

## License

[MIT](LICENSE)
