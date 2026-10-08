# Tutorial

A tutorial walks a beginner through a complete path on one page. Path: `docs/tutorials/<name>.md`.

## When to propose one

Propose a tutorial when at least one how-to, plus the FAQ (frequently asked questions) entries and reference pages it links, cover a beginner's path end to end. Name the pages in the proposal. Write only after the user confirms; never write one unprompted.

## Template

```md
---
description: <one line: who this is for and what they will have built or done by the end>
---

# <Name: "Your first remote debug session">

<Who this is for and what they will have at the end. One short paragraph.>

> Source of truth: the steps below are copied from [<how-to>](../how-to/<goal>.md). When the two differ, the how-to is right; update this page to match.

## Before you start

- <prerequisite, with a link to where to get it>

## 1. <First milestone>

<Steps inlined from the how-to, with the result the learner should see after each.>

## 2. <Next milestone>

## What you did

<Recap of the path, with links to the how-to, FAQ, and reference pages for going further.>
```

## Rules

- **Inline the steps.** The learner never leaves the page. Copy the steps from the how-to rather than linking out mid-path.
- **Carry the source-of-truth note** pointing at the how-to, so the duplication is declared and the how-to wins when they drift.
- **Milestones, not features.** Each section ends with something the learner can see working.
- **Context goes in a sentence, reasoning goes in a link.** A line of why is fine where it keeps the learner oriented; anything longer links the FAQ entry.
- **Front-matter description names the audience and the outcome** so a reader scanning descriptions knows who the page is for.
- **Spell out every acronym on first use.**
