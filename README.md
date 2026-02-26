# spec-first-starter

A **spec-driven development framework** for AI-assisted projects. Drop the `.agent/` folder into any repo and get structured product thinking, autonomous task execution, and living documentation — out of the box.

> Build the right thing, then build it right.

---

## Why

Most AI coding sessions start with "just build it" and end with rework. This framework enforces a **spec-first workflow** where you define the problem, design the UX, get approval, *then* implement. Every feature gets a spec. Every spec becomes living documentation.

## What You Get

```
.agent/
├── memory/              # Runtime state — what's happening now
│   ├── active_state.md  # Context, decisions, learnings
│   ├── task_queue.md    # Task claiming & execution
│   ├── backlog.md       # Future features & tech debt
│   ├── failures.md      # Failure log for debugging
│   └── milestone_list.json
│
├── product/             # Product definition — what to build
│   ├── problem.md       # Problem, audience, constraints
│   ├── requirements.md  # Functional & non-functional reqs
│   ├── users.md         # Personas with pain points
│   ├── feature_map.md   # Features by domain with status
│   ├── architecture.md  # Tech stack, structure, APIs
│   └── specs/           # Feature specifications
│       └── _TEMPLATE_spec.md
│
├── skills/              # Reusable agent knowledge
│   └── example-skill/
│
└── workflows/           # Slash-command workflows
    ├── discovery.md     # /discovery — vision, personas, requirements
    ├── loop.md          # /loop — autonomous task execution
    ├── new_feature.md   # /new_feature — spec-first dev
    └── success.md       # /success — commit & finalize
```

## Four Core Workflows

| Command | What It Does |
|---------|-------------|
| `/discovery` | **Vision → Personas → Requirements.** Interactive discovery flow to initialise a new project with problem statement, user personas, and requirements. |
| `/new_feature` | **Understand → Design → Approve → Implement → Verify.** Enforces spec-first development with UX mockups before code. |
| `/loop` | **Autonomous task execution.** Picks tasks from the queue, claims them, executes, and moves to the next. Supports multi-agent coordination. |
| `/success` | **Commit, update docs, capture learnings.** Runs after completing a feature — updates feature map, spec outcomes, and active state. |

## Quick Start

1. **Copy** the `.agent/` folder into your project root
2. **Fill in** `product/problem.md` — what are you solving?
3. **Define** `product/users.md` — who are you building for?
4. **Write** `product/requirements.md` — what needs to exist?
5. **Sketch** `product/architecture.md` — how will it work?
6. **Break down** features in `product/feature_map.md`
7. **Queue tasks** in `memory/task_queue.md`
8. **Run** `/new_feature` to start your first feature

## The Spec-First Cycle

```
/new_feature
  → Phase 1: Read context (feature map + queue)
  → Phase 2: Design (mock UX → write spec → get approval)
  → Phase 3: Implement (follow spec tasks)
  → Phase 4: Verify (run spec verification)
/success
  → Commit → update feature map → update spec with outcomes
/loop
  → Pick next task → repeat
```

## Key Principles

- **Never code without a spec** — design first, build second
- **Specs are living documents** — they evolve from "what we planned" to "what we built"
- **Task claiming is multi-agent safe** — multiple agents can work the queue simultaneously
- **Failures are learning** — logged for pattern recognition, not blame
- **Decisions are recorded** — with dates, in `active_state.md`

## Works With

This framework is **tool-agnostic** — it works with any AI coding assistant that can read markdown files and follow workflow instructions. Tested with:
- Antigravity (Google DeepMind)
- Claude Code
- GitHub Copilot Workspace

## License

[MIT](LICENSE) — use it however you want.
