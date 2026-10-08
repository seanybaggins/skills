# How-to

A how-to gets a reader who already knows the system from a goal to a result. Any why it raises goes to an FAQ (frequently asked questions) entry. Path: `docs/how-to/<goal>.md`.

## Template

```md
---
description: <one line: the goal this page reaches, phrased so a grep for the task finds it>
---

# <Goal, as a verb phrase: "Debug a remote embedded target">

## Prerequisites

- <tool, access, or state the reader must already have>

## Steps

1. <one action, with the exact command or edit>
2. <next action>

## Expected result

<what the reader sees when it worked>

## See also

- [Why <question>?](../faq/<topic>.md#why-question) (FAQ)
- [<Reference page>](../reference/<subject>.md)
```

## Rules

- **Title is a goal.** A verb phrase naming the outcome, not a feature or a flag.
- **Write only on explicit request, only for workflows.** A new CLI (command-line interface) flag or API (application programming interface) endpoint is documented in source and the language's doc tooling, never as a how-to.
- **Steps are the whole body.** Each step is one action the reader performs, with the command or edit spelled out. Prerequisites and Expected result bound the sequence.
- **Keep the why out; link it.** When a step needs justification, write that justification as an FAQ entry under `docs/faq/<topic>.md` and link it from See also. The how-to itself stays pure steps.
- **Front-matter description names the goal** so a reader scanning `grep -r '^description:' docs/` finds it from the task they are trying to do.
- **Spell out every acronym on first use.**
