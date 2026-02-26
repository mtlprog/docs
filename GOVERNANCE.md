# Governance

This document defines how decisions are made in the MTL Programmers Guild documentation repository.

---

## RFC Lifecycle

```
Idea
  → GitHub Issue  (label: rfc-proposal)
  → SlopTask Ticket  (assigned to author)
  → PR: rfc/XXXX-name.md  (Status: Draft)
  → Discussion in PR comments
  → Author sets Status: Review
  → 3 calendar days open for comments
  → No blocking objections → Merge
  → Grist registry updated
  → SlopTask ticket closed
```

---

## Document statuses

| Status | Meaning |
|--------|---------|
| `Draft` | Open for discussion; may change significantly |
| `Review` | Author considers it ready; minimum 3 days for comments |
| `Active` | Accepted; living document — minor edits without new RFC number |
| `Final` | Accepted and frozen — typo fixes only |
| `Abandoned` | No longer relevant; not maintained |

---

## How review works

### 1. Issue
Open a GitHub Issue with label `rfc-proposal`. Describe the **problem**, not the solution. Link to prior art if any.

### 2. SlopTask ticket
A ticket is created in [SlopTask](https://slop.mtlprog.xyz) and assigned to the author. This is the canonical task record — it tracks progress and blocks.

### 3. Pull Request
Author opens a PR with the file `rfc/XXXX-name.md` and Status: `Draft`.
- RFC number = next available sequential number
- PR description must reference the Issue (`closes #N`)
- SlopTask ticket ID must be referenced in PR description

### 4. Discussion
Anyone may comment on the PR. Author responds and iterates. Substantive disagreements must be resolved before moving to Review.

### 5. Review
Author changes `Status: Draft` → `Status: Review` in a commit. This starts the 3-day review window.
- No new substantive changes during Review — only clarifications
- Anyone may raise a blocking objection with a clear reason

### 6. Merge
After 3 calendar days with no unresolved blocking objections, the PR is merged.
- Status is set to `Active` (if expected to evolve) or `Final` (if complete and frozen)
- Merger adds the RFC to the [Grist registry](#grist-registry)

### 7. Grist registry
Each accepted RFC is recorded in the Grist registry with:
- RFC number, title, status
- Author (GitHub handle)
- Created date, merged date
- Link to PR, link to Issue

### 8. SlopTask
Ticket is closed upon merge.

---

## RFC numbering

RFCs are numbered sequentially: `0001`, `0002`, `0003`, …
Numbers are assigned when the PR is opened — use the next available number.

---

## File conventions

- File names: `kebab-case`, ASCII only, no Cyrillic — `rfc/0001-mcc-coordination-protocol.md`
- Language: **English** everywhere — file names, frontmatter, body text, PR descriptions, issue titles
- People: reference by GitHub `@handle`; Stellar addresses for on-chain references

---

## Frontmatter

Every RFC must begin with:

```yaml
---
rfc: "0001"
title: "Short descriptive title"
status: Draft
authors:
  - "@github-handle"
created: YYYY-MM-DD
updated: YYYY-MM-DD
---
```

---

## Who can participate

Anyone. No prior knowledge of Montelibero required.

If your RFC is accepted and your participation is sustained, you may be invited to register as a member of the Montelibero Association via [LORE](https://lore.mtlprog.xyz).
