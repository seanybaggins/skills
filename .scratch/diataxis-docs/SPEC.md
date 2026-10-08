# Spec: Diátaxis documentation across the skills

Agreed in a grilling session on 2026-10-08. Fork of mattpocock/skills, diverging on purpose.

## Vocabulary

- **Diátaxis**: a documentation framework with four quadrants: how-to, reference, explanation, tutorial. In this fork, explanation is relabelled **FAQ** everywhere.
- **Lifetime test**: a document earns a place in the tree only if it survives a rewrite of the code it describes and a new contributor six months out would want it. Borderline cases ask the user. PR-lifetime material never goes in the tree.
- **Decision record**: what upstream calls an ADR (Architecture Decision Record). Folder is spelled out.
- **Acronym rule**: every acronym is spelled out on first use in every file any skill writes (skill output, PR bodies, tickets, specs, handoffs, docs). ADR is not an exception.

## Target-repo layout (what the skills write into a user's project)

```
docs/
├── README.md                     ← one-page human orientation: the four folders and the lifetime test
├── how-to/<goal>.md
├── reference/
│   ├── GLOSSARY.md               ← single-context
│   ├── <ctx>/GLOSSARY.md         ← multi-context; root GLOSSARY-MAP.md unchanged, points here
│   ├── architecture-decision-records/NNNN-<slug>.md
│   └── <subject>.md              ← durable facts only; never CLI or API reference (those live in source and language doc tools)
├── faq/<topic>.md
├── tutorials/<name>.md
└── agents/                       ← configuration, stays separate (issue-tracker.md, domain.md, triage-labels.md)
.scratch/research/<topic>.md      ← research output; promotion to the tree is a separate explicit step
```

Every file in how-to, reference, faq, tutorials carries YAML front-matter with a one-line `description:`. Consumers scan descriptions (e.g. `grep -r '^description:' docs/`) and open only matches. Never read the whole tree.

## Quadrant rules

- **How-to**: title is a goal ("Debug a remote embedded target"). Sections: Prerequisites, numbered Steps, Expected result, See also. Contains no why. Any why that arises is written as an FAQ entry and linked from See also. Written only on explicit request, only for workflows. Never for a new CLI flag or API.
- **FAQ**: `docs/faq/<topic>.md`, `### <question>?` headings. Each answer: short answer first (one or two sentences), optional elaboration, See also.
- **Reference**: glossary (format from domain-modeling GLOSSARY-FORMAT.md), decision records, other durable facts one file per subject.
- **Tutorial**: proposed by the skill, never auto-written, when at least one how-to plus its FAQ and reference form a complete beginner path. User confirms. Steps are inlined so the learner never leaves the page, with a "source of truth" note pointing at the how-to.

## Changes in this repo (skills)

### T1 New skill `skills/engineering/documenting/`
- `SKILL.md`: model-invoked (no `disable-model-invocation`), also runnable as `/documenting <what>`. Carries: the layout above, the lifetime test rubric, the acronym rule, the front-matter requirement, the "ask on borderline" rule, the tutorial proposal rule. Points to per-quadrant files.
- `references/diataxis/how-to.md`, `faq.md`, `reference.md`, `tutorial.md`: template plus rules for that quadrant.
- `agents/openai.yaml` like sibling skills.
- Follow `skills/productivity/writing-for-agents/SKILL.md` and its SKILL-MECHANICS.md. Concise. No em-dashes.

### T2 `domain-modeling` and `grill-with-docs`
- Glossary path `docs/reference/GLOSSARY.md`; multi-context `docs/reference/<ctx>/GLOSSARY.md` with root `GLOSSARY-MAP.md`.
- Decision records at `docs/reference/architecture-decision-records/` (single) and `docs/reference/<ctx>/architecture-decision-records/` (multi).
- Spell out "architecture decision record" on first use in SKILL.md, ADR-FORMAT.md, GLOSSARY-FORMAT.md, and the grill-with-docs description. Rename ADR-FORMAT.md to DECISION-RECORD-FORMAT.md and fix links.
- SKILL.md calls the Skill tool with "documenting" for layout and the acronym rule rather than restating them.

### T3 `setup-matt-pocock-skills`
- `domain.md` template: new paths, the tree listing, the description-scan rule for consumers, the acronym rule.
- Setup writes `docs/README.md` (orientation page) if absent.
- When a root `GLOSSARY.md` or `docs/adr/` already exists, ask before `git mv` to the new location; record whatever path results in `domain.md`.
- Exploration step lists the new paths.

### T4 Consumer skills
Files: tdd, diagnosing-bugs, pr, wait-what, improve-codebase-architecture, to-tickets, to-spec, triage, implement, implement-spec, code-review, handoff, retro, wayfinder, teach (only where they currently name `GLOSSARY.md`, `docs/adr/`, or ADRs; also writing skills for the acronym rule).
- Replace hardcoded `GLOSSARY.md` / `docs/adr/` paths with "the glossary and decision records at the paths named in `docs/agents/domain.md`".
- Skills that explore before working (tdd, diagnosing-bugs, implement, improve-codebase-architecture, triage, to-tickets, to-spec) also scan `docs/` front-matter descriptions for relevant how-tos and FAQ entries, opening only matches.
- Every skill that writes an artefact (pr, to-spec, to-tickets, handoff, retro, wayfinder, triage, teach, domain-modeling, research) gets one line: spell out every acronym on first use.
- Spell out "ADR" on first use wherever it stays.

### T5 `research`
- Step 3 becomes: save to `.scratch/research/<topic>.md`. Promotion into the Diátaxis tree is a separate step via `documenting`, applying the lifetime test.

### T6 `ask-matt`
- Route to `documenting`: where it sits in the flow (after grill-with-docs leaves a glossary; on explicit "document this workflow"; promotion of research). Spell out ADR. Update paths it names.

### T7 Fork plumbing
- `.claude-plugin/marketplace.json`: name `sean-link`, owner Sean Link, plugin `sean-link-skills`, description notes fork.
- `.claude-plugin/plugin.json` and `package.json`: name `sean-link-skills`, version 1.4.0, repository `https://github.com/seanybaggins/skills`, author Sean Link; add `./skills/engineering/documenting` to `skills`.
- `README.md` and `skills/engineering/README.md`: add `documenting` under Model-invoked, update domain-modeling/research lines. No docs page, no changeset.
- `claude plugin validate . --strict` passes.

## Changes in ~/nix-home (T8, separate repo, left uncommitted)
- `overlays/pkgs/matt-pocock-skills/default.nix`: take `name` as an argument (default "matt-pocock").
- `flake.nix`: add input `sean-link-skills = { url = "github:seanybaggins/skills"; flake = false; }`.
- `parts/nixpkgs.nix`: add `sean-link-skills = final.callPackage ../overlays/pkgs/matt-pocock-skills { src = inputs.sean-link-skills; name = "sean-link"; }`.
- `home/home.nix`: comment out the matt-pocock line, add `home.file.".claude/marketplaces/sean-link".source = pkgs.sean-link-skills;`.
- Test with `nix build --override-input sean-link-skills path:/home/sean/personal-repos/skills` on the home configuration (or evaluate the package), output to ~/nix-home/claude-commands.log. Do not switch the generation.
