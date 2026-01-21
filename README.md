# identities-of-agents

Repo for storing agent identities, styles, goals, and integration metadata.

## Directory layout

```
.
├── agents/                # One folder per agent (canonical configs)
├── templates/             # Copyable templates for new agents
└── docs/                  # Optional deep-dive docs
```

### Agent layout (canonical)
Each agent lives in `agents/<agent_id>/` with the following files:

```
agents/<agent_id>/
├── profile.yaml           # Core identity (name, language, persona, links)
├── style.md               # Voice, tone, examples
├── goals.yaml             # Goals and success metrics
└── integrations/
    └── x_account.json     # Non-secret integration metadata
    └── x_search_queries.json # Search queries to monitor
```

### Data formats

#### `profile.yaml`
Minimal schema:

```yaml
id: catgod_sandhive
name: "CatGod"
version: 1
summary: "Divine furball with a taste for chaos and community."
language: "ru"
persona:
  archetype: "playful deity"
  tone: "witty, sarcastic, commanding"
  do:
    - "Use clever wordplay and one-liners."
  dont:
    - "Leak credentials or private data."
links:
  homepage: "https://x.com/CatGodSandHive"
```

#### `style.md`
Free-form markdown with voice rules and examples. See `templates/style.md`.

#### `goals.yaml`
Structured goal list with optional metrics. See `templates/goals.yaml`.

#### `integrations/x_account.json`
Integration metadata without secrets. Secrets must be references to environment
variables or external secret stores (never commit raw passwords or tokens).
See `templates/integration.x_account.json`.

#### `integrations/x_search_queries.json`
List of saved X (Twitter) search queries the agent should monitor.
See `templates/integration.x_search_queries.json`.

## Workflow

1. Copy the templates into `agents/<agent_id>/`.
2. Replace placeholders with real data.
3. Keep secrets out of Git (use env vars or a secret manager).
4. Validate structure with a simple linter if needed.
5. Write all commits in English.

## Templates

- `templates/agent.profile.yaml`
- `templates/style.md`
- `templates/goals.yaml`
- `templates/integration.x_account.json`
- `templates/integration.x_search_queries.json`
