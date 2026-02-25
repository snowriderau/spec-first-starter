# Task Queue

**Last Updated:** YYYY-MM-DD

Tasks for autonomous execution. Agents **claim** tasks before working on them.

---

## Queue

| # | ID | Task | Spec | Status | Claimed By | Est. |
|---|-----|------|------|--------|------------|------|
| 0 | INIT-1 | (First task description) | [spec](../product/specs/INIT-1_name.md) | QUEUED | — | Xh |
| 1 | INIT-2 | (Second task description) | [spec](../product/specs/INIT-2_name.md) | QUEUED | — | Xh |

---

## Task Dependencies

```
INIT-1 (First task) ←── no blockers
  └── INIT-2 (Second task) ←── INIT-1
```

---

## Task Details

### INIT-1: (First Task Name)
**Spec:** [INIT-1_name.md](../product/specs/INIT-1_name.md)

**Tasks:**
1. (Specific subtask)
2. (Specific subtask)

**Verification:**
- (How to test this works)

---

## Status Guide

| Status | Meaning |
|--------|---------|
| `QUEUED` | Available for any agent to claim |
| `CLAIMED` | Agent working on it (see "Claimed By") |
| `DONE` | Completed — move to Completed section |
| `BLOCKED` | Can't proceed — see Blocked section |

---

## Completed

| # | ID | Task | Date | Status |
|---|----|------|------|--------|

---

## Blocked

| ID | Task | Reason | Since |
|----|------|--------|-------|

---

## Claim Rules

1. **Before starting work:** Change status from `QUEUED` → `CLAIMED`
2. **Add your agent ID:** Put a unique ID in "Claimed By"
3. **Skip claimed tasks:** If a task is `CLAIMED` by another agent, move to next `QUEUED` task
4. **Release on completion:** Move to Completed section
5. **Release on block:** Set to `BLOCKED` with reason

### Stale Claims

If a task is CLAIMED but hasn't been updated in 1+ hours, another agent may reclaim it.
