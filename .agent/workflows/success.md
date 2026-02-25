---
description: Commit work, update docs, and capture learnings on successful feature completion
---

# /success - Finalize Feature Workflow

Run this workflow when a feature or fix is complete and working.

// turbo-all

---

## 1. Review Changes

```bash
git status
```

---

## 2. Quick Architecture Check

Before committing, verify against your core architectural principles:

| Rule | Check |
|------|-------|
| (Principle 1) | (Verification question) |
| (Principle 2) | (Verification question) |
| Error handling | Graceful failure on errors? |

**Violations?** Note in `.agent/memory/failures.md` and continue.

---

## 3. Stage & Commit

```bash
git add -A
git commit -m "feat: <DESCRIBE_WHAT_WAS_ACCOMPLISHED>"
```

**Prefixes:** `feat:` | `fix:` | `refactor:` | `docs:` | `data:` | `chore:`

---

## 4. Update Task Queue (FOR /loop)

If running in autonomous loop mode, update `.agent/memory/task_queue.md`:

1. Move completed task to `## Completed` section with date
2. Clear the "Claimed By" field
3. If needed, mark next `QUEUED` task as your next target

**Example move:**
```markdown
## Completed
| INIT-1 | First feature | 2026-01-25 | feat: implement first feature |
```

---

## 5. Update Feature Map

Mark the feature as ✅ Done in `.agent/product/feature_map.md`:

```markdown
| INIT-1 | Feature name | P0 | ✅ Done | Implemented with... |
```

---

## 6. Update Feature Spec

**Specs are living documents, not throwaway planning artifacts.** They serve as the permanent documentation for each feature and should reflect what was actually built.

If the completed work has a spec in `.agent/product/specs/`, update it with:

1. **Set status** to `✅ Done (YYYY-MM-DD)` and add commit hashes
2. **Add an `## Implementation Outcomes` section** at the bottom covering:
   - Actual results and metrics (e.g. rows inserted, success rates, performance)
   - Any deviations from the original design and why
   - Bug fixes or learnings discovered during implementation
   - Files modified with a summary of changes
   - Remaining next steps or follow-up work
3. **Do NOT delete** the original design sections — they provide context for why decisions were made

> The spec goes from "what we planned" → "what we built". Future agents and conversations reference specs to understand the feature, not the implementation plan.

---

## 7. Quick Doc Updates

| Changed | Update |
|---------|--------|
| Architecture | `.agent/product/architecture.md` |
| New commands | `README.md` |
| Learnings | `.agent/memory/active_state.md` |

---

## 8. Commit Docs

```bash
git add -A && git commit -m "docs: update after <feature>"
```

---

## 9. Final Check

```bash
git status && git log --oneline -3
```

---

## Summary Output

```
✅ Committed: <what>
📝 Docs updated: <which>
📋 Spec updated: <spec file>
🔗 Commits: <hashes>
```

**For /loop:** After this, return to loop and pick next task.
