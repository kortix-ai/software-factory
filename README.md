# Kortix Software Factory

A reference for one Kortix loop: agents that turn issues, failing tests,
production errors, database anomalies, Slack threads and customer feedback into
tickets, then build each ticket into a verified pull request, 24/7.

This repository is meant to be **read and adapted**, not copied as is.

## Add it to your repository

Paste this into Claude Code, Codex or Cursor in your repository:

```text
Add a Kortix software factory to this repository with me.
Read https://github.com/kortix-ai/software-factory and adapt it to this repository.
Set it up with the Kortix CLI, following https://kortix.com/setup.md step by step.
Ask me before each decision. Never print a secret value.
```

Your agent reads this repository, looks at yours, and writes your own
`kortix.yaml` and `.kortix/` folder. It runs on your Claude or Codex plan, or
any API key.

## How it works

```
signal ──► source trigger ──► ticket (your tracker) ──► intake ──► worker ──► pull request ──► you merge
```

| Piece | Where |
| --- | --- |
| The agent: one `factory` agent, its roles are skills | `.kortix/software-factory/factory.yaml`, `agents/factory.md` |
| The contract: tickets, states, markers, caps, PR evidence | `.kortix/software-factory/skills/software-factory/SKILL.md` |
| Ticket stores: GitHub Issues, Linear, Jira, Asana, a JSON file | `…/references/stores/` |
| Sources: GitHub issues, tests, Slack, errors, logs, database, feedback, security | `…/references/sources/` |
| Loops: intake, worker, review, merge gate, feedback, groom, eval | `…/references/execution/` |
| Settings: store, sources, caps, merge policy, models, identity | `.kortix/software-factory/factory.json` |
| The dev environment the agents run | `.kortix/sandbox/Dockerfile`, `.kortix/skills/dev-environment/` |
| What an agent asks and checks when it adapts this | `ADAPTING.md` |

## Defaults

- Only GitHub issues labelled `kortix` and the nightly tests start work.
- At most 3 workers at once and 5 new tickets per source per day.
- A person merges every pull request (`merge.policy: hold`).
- The factory acts as its own GitHub account, never as you.

Delete `.kortix/software-factory/` and its line under `imports:` to remove it.

Kortix is open source: https://github.com/kortix-ai/suna
