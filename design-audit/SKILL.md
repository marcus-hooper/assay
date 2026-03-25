---
name: design-audit
version: 0.1.0
description: |
  Post-implementation design completeness audit. Reads a design document, extracts every
  specified behavior/condition/requirement, derives what "done" looks like in code, and
  verifies each item against the actual implementation. Catches specified-but-not-implemented
  gaps, mislabeled status markers, and incomplete coverage.
  Use when: "audit the design", "check completeness", "verify implementation matches spec",
  "design audit", or when a design doc has status markers to verify.
allowed-tools:
  - Bash
  - Read
  - Grep
  - Glob
  - Agent
  - AskUserQuestion
---

# Design Audit

Post-implementation verification that code matches a design specification.

## When to Use

- After implementing features from a design document
- When a design doc has items marked "Complete" that need verification
- When you suspect gaps between spec and implementation
- Before marking a design document as fully implemented

## Inputs

The user must provide:
- Path to the design document
- (Optional) Path to the source files to audit against

## Workflow

> **TODO:** Full skill prompt to be implemented. The workflow will follow this structure:

### Phase 1: Extract Spec Items
- Parse the design document for all specified behaviors, conditions, and requirements
- Extract status claims ("Complete", "Incomplete", etc.)
- Build a structured checklist of every deliverable

### Phase 2: Derive Completeness Criteria
- For each spec item, derive what "done" looks like in code
- Identify functions, conditions, tests, and documentation that must exist
- Map each criterion to searchable patterns (grep targets)

### Phase 3: Verify Implementation
- For each derived criterion, search the codebase to confirm it exists
- Check that code behavior matches the specification (not just presence)
- Verify status claims against actual state

### Phase 4: Report Gaps
- Structured output: what's missing, what's incomplete, what's mislabeled
- Severity classification: blocking vs. non-blocking
- Specific remediation for each gap
