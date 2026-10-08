---
name: domain-modeling
description: Build and sharpen a project's domain model. Use when discussing codebase terminology, writing or editing a glossary, or recording or editing an architecture decision record (ADR).
---

# Domain Modeling

Actively build and sharpen the project's domain model as you design. This is the *active* discipline: challenging terms, inventing edge-case scenarios, and writing the glossary and decisions down the moment they crystallise. (Merely *reading* the glossary for vocabulary is not this skill: that's a one-line habit any skill can do. This skill is for when you're changing the model, not just consuming it.)

Call the Skill tool with "documenting" for the full `docs/` layout and the acronym rule. Both apply to every file this skill writes.

## File structure

Glossaries and architecture decision records (ADRs) are reference documents. Most repos have a single context:

```
docs/
└── reference/
    ├── GLOSSARY.md
    └── architecture-decision-records/
        ├── 0001-event-sourced-orders.md
        └── 0002-postgres-for-write-model.md
```

If a `GLOSSARY-MAP.md` exists at the repo root, the repo has multiple contexts. The map points to where each one lives:

```
/
├── GLOSSARY-MAP.md
└── docs/
    └── reference/
        ├── architecture-decision-records/     ← system-wide decisions
        ├── ordering/
        │   ├── GLOSSARY.md
        │   └── architecture-decision-records/ ← context-specific decisions
        └── billing/
            ├── GLOSSARY.md
            └── architecture-decision-records/
```

Create files lazily: only when you have something to write. If no glossary exists, create one when the first term is resolved. If no `architecture-decision-records/` exists, create it when the first ADR is needed.

## During the session

### Challenge against the glossary

When the user uses a term that conflicts with the existing language in the glossary, call it out immediately. "Your glossary defines 'cancellation' as X, but you seem to mean Y. Which is it?"

### Sharpen fuzzy language

When the user uses vague or overloaded terms, propose a precise canonical term. "You're saying 'account': do you mean the Customer or the User? Those are different things."

### Discuss concrete scenarios

When domain relationships are being discussed, stress-test them with specific scenarios. Invent scenarios that probe edge cases and force the user to be precise about the boundaries between concepts.

### Cross-reference with code

When the user states how something works, check whether the code agrees. If you find a contradiction, surface it: "Your code cancels entire Orders, but you just said partial cancellation is possible. Which is right?"

### Update the glossary inline

When a term is resolved, update the glossary right there. Don't batch these up: capture them as they happen. Use the format in [GLOSSARY-FORMAT.md](./GLOSSARY-FORMAT.md).

The glossary should be totally devoid of implementation details. Do not treat it as a spec, a scratch pad, or a repository for implementation decisions. It is a glossary and nothing else.

### Offer ADRs sparingly

Only offer to create an ADR when all three are true:

1. **Hard to reverse**: the cost of changing your mind later is meaningful
2. **Surprising without context**: a future reader will wonder "why did they do it this way?"
3. **The result of a real trade-off**: there were genuine alternatives and you picked one for specific reasons

If any of the three is missing, skip the ADR. Use the format in [DECISION-RECORD-FORMAT.md](./DECISION-RECORD-FORMAT.md).
