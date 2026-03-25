---
name: verify-implementation
version: 0.1.0
description: |
  Mechanical plan-vs-code compliance check. Independently counts tests in spec files
  and compares to plan claims, matches each planned test to an actual test case, verifies
  each planned documentation update exists in the actual file, and checks scope compliance
  (no additions, no omissions). Trust nothing — verify by reading the code.
  Use when: "verify implementation", "check implementation against plan",
  "did the implementer finish everything", or after implementation before review.
allowed-tools:
  - Bash
  - Read
  - Grep
  - Glob
  - Agent
  - AskUserQuestion
---

# Verify Implementation

Mechanical compliance check: does the code match the plan?

## When to Use

- After implementation, before code review
- When an implementation report claims completeness
- When you want to verify test counts, documentation, and scope compliance
- As a pre-review quality gate

## Inputs

The user must provide:
- Path to the plan document
- Path to the implementation report (if one exists)
- (Optional) Paths to changed source files, or a git diff reference

## Workflow

> **TODO:** Full skill prompt to be implemented. The workflow will follow this structure:

### Phase 1: Backlog Verification
- Every acceptance criterion from requirements appears in both plan and implementation

### Phase 2: Implementation Verification (parallel)
- **Count Verification:** Count actual `it()` blocks in spec files, compare to plan claims
- **Test-by-Test:** Match each planned test to an actual test case by behavior
- **Documentation:** Verify each planned doc update exists in the actual file

### Phase 3: Scope Check
- All IN scope items implemented
- No OUT of scope items implemented
- No unplanned file changes
- No "while we're here" additions

### Phase 4: Quality Check
- Code follows existing patterns
- Tests have meaningful assertions (not stubs)
- Documentation is accurate (not placeholder)

### Phase 5: Gap Detection
- Independently derive what SHOULD exist from code changes
- Verify those artifacts exist
- Final safety net — catches what everyone else missed

### Phase 6: Report
- APPROVE or REJECT with specific blocking issues
- Every blocking issue has a specific fix
