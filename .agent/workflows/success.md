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

**Specs are living documents, not throwaway planning artifacts.** They serve as the permanent documentation for each feature and MUST describe what is currently in production.

If the completed work has a spec in `.agent/product/specs/`, completely overhaul it:

1. **Set status** to `✅ Done (YYYY-MM-DD)` or `Living Reference`.
2. **Rewrite the document** to act as a single, complete specification of what is actually built and running.
3. **Delete outdated "Next Steps", "Implementation Status", or "Planning" sections.** If a feature changed during implementation, rewrite the section so it describes what exists now.
4. **Do NOT append an "Implementation Outcomes" or "Updates" log.** This is not a change tracker; it is a source of truth.
5. If there are future ideas, put them in a dedicated `Future Enhancements` section.

> A spec goes from "what we plan to build" -> "how it currently works in production." Future agents use specs as reference manuals, so outdated plans cause bad follow-on work.

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
