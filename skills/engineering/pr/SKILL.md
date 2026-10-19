---
name: pr
description: "Use when writing a PR body."
metadata:
  credits:
    skill: show-me
    author: Dex Horthy
    organisation: Humanlayer
    url: "https://github.com/humanlayer/skills/blob/main/plugins/show-me/skills/show-me/SKILL.md"
---

Use this template for writing the PR body:

```markdown
## What

<A brief description of what this pull request is>

## Why

<A brief explanation describing why this pull request existis>

## Testing
### <Before if applicable>
#### Ran
```sh
<command showing what was ran>
```
#### Result
```txt
<command output showcasing failure>
```
### After
#### Ran
```sh
<command showing what was ran>
```
#### Result
```txt
<command output showcasing success>
```

## Merge Danger

**Door:** <one-way or two-way>

<optional: description>

**Blast Radius:** <one-word description>

<optional: potential ramifications of merge>
```

> Agent instuctions: 
>
> - Use the user's domain language from the glossary at the 
> path named in `docs/agents/domain.md`. Spell out every acronym on first use.
>
> - When opening a pull request, always open it as a draft. PRs need human review from the person 
> who is responsible for the code

