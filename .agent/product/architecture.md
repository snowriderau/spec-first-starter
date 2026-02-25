# Technical Architecture

## Platform Strategy

<!-- Describe the high-level platform approach: single app? monorepo? multiple surfaces? -->

(Brief description of the overall technical architecture)

---

## Project Structure

```
project-name/
├── src/                       # Source code
│   ├── components/            # UI components
│   ├── pages/                 # Routes / pages
│   ├── lib/                   # Shared utilities
│   ├── types/                 # TypeScript interfaces
│   └── styles/                # CSS / design tokens
├── server/                    # Backend (if applicable)
│   └── src/
├── data/                      # Data files / databases
├── scripts/                   # Build/deploy/utility scripts
├── public/                    # Static assets
└── package.json
```

---

## Tech Stack

| Layer | Technology | Purpose |
|-------|-----------|---------|
| **Frontend** | (e.g. Next.js, Vite + React) | (Purpose) |
| **Styling** | (e.g. Tailwind, Vanilla CSS) | (Purpose) |
| **Backend** | (e.g. Express, Hono, none) | (Purpose) |
| **Database** | (e.g. SQLite, Postgres, Supabase) | (Purpose) |
| **Auth** | (e.g. Firebase, Supabase, none) | (Purpose) |
| **Hosting** | (e.g. Vercel, Cloudflare, self-hosted) | (Purpose) |
| **CI/CD** | (e.g. GitHub Actions) | (Purpose) |

---

## API Design

```
PUBLIC (no auth):
  GET  /api/resource              → List all
  GET  /api/resource/[id]         → Single item

AUTHENTICATED (auth required):
  POST /api/resource              → Create
  PUT  /api/resource/[id]         → Update
  DELETE /api/resource/[id]       → Delete
```

---

## Data Model

<!-- Describe key tables/collections and their relationships -->

```sql
-- Example schema
CREATE TABLE IF NOT EXISTS items (
  id TEXT PRIMARY KEY,
  name TEXT NOT NULL,
  created_at DATETIME DEFAULT CURRENT_TIMESTAMP
);
```

---

## Execution Phases

| Phase | Work | Effort |
|-------|------|--------|
| **1. Foundation** | Project scaffold, core data model, basic UI | X weeks |
| **2. Core Features** | Primary feature set, integrations | X weeks |
| **3. Polish** | Design system, performance, edge cases | X weeks |
| **4. Launch** | Deployment, monitoring, documentation | X weeks |

---

## Operational Rules

1. (Key architectural principle — e.g. "Never mutate historical data")
2. (Key architectural principle — e.g. "All external calls rate-limited")
3. (Key architectural principle — e.g. "Prefer static artifacts over runtime queries")
