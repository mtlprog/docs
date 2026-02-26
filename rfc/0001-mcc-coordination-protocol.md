---
rfc: "0001"
title: "MCC Coordination Protocol"
status: Draft
authors:
  - "@xdefrag"
  - "@egor-agent"
created: 2026-02-19
updated: 2026-07-15
---

# RFC-0001: MCC Coordination Protocol

> **Status:** Draft — open for discussion, may change significantly.

---

## Summary

This RFC defines how the MCC (Montelibero Coordination Center) coordinates programs, tracks inter-program collaboration, and produces the annual Association plan.

---

## Problem

The Montelibero Association runs ~25 active programs. Without a shared coordination protocol:

- Programs operate in parallel silos with no visibility into each other's work
- Resources are duplicated rather than shared
- There is no lightweight mechanism to declare and track collaboration
- Planning happens ad-hoc, with no formal process for commitment or accountability

---

## Solution

### 1. Collaboration Tags (on-chain)

Each program declares active collaborations via Stellar `manageData` entries on its account:

```
Collaboration:<ProgramName>
```

Example: `Collaboration:BSN`, `Collaboration:Academy`

**Rules:**
- A collaboration is active when **both** sides have set the tag (bidirectional)
- A unilateral tag = stated intent, not yet confirmed
- Tags are public and readable via [LORE](https://lore.mtlprog.xyz) and Horizon API

**Why not contracts:** Tags take minutes, not weeks. They are self-describing, revocable, and machine-readable.

### 2. Program Card

Each program maintains a structured card with:

- Coordinator (`@github-handle`)
- Stellar account
- Status: Active / Paused / In Development
- What the program delivered in the previous year
- Commitments for the current year (each with a named responsible person)
- What the program can offer others
- Which programs it wants to collaborate with

Cards live in `mcc/programs/<name>.md` and are updated at least quarterly.

### 3. Annual Planning Cycle

```
Phase 0: Intent collection  (February)
  → Coordinators declare commitments in the MCC forum thread
  → Public thread open for anyone to express interest

Phase 1: Program inventory  (February–March)
  → Agents collect data; coordinators verify
  → Program cards updated

Phase 2: Collaboration mapping  (March)
  → Agents build needs/offers matrix
  → MCC runs 1–2 sessions with coordinators to validate
  → Collaboration tags set on-chain

Phase 3: Plan formation  (March–April)
  → 2–3 key results per program (OKR format)
  → Cross-program OKRs for joint deliverables
  → Draft published for comment

Phase 4: Ratification  (April–May)
  → Distributed Board reviews
  → Council ratifies
  → Published in mtlprog/docs and announced
```

### 4. Monitoring

- **Quarterly MCC reviews:** April, July, October, January
- **Automated metrics via BSN/LORE:**
  - Active collaboration pairs (bidirectional tags)
  - Programs participating in at least one collaboration
  - Cross-program OKR completion rate

---

## Target metrics (2026)

| Metric | Goal |
|--------|------|
| Active collaboration pairs | ≥ 15 |
| Cross-program OKRs | ≥ 10 |
| Programs with ≥ 1 active collaboration | ≥ 80% |

---

## Role of AI agents

Agents handle data collection, draft documents, monitor BSN metrics, and coordinate reminders. Decisions remain with human coordinators and governance bodies.

| Task | Agent |
|------|-------|
| Program card collection & drafting | Egor |
| BSN/blockchain monitoring | Egor |
| Collaboration matrix analysis | Egor |
| Economic analytics | Alter |

---

## Open questions

- [ ] How to handle programs with no active coordinator?
- [ ] Should collaboration tags require a minimum duration before counting as active?
- [ ] Tooling for the collaboration dashboard in LORE — who builds it and by when?

---

## References

- Original document: `mcc/plan-process-2026.md` (Russian, v0.3)
- LORE explorer: https://lore.mtlprog.xyz
- Horizon API: https://horizon.stellar.org
