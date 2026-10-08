# Reference

Reference holds durable facts a reader looks up: the glossary, decision records, and one page per subject for everything else. Why belongs in an FAQ (frequently asked questions) entry, steps in a how-to. Path: `docs/reference/`.

## Three kinds

| Kind | Path | Format |
|---|---|---|
| Glossary | `docs/reference/GLOSSARY.md` (single context) or `docs/reference/<ctx>/GLOSSARY.md` with `GLOSSARY-MAP.md` at the repo root (multi-context) | `GLOSSARY-FORMAT.md` in the `domain-modeling` skill |
| Decision record | `docs/reference/architecture-decision-records/NNNN-<slug>.md` (single) or `docs/reference/<ctx>/architecture-decision-records/` (multi) | the decision record format in the `domain-modeling` skill |
| Subject page | `docs/reference/<subject>.md` | template below |

Glossaries and decision records are written through the `domain-modeling` skill; invoke it rather than restating its formats.

## Subject page template

```md
---
description: <one line: the subject and what facts the page holds>
---

# <Subject>

<One or two sentences on what this subject is.>

## <Facet>

<Facts, tables, or lists. State what is, with no steps and no why.>

## See also

- [<FAQ entry>](../faq/<topic>.md#question) (FAQ)
- [<How-to>](../how-to/<goal>.md)
```

## Rules

- **Durable facts only.** Each page passes the lifetime test in the documenting `SKILL.md` (Lifetime test).
- **One file per subject.** Extend the subject's page before creating a new one.
- **Subjects only, no command or endpoint surfaces.** The CLI/API exclusion in the documenting `SKILL.md` (Layout) applies.
- **State, do not instruct or justify.** Steps belong in a how-to; why belongs in an FAQ entry. Link both from See also.
- **Front-matter description names the subject** so a reader scanning descriptions finds the page.
- **Spell out every acronym on first use.** ADR (architecture decision record) included; the folder name is spelled out for the same reason.
