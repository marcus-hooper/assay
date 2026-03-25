---
name: completion-review
version: 0.1.0
description: |
  Post-ship codebase impact audit. After a feature lands, searches for code that's now
  redundant, code that should adopt the new capability, blocked work that's now unblocked,
  and documentation drift. Generates follow-up work items.
  Use when: "completion review", "ripple effects", "what did this change affect",
  "adoption audit", or after completing a feature to find what else needs updating.
allowed-tools:
  - Bash
  - Read
  - Grep
  - Glob
  - Agent
  - AskUserQuestion
---

# Completion Review

Post-implementation codebase impact and adoption audit.

## When to Use

- After completing a feature or requirement
- After merging a significant change
- When you want to find code that should use a new capability
- When you want to identify redundant code after a refactor

## Inputs

The user must provide:
- Description of what was implemented (or path to implementation report/PR)
- (Optional) Path to the source files that changed

## Workflow

> **TODO:** Full skill prompt to be implemented. The workflow will follow this structure:

### Phase 1: Redundant Code Analysis
- Search for code that manually does what the new feature now handles
- Classify as "redundant now" vs. "redundant after future work"

### Phase 2: Redundant Tests Analysis
- For each redundant source file, find its test file
- Identify tests verifying now-obsolete behavior

### Phase 3: Adoption Audit
- Search for code that SHOULD use the new capability but doesn't
- Think about use cases, not implementation — where would this be valuable?
- Search user-facing scenarios: error handling, logging, diagnostics

### Phase 4: Blocked Work
- What was blocked that's now possible?
- What helpers/methods can other features now reuse?

### Phase 5: Documentation Drift
- Code samples that no longer match implementation
- Status markers that need updating
- Stale examples or outdated instructions

### Phase 6: Follow-up Items
- Generate structured list of follow-up work items
- Each item classified: adoption, cleanup, test update, doc fix
