# Docs

Documentation for this repo, organised by what the reader is trying to do.

| Folder | Holds | Reach for it when |
| --- | --- | --- |
| `how-to/` | Goal-titled, step-by-step guides for a workflow | You need to get something done |
| `reference/` | Durable facts: the glossary, architecture decision records (ADRs), one file per subject | You need to look something up |
| `faq/` | Questions and short answers that explain why things are the way they are | You want to understand a choice |
| `tutorials/` | Complete beginner paths, steps inlined | You are new and want a guided start |
| `agents/` | Configuration for the engineering skills | You are changing how agents work here |

Every file in the first four folders starts with YAML front-matter carrying a one-line `description:`. Scan descriptions (`grep -r '^description:' docs/`) and open only what matches.

## The lifetime test

A document earns a place here only if it survives a rewrite of the code it describes and a new contributor six months from now would still want it. Material tied to one pull request (PR) belongs in the PR, not here. Research notes live in `.scratch/research/` until they pass this test.

## Conventions

- Spell out every acronym on first use in every file.
- How-tos hold no "why"; the why becomes an FAQ (frequently asked questions) entry linked from the how-to's See also.
- `/documenting` writes to this tree and applies these rules.
