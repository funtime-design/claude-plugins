---
name: gaps
description: Use when the user wants gaps, blind spots, or missing pieces found in a plan, project, spec, or system — "find gaps", "/gaps", "what are we missing", "poke holes", "push back on this".
---

# Gaps — evidence-based gap analysis

Brainstormed gap lists are cheap and ~30% wrong: testing showed an agent confidently reporting "missing" safeguards that already existed, because it reviewed a summary instead of the source. A gap report is only worth reading if every gap survived a check against the real artifacts.

## The contract

A finding may only appear in the final report as one of:

- **CONFIRMED** — you read the actual file/config/code and quote the line (or absence) that proves it. Include `file:line` or "checked <file>, section absent".
- **RESEARCH GAP** — a comparable system does X, this project verifiably does not. Cite the external source AND the local check.
- **OPEN QUESTION** — you could not verify (file unreadable, behavior only observable at runtime). Say exactly what check would settle it.

Anything that is none of these dies in your notes. Never pad the report with unverified plausibilities — a short verified list beats a long impressive one.

## Method

1. **Read the real thing.** The actual skill/plan/spec/config files — never work from a summary of them, including the user's own summary. List which files you read at the top of the report.
2. **Inventory implicit claims.** Every "X is handled" the project assumes. Each claim is a gap candidate.
3. **Fresh research pass** (frontier topics: last ~30 days first; use a Google-grounded CLI like `agy` plus your harness's web search — delegated, not in the main loop). Question: what do the closest comparable systems have that this one lacks? Guardrail vocabulary: iteration caps, no-progress detection, cost budgets, idempotent resume, staleness handling, single points of failure, rollback, credential expiry, silent-failure monitoring.
4. **Verify each candidate against source** (step 1 files). This kills the false gaps — expect to kill a third.
5. **Cross-verify the top 3** with one external pass (a gate CLI or ONE high-tier subagent): "Here is the claimed gap and the evidence — refute it."
6. **Report:** ranked by real-world hit probability. Each entry: classification, evidence, cheapest fix. Append the confirmed list to the project's `decisions.md` or run log.

## Red flags — stop and correct

- A finding with no file/line or source citation
- Reviewing the user's description of the system instead of the system
- Report longer than the evidence supports ("18 gaps" where 6 are checked)
- Skipping the research pass because "I already know the failure modes"
