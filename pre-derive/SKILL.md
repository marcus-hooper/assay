---
name: pre-derive
version: 0.1.0
description: |
  Anti-anchoring requirements derivation. Reads ONLY the requirements/spec/issue — never
  the plan or implementation — and independently derives what code changes, tests, error
  handling, and documentation should exist. Produces a "derived expectations" checklist
  that can be compared against any plan or implementation to find gaps.
  Use when: "derive requirements", "pre-derive", "what should this look like",
  or before reviewing a plan to avoid confirmation bias.
allowed-tools:
  - Read
  - Grep
  - Glob
  - Agent
  - AskUserQuestion
---

# Pre-Derive

Independent requirements derivation to prevent anchoring bias.

## When to Use

- Before reviewing a plan (to avoid anchoring to its structure)
- Before reviewing an implementation (to have independent expectations)
- When you want to verify a spec is complete before planning begins
- As Phase 0 of any validation workflow

## Inputs

The user must provide:
- Path to the requirements document (spec, issue, backlog item, design doc)

The user must NOT provide (and the skill must NOT read):
- The plan document
- The implementation or source files
- The review document

## Workflow

> **TODO:** Full skill prompt to be implemented. The workflow will follow this structure:

### Phase 1: Scope Analysis
- Read the requirements document
- For each item in scope, identify: code changes required, external calls, failure points

### Phase 2: Failure Mode Derivation
- For each external call: can it throw? What should happen on failure? What test is needed?
- For each data input: what if it's null/undefined/malformed?

### Phase 3: Artifact Derivation
- What unit tests must exist?
- What error handling must exist?
- What documentation must be updated?
- What integration/E2E tests are needed?

### Phase 4: Output
- Structured checklist of derived expectations
- Each item tagged with its source (which requirement drove it)
- Ready for comparison against plan or implementation
