# Domain Docs

How the engineering skills consume this repo's documentation when exploring the codebase.

## Where things live

- **Glossary**: `docs/reference/GLOSSARY.md`. In a multi-context repo, `GLOSSARY-MAP.md` at the repo root points at one `docs/reference/<context>/GLOSSARY.md` per context; read each one relevant to the topic.
- **Architecture decision records (ADRs)**: `docs/reference/architecture-decision-records/`. In a multi-context repo, context-scoped decisions live in `docs/reference/<context>/architecture-decision-records/`.

If any of these files don't exist, **proceed silently**. Don't flag their absence; don't suggest creating them upfront. The `/domain-modeling` skill (reached via `/grill-with-docs` and `/improve-codebase-architecture`) creates them lazily when terms or decisions actually get resolved.

## Docs tree

```
docs/
├── README.md                     ← orientation: the four folders and the lifetime test
├── how-to/<goal>.md
├── reference/
│   ├── GLOSSARY.md               ← single-context (multi-context: <context>/GLOSSARY.md)
│   ├── architecture-decision-records/NNNN-<slug>.md
│   └── <subject>.md              ← durable facts, one file per subject
├── faq/<topic>.md
├── tutorials/<name>.md
└── agents/                       ← skill configuration (this file, issue-tracker.md, triage-labels.md)
```

## Before exploring, read these

1. The glossary (or the glossaries the map names) for the area you're working in.
2. The decision records that touch that area.
3. Every file under `how-to/`, `reference/`, `faq/`, and `tutorials/` carries YAML front-matter with a one-line `description:`. Scan those descriptions (`grep -r '^description:' docs/`) and open only the matches. Never read the whole tree.

## Use the glossary's vocabulary

When your output names a domain concept (in an issue title, a refactor proposal, a hypothesis, a test name), use the term as defined in the glossary. Don't drift to synonyms the glossary explicitly avoids.

If the concept you need isn't in the glossary yet, that's a signal: either you're inventing language the project doesn't use (reconsider) or there's a real gap (note it for `/domain-modeling`).

## Flag decision-record conflicts

If your output contradicts an existing decision record, surface it explicitly rather than silently overriding:

> _Contradicts ADR-0007 (event-sourced orders), but worth reopening because…_

## Spell out acronyms

Spell out every acronym on first use in every file you write (docs, pull request (PR) bodies, tickets, specs, handoffs). ADR is not an exception.
