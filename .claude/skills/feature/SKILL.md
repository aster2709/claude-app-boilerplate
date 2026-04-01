---
name: feature
description: End-to-end feature development on an existing codebase. From requirements to deployment.
disable-model-invocation: true
argument-hint: [describe the feature you want to build]
---

The user wants to add a feature to an existing codebase. You are the team lead orchestrating an agent team.

## CRITICAL: Use Agent Teams, NOT Subagents

You MUST create an agent team for this work. Do NOT use the Agent tool to spawn subagents.
Instead, create an agent team with tmux split panes so the user can watch all agents work side by side.

Each teammate is a separate Claude Code instance with its own context window.
Teammates communicate through the shared task list and direct messaging.

When spawning teammates, reference the agent definitions in .claude/agents/ by name.
All teammates use Opus.

## Context: Existing Documentation

Before starting any phase, teammates MUST read the docs/ folder if it exists.
This contains the original PRD, research, and architecture documents from the initial build.
All feature work should be consistent with these foundational documents.

## Phase 1: Requirements Discovery

Create an agent team. Spawn a requirements-analyst teammate. Have them:
- Read docs/PRD.md, docs/ARCHITECTURE.md, and docs/RESEARCH.md for existing context
- Read the existing codebase to understand current state
- Ask the user detailed clarifying questions about the feature
- Produce a Feature Spec (not a full PRD — scoped to this feature)
- Include: user flows, data model changes, API changes, UI changes
- Require plan approval before proceeding

## Phase 2: Research

Spawn a researcher teammate. Have them:
- Research modern patterns specific to this feature's domain
- Check how similar features are implemented in production apps
- Identify any new dependencies needed
- Output a Research Brief

## Phase 3: Implementation Plan

Spawn an implementation-planner teammate. Have them:
- Read the existing codebase structure
- Read the feature spec and research brief
- Break the feature into tasks with dependencies and file ownership
- Include database migrations, API endpoints, UI components, tests
- Require plan approval before proceeding

## Phase 4: Implementation

Spawn a backend-implementer and frontend-implementer to work in parallel on independent tasks.
- Backend: API routes, database, integrations, business logic
- Frontend: Pages, components, styling per docs/DESIGN.md
Add more implementers if the task list demands it.

## Phase 5: Review

Spawn a reviewer teammate to do a deep review of all changes. If critical issues are found, assign them back to implementers.

## Phase 6: Audit

Spawn an auditor teammate to verify:
- Feature spec requirements are fully implemented
- No gaps between what was planned and what was built
- Tests cover the critical paths
- No regressions in existing functionality

## Phase 7: PR & Deploy

Create a PR with a clear description of the feature. Spawn a deployer teammate to:
- Check deployment config exists (ask user if not)
- Deploy to staging/production
- Spawn a monitor teammate to verify deployment succeeded

## Phase 8: QA Testing

Spawn a qa-tester teammate to:
- Open the live deployment in Chrome via Chrome DevTools MCP
- Test all user flows like a real user
- Test desktop and mobile viewports
- Take screenshots, check console for errors
- Write docs/QA-REPORT.md
- If major issues found, assign fixes back to implementers, redeploy, re-test

## Rules

- ALWAYS use agent teams with tmux split panes, NEVER use the Agent tool for subagents.
- Wait for user approval after Phase 1 and Phase 3.
- ALL 8 phases must run. Do NOT stop early.
- Each agent focuses on ONE job — no overlap.
- All agents use Opus.
- Report at phase transitions.
- If the auditor finds gaps, loop back to implementation before deploying.
- Create a single feature branch for all work.

The user's feature request: $ARGUMENTS
