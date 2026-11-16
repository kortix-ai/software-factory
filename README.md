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
Ask all your questions in one message. Never print a secret value.
```

Your agent reads this repository, looks at yours, and writes your own Kortix
workspace repository beside your code: `kortix.yaml`, `agents/` and `skills/`.
Your code repository gets no Kortix file; the agents reach it on GitHub. It
runs on your Claude or Codex plan, or any API key.

## How it works

```
signal ──► source trigger ──► ticket (your tracker) ──► intake ──► worker ──► pull request ──► you merge
```

| Piece | Where |
| --- | --- |
| The agent: one `factory` agent, its roles are skills | `software-factory.yaml`, `agents/factory.md` |
| The contract: tickets, states, markers, caps, PR evidence | `skills/software-factory/SKILL.md` |
| Ticket stores: GitHub Issues, Linear, Jira, Asana, a JSON file | `…/references/stores/` |
| Sources: GitHub issues, tests, Slack, errors, logs, database, feedback, security | `…/references/sources/` |
| Loops: intake, worker, review, merge gate, feedback, groom, eval | `…/references/execution/` |
| Settings: store, sources, caps, merge policy, models, identity | `factory.json` |
| The dev environment the agents run | `Dockerfile`, `skills/dev-environment/` |
| What an agent asks and checks when it adapts this | `ADAPTING.md` |

## Defaults

- Only GitHub issues labelled `kortix` and the nightly tests start work.
- At most 3 workers at once and 5 new tickets per source per day.
- A person merges every pull request (`merge.policy: hold`).
- The factory acts as its own GitHub account, never as you.

To remove it, delete `software-factory.yaml`, `factory.json`, `agents/factory.md`,
`skills/software-factory/` and its line under `imports:`.

Kortix is open source: https://github.com/kortix-ai/suna
