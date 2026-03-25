---
name: validate-plan
version: 0.1.0
description: |
  Adversarial plan validation with binary PASS/FAIL verdicts. Verifies a plan against
  its requirements using anti-anchoring (Phase 0 derives expectations independently),
  explicit enumeration checks (no vague "appropriate tests"), red flag scanning,
  and failure mode coverage. Returns PASS or FAIL — no soft language.
  Use when: "validate this plan", "is this plan complete", "check the plan",
  or before handing a plan to an implementer.
allowed-tools:
  - Read
  - Grep
  - Glob
  - Agent
  - AskUserQuestion
---

# Validate Plan

Adversarial quality gate between planning and implementation.

## When to Use

- Before starting implementation on a plan
- When you want to verify a plan is complete and specific enough
- As a quality gate in a plan-implement-review workflow
- When you suspect a plan has vague or missing sections

## Inputs

The user must provide:
- Path to the plan document
- Path to the requirements document (spec, backlog, design doc)

## Workflow

> **TODO:** Full skill prompt to be implemented. The workflow will follow this structure:

### Phase 0: Pre-Derivation (Anti-Anchoring)
- Read ONLY the requirements — do NOT read the plan
- Derive what the plan SHOULD contain: code changes, tests, error handling, docs
- Output derived expectations before seeing the plan

### Phase 1: Verification (parallel agents)
- **Backlog Alignment:** Every requirement criterion addressed in the plan
- **Scope Validation:** IN/OUT scope correct, no scope creep language
- **Technical Analysis:** SDK/API understanding, data sources, failure modes
- **Testing Requirements:** Explicit test enumeration, not categories
- **Documentation:** Specific file/section targets, not "update docs"

### Phase 2: Adversarial Review
- Compare Phase 0 expectations against actual plan
- Every Phase 0 item must be explicitly addressed
- Red flag phrase scanning (automatic FAIL triggers)

### Phase 3: Verdict
- Binary PASS or FAIL — no "conditional pass", "minor issues", "mostly complete"
- If FAIL: specific corrections list for the planner
