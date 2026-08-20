# dotagents

A collection of agent skills.

## Install

Install the skills with:

```sh
npx skills add frovere/dotagents
```

The repository currently includes the `commit` skill for creating atomic Git commits with consistent messages.

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
