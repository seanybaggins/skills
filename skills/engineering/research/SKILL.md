---
name: research
description: Investigate a question against high-trust primary sources and capture the findings as a Markdown file under `.scratch/research/`. Use when the user wants a topic researched, docs or API facts gathered, or reading legwork delegated to a background agent.
---

Spin up a **background agent** to do the research, so you keep working while it reads.

Its job:

1. Investigate the question against **primary sources** (official docs, source code, specs, first-party APIs), not a secondary write-up of them. Follow every claim back to the source that owns it.
2. Write the findings to a single Markdown file, citing each claim's source. Spell out every acronym on first use.
3. Save it to `.scratch/research/<topic>.md`, creating the folder if needed, and say the path.

Promotion into the project's documentation tree is a separate step: call the Skill tool with "documenting", which applies the lifetime test.
