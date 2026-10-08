---
name: documenting
description: Write or organise project documentation in the Diátaxis layout under docs/. Use when writing a how-to, an FAQ (frequently asked questions) entry, a reference page, or a tutorial, when deciding where a glossary or decision record lives, when promoting research notes into docs/, or when another skill needs the docs layout, the lifetime test, or the acronym rule.
---

# Documenting

Documentation lives under `docs/` in four Diátaxis quadrants (how-to, reference, FAQ, tutorials). Diátaxis calls the third quadrant "explanation"; this layout calls it **FAQ** (frequently asked questions) everywhere.

## Layout

```
docs/
├── README.md                     ← one-page orientation: the four folders and the lifetime test
├── how-to/<goal>.md
├── reference/
│   ├── GLOSSARY.md               ← single-context
│   ├── <ctx>/GLOSSARY.md         ← multi-context; GLOSSARY-MAP.md at the repo root points here
│   ├── architecture-decision-records/NNNN-<slug>.md
│   └── <subject>.md              ← durable facts, one file per subject
├── faq/<topic>.md
├── tutorials/<name>.md
└── agents/                       ← configuration (issue-tracker.md, domain.md, triage-labels.md); stays separate
.scratch/research/<topic>.md      ← research output; promotion into docs/ is a separate explicit step
```

CLI (command-line interface) and API (application programming interface) reference lives in source and the language's doc tooling, never under `docs/reference/`.

## Lifetime test

A page earns a place in the tree only when both hold:

1. It survives a rewrite of the code it describes.
2. A new contributor six months out would want it.

PR (pull request) lifetime material (what changed, review notes, handoff state) stays out of the tree. **Borderline: ask the user** with the two criteria and your read on each, then follow their call.

Promoting `.scratch/research/<topic>.md` runs the same test on each finding; survivors land in the quadrant their form dictates, the rest stay in scratch.

## Rules every page follows

- **Front-matter.** Every file in how-to, reference, faq, tutorials opens with YAML (YAML Ain't Markup Language) front-matter carrying a one-line `description:`. Readers scan descriptions (`grep -r '^description:' docs/`) and open only matches; a page without one is invisible.
- **Acronym rule.** Spell out every acronym on first use in every file you write, docs or otherwise (PR bodies, tickets, specs, handoffs). ADR (architecture decision record) is not an exception. "Diátaxis" is a name, not an acronym.
- **Punctuation.** Punctuate with commas, colons, periods, or parentheses.

## Reading before writing

Scan descriptions and read only matching pages; extend an existing page before creating a new one. Read the whole tree only when writing `docs/README.md`.

## Pick the quadrant

| You are writing | Read |
|---|---|
| Steps to reach a goal, on explicit request, for a workflow (never a flag or endpoint) | [`references/diataxis/how-to.md`](references/diataxis/how-to.md) |
| A why: a question whose answer is reasoning, trade-off, or context | [`references/diataxis/faq.md`](references/diataxis/faq.md) |
| A glossary, a decision record, or durable facts about a subject | [`references/diataxis/reference.md`](references/diataxis/reference.md) |
| A beginner path a how-to, its FAQ, and its reference already cover end to end | [`references/diataxis/tutorial.md`](references/diataxis/tutorial.md) |

A how-to carries no why: any why that surfaces becomes an FAQ entry linked from the how-to's See also.

## Tutorial proposal rule

Tutorials are proposed, never written unprompted. When at least one how-to plus its FAQ and reference form a complete beginner path, say so and name the pages; write the tutorial only after the user confirms.
