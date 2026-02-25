---
name: spec-first-lite
description: Lightweight skill to enforce spec-first feature delivery in this repository. Use when implementing, planning, or reviewing feature work.
---

# Spec First Lite

## Use when

- A user asks to build or change a feature.
- A task references feature IDs, specs, or workflow commands.
- You need to verify delivery is aligned with project docs.

## Required pre-read

1. `.agent/product/feature_map.md`
2. `.agent/memory/task_queue.md`
3. `.agent/product/architecture.md`

## Rules

1. Do not implement feature code before a spec exists in `.agent/product/specs/`.
2. If no spec exists, create one from `.agent/product/specs/_TEMPLATE_spec.md` and request approval before coding.
3. During implementation, follow the spec `Implementation Tasks` and `Verification` sections.
4. On completion, update:
   - feature status in `.agent/product/feature_map.md`
   - spec `Implementation Outcomes`
   - `.agent/memory/active_state.md` when decisions changed

## Workflow pointers

- Design/start: `.agent/workflows/new_feature.md`
- Autonomous execution: `.agent/workflows/loop.md`
- Finalization/docs: `.agent/workflows/success.md`
