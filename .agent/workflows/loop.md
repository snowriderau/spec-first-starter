---
description: Start autonomous loop - pick a task from the queue and work continuously until done
---

# 🔄 Autonomous Loop

**To use:** Open this workflow and ask "Run /loop"

---

## Loop Instructions

### Step 0: Generate Agent ID
Generate a unique agent ID for this session. Use format: `agent-HH:MM` (current time).
Example: `agent-13:15`

Store this mentally - you'll use it for all claims.

### Step 1: Read Queue
// turbo
```bash
cat .agent/memory/task_queue.md
```

### Step 2: Find & Claim Task
1. Find the **first task** with status `QUEUED` (not `CLAIMED`)
2. **IMPORTANT:** Edit `task_queue.md`:
   - Change status from `QUEUED` → `CLAIMED`
   - Add your agent ID to "Claimed By" column
3. If ALL tasks are `CLAIMED` by other agents, output:
   ```
   ⏳ All tasks claimed by other agents. Waiting...
   ```
   Then skip to Step 5 (check again in next iteration).

### Step 3: Execute Task

#### 3a. Check for Spec
Look for a spec linked in the task or feature map:
```bash
cat .agent/product/specs/<TASK_ID>_*.md 2>/dev/null || echo "No spec found"
```

**If NO spec exists:**
1. **STOP** - Do not start coding
2. Create spec using `/new_feature` Phase 2 (Design)
3. Get user approval if significant feature
4. Then proceed to implementation

#### 3b. Implementation
1. Read the spec's verification criteria
2. Follow `/new_feature` Phase 3 (Implementation)
3. Run tests/verification as specified in spec

### Step 4: On Completion
**Success:**
1. Run `/success` workflow to commit
2. Update `task_queue.md`:
   - Move the task row to `## Completed` section
   - Include date and commit message

**Failure:**
1. Log error to `.agent/memory/failures.md`
2. Try to fix (max 3 attempts)
3. If still failing:
   - Change status to `BLOCKED`
   - Add reason to Blocked section
   - Clear "Claimed By"

### Step 5: Continue Loop
**DO NOT STOP.** After completing/blocking a task:
1. Say: "✅ Task complete. Checking queue for next task..."
2. Go back to Step 1
3. Repeat until no more `QUEUED` tasks

### Step 6: Completion
When ALL tasks are `DONE` or `BLOCKED`:
```
<promise>LOOP_COMPLETE</promise>
```

---

## Multi-Agent Coordination

Multiple agents can run `/loop` simultaneously:

| Agent 1 | Agent 2 |
|---------|---------|
| Claims Task-1 | Sees Task-1 claimed, claims Task-2 |
| Works on Task-1 | Works on Task-2 |
| Completes, claims Task-3 | Completes, claims Task-4 |

**Rule:** First agent to write the claim wins. If you see a task already claimed, skip it.

**Stale Claims:** If a task is CLAIMED but untouched for 1+ hour, you may reclaim it.

---

## Emergency Stop

To cancel the loop at any time:
- Send any message to interrupt
- Or say "stop" or "cancel"
