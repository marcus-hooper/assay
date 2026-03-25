# assay

Verification skills for [Claude Code](https://claude.ai/code).

Trust nothing, verify everything. Assay provides post-implementation audit and verification skills that catch gaps between what was specified and what was built.

## Skills

| Skill | What it does |
|-------|-------------|
| `/design-audit` | Verifies implementation matches a design spec — catches specified-but-not-implemented gaps |
| `/pre-derive` | Independently derives expected requirements before seeing a plan, preventing anchoring bias |
| `/completion-review` | Post-ship codebase impact audit — finds redundant code, adoption opportunities, documentation drift |
| `/validate-plan` | Adversarial plan validation with binary PASS/FAIL verdicts and red flag scanning |
| `/verify-implementation` | Mechanical plan-vs-code compliance — counts tests, matches deliverables, checks scope |

## Install

```bash
git clone https://github.com/marcus-hooper/assay.git ~/Source/assay
cd ~/Source/assay && ./setup
```

The setup script symlinks skills into `~/.claude/skills/` where Claude Code discovers them automatically.

## Uninstall

```bash
cd ~/Source/assay && ./uninstall
```

## Philosophy

These skills are built on a workflow methodology where:

- **Plans are contracts** — the plan defines exactly what must be implemented, no more, no less
- **Verification is independent** — derive expectations before seeing the implementation to avoid confirmation bias
- **Binary verdicts** — PASS or FAIL, not "mostly complete" or "minor issues"
- **Count everything** — if the plan says 8 tests, count 8 `it()` blocks in the spec file
- **Trust nothing** — don't trust the plan's claim it covered the spec, don't trust the implementation report's claim everything was done

## Status

Early development. Skill definitions are scaffolded with workflow outlines. Full prompt implementations are in progress.

## License

MIT
