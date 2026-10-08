# FAQ

The FAQ (frequently asked questions) quadrant is where the why lives: reasoning, trade-offs, context, and history that no how-to or reference page should carry. Path: `docs/faq/<topic>.md`, one file per topic, one `###` heading per question.

## Template

```md
---
description: <one line: the topic and the kind of questions this file answers>
---

# <Topic>

### <Question, phrased as the reader would ask it>?

<Short answer: one or two sentences.>

<Optional elaboration: the trade-off, the history, the alternatives considered.>

See also: [<how-to or reference page>](../how-to/<goal>.md)

### <Next question>?
```

## Rules

- **Headings are questions** ending in `?`, so a how-to's See also can link straight to the anchor.
- **Short answer first.** One or two sentences a reader can stop at. Elaboration follows only when it adds something.
- **One topic per file.** A question that belongs to another topic goes in that topic's file, created if absent.
- **This is the home for why.** When a how-to step or a reference fact wants justification, the justification is written here and linked from that page's See also.
- **Decision records stay in reference.** An FAQ entry may summarise a decision and link the ADR (architecture decision record) under `docs/reference/architecture-decision-records/`; it does not replace it.
- **Front-matter description names the topic** so a reader scanning descriptions finds the file from the subject of their question.
- **Spell out every acronym on first use.**
