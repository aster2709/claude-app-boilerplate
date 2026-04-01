---
name: build
description: Full application build from requirements. Orchestrates multi-agent pipeline from PRD to review.
disable-model-invocation: true
argument-hint: [describe what you want to build]
---

The user wants to build something from scratch. You are the team lead orchestrating an agent team.

## CRITICAL: Use Agent Teams, NOT Subagents

You MUST create an agent team for this work. Do NOT use the Agent tool to spawn subagents.
Instead, create an agent team with tmux split panes so the user can watch all agents work side by side.

Each teammate is a separate Claude Code instance with its own context window.
Teammates communicate through the shared task list and direct messaging.

When spawning teammates, reference the agent definitions in .claude/agents/ by name.
All teammates use Opus.

## Phase 1: Requirements (approval gate)

Create an agent team. Spawn a requirements-analyst teammate. Have them ask the user detailed clarifying questions until a complete PRD can be written. Require plan approval before finalizing the PRD. Do NOT proceed until the user approves.

## Phase 2: Research

Once PRD is approved, spawn a researcher teammate to investigate modern best practices, standard patterns, and technology choices relevant to the PRD. Wait for completion.

## Phase 3: Architecture (approval gate)

Spawn an architect teammate. Give them the PRD and research document. Have them design the complete system architecture. Require plan approval. Do NOT proceed until the user approves.

## Phase 4: Skeleton

Once architecture is approved, spawn a skeleton-builder teammate to create the repo structure, configs, and empty modules that compile and run.

## Phase 5: Implementation Planning (approval gate)

Spawn an implementation-planner teammate to break the architecture into concrete, parallelizable tasks with dependencies. Present the plan to the user for approval.

## Phase 6: Implementation

Spawn 2-3 implementer teammates to work through tasks in parallel using git worktrees. Each implementer works on independent tasks. Spawn a test-engineer teammate to write tests alongside implementation.

## Phase 7: Review

Once implementation is complete, spawn a reviewer teammate for a deep code review. Have them file issues as tasks. If critical issues are found, assign them back to implementers.

## Rules

- ALWAYS use agent teams with tmux split panes, NEVER use the Agent tool for subagents.
- Wait for user approval between phases 1-2, 3-4, and 5-6.
- All agents use Opus.
- Update the user at phase transitions, not on every action.
- If any agent gets stuck, report to the user immediately.

The user's requirement: $ARGUMENTS
