# Claude App Boilerplate

Template repository for building full-scale applications using Claude Code's multi-agent orchestration.

## What's Included

- **15 specialized agent definitions** — team lead, requirements analyst, researcher, architect, ui designer, skeleton builder, implementation planner, backend implementer, frontend implementer, test engineer, reviewer, auditor, deployer, monitor, qa tester
- **3 skills** — `/build` (new app from scratch), `/feature` (add features to existing codebase), `/audit` (gap analysis)
- **12-phase pipeline** — requirements → research → architecture → design → skeleton → planning → implementation → testing → review → audit → deploy → QA
- **Project CLAUDE.md** — full context for any new session to understand the design and methodology

## Quick Start

1. Create a new repo from this template:
   ```bash
   gh repo create my-app --template aster2709/claude-app-boilerplate --clone --private
   cd my-app
   ```

2. Start Claude Code (preferably inside cmux or tmux for split panes):
   ```bash
   cmux claude-teams --dangerously-skip-permissions
   # or: tmux → claude
   ```

3. Build your app:
   ```
   /build a SaaS invoice platform with Stripe integration
   ```

4. Add features later:
   ```
   /feature add Stripe subscription billing for premium accounts
   ```

5. Run a gap check anytime:
   ```
   /audit
   ```

## Skills

| Skill | When to use |
|---|---|
| `/build` | Day zero — new app from requirements to deployed and QA-tested |
| `/feature` | Ongoing — add features to an existing codebase |
| `/audit` | Anytime — check for gaps between PRD and implementation |

## Pipeline

### /build (new project — 12 phases)

```
Requirements → Research → Architecture → Design → Skeleton
  (gate)                    (gate)
                                                      ↓
Implementation Planning → Backend + Frontend (parallel)
      (gate)                        ↓
                              Testing → Review → Audit → Deploy → QA
```

### /feature (existing codebase)

```
Requirements → Research → Implementation Plan → Implementers → Review → Audit → Deploy → QA
  (gate)                      (gate)
```

## Agents (15)

| Agent | Role |
|---|---|
| team-lead | Orchestrates full pipeline, enforces completion criteria |
| requirements-analyst | Asks clarifying questions, writes PRD/feature spec |
| researcher | Investigates modern best practices, cost analysis |
| architect | Designs system architecture from PRD + research |
| ui-designer | Design system, shadcn/ui + Magic UI scaffolding |
| skeleton-builder | Creates repo structure, configs, empty modules |
| implementation-planner | Breaks work into parallelizable tasks |
| backend-implementer | API routes, database, integrations, business logic |
| frontend-implementer | Pages, components, styling per DESIGN.md |
| test-engineer | Unit, integration, and component tests |
| reviewer | Deep code review for security, performance, correctness |
| auditor | Verifies implementation matches PRD, finds gaps |
| deployer | Handles deployment to Vercel, Render, Railway, etc. |
| monitor | Post-deployment verification, CI/CD checks |
| qa-tester | Live browser testing via Chrome DevTools MCP |

## Requirements

- Claude Code with Claude Max plan
- tmux (`brew install tmux`) or [cmux](https://cmux.com) (recommended)
- Agent Teams enabled (included in .claude/settings.json)
- Chrome DevTools MCP (for QA testing)

## Recommended System Setup

- [Honcho](https://honcho.dev) plugin — persistent memory across projects
- [cmux](https://cmux.com) — terminal built for coding agents with notification rings
- 21st.dev Magic components — UI design inspiration

## Documentation

All agent outputs are saved to `docs/`:
- `PRD.md` — Product requirements
- `RESEARCH.md` — Technical research and recommendations
- `ARCHITECTURE.md` — System design with cost estimates
- `DESIGN.md` — Visual design system specification
- `IMPLEMENTATION_PLAN.md` — Task breakdown with dependencies
- `QA-REPORT.md` — Browser testing results with screenshots

## Skill Learning

After successful builds, reusable patterns are saved to `.claude/skills/learnings/` so future builds benefit from past experience. This is the boilerplate's self-improvement mechanism.
