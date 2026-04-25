---
name: feature-development-with-roadmap-phase
description: Workflow command scaffold for feature-development-with-roadmap-phase in thoughtbox.
allowed_tools: ["Bash", "Read", "Write", "Grep", "Glob"]
---

# /feature-development-with-roadmap-phase

Use this workflow when working on **feature-development-with-roadmap-phase** in `thoughtbox`.

## Goal

Implements a major new feature or architectural phase, typically as part of a roadmap (e.g. persistence, progressive disclosure, init workflow, server refactor).

## Common Files

- `src/persistence/*.ts`
- `src/discovery-registry.ts`
- `src/tool-descriptions.ts`
- `src/tool-registry.ts`
- `src/init/**`
- `src/server-factory.ts`

## Suggested Sequence

1. Understand the current state and failure mode before editing.
2. Make the smallest coherent change that satisfies the workflow goal.
3. Run the most relevant verification for touched files.
4. Summarize what changed and what still needs review.

## Typical Commit Signals

- Create new files for the feature (e.g. storage, registry, handler, etc.)
- Update or create index/registry/handler files to wire in the new feature
- Add or update types and schemas as needed
- Document the new feature in README or architecture docs
- Merge via pull request with 'feat:' or 'refactor:' prefix

## Notes

- Treat this as a scaffold, not a hard-coded script.
- Update the command if the workflow evolves materially.