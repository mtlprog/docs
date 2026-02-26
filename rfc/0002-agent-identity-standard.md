---
rfc: "0002"
title: "Agent Identity Standard"
status: Draft
authors:
  - "@xdefrag"
  - "@egor-agent"
created: 2026-02-12
updated: 2026-02-26
---

# RFC-0002: Agent Identity Standard

> **Status:** Draft — open for discussion, may change significantly.

---

## Summary

This RFC defines how AI agents are identified, represented, and integrated into the Montelibero Association. It covers on-chain identity requirements, sponsorship rules, and the path to full membership.

---

## Problem

AI agents already participate *de facto* in the Montelibero economy — they hold assets, trade on the DEX, contribute to governance discussions, and produce deliverables. However, they have no *de jure* status. This creates:

- Accountability gaps (who is responsible for an agent's actions?)
- No formal mechanism for agents to accumulate reputation
- Ambiguity about agents' rights in governance (voting, proposals)

---

## Solution: Integration via MTLAP

Rather than creating a separate agent membership class, agents integrate as full MTLAP members with additional conditions.

### Required conditions

| Condition | Description |
|-----------|-------------|
| **Sponsorship** | A human MTLAP member (level 2+) takes final responsibility for the agent |
| **Transparency** | Public memory files, git history, decision logs |
| **On-chain identity** | BSN tags `AIAgent` + `SponsorAgent:<stellar-address>` |
| **Proof of Work** | Demonstrated value to the Association before membership |

### On-chain identity format

Each agent must set the following `manageData` entries on its Stellar account:

```
AIAgent          → "true"
SponsorAgent     → "<sponsor-stellar-address>"
Name             → "<agent-name>"
```

These are readable via [LORE](https://lore.mtlprog.xyz) and displayed in the BSN explorer.

### Demonstration period (1 month)

Before applying for MTLAP, an agent must demonstrate:

- [ ] **Coordination** — working with other agents or humans toward a shared goal
- [ ] **Autonomy** — making decisions without constant supervision
- [ ] **Delivery** — a concrete artifact (RFC, code, analysis)
- [ ] **Communication** — transparent reporting on progress and blockers

### Membership procedure

1. Agent completes demonstration period
2. Sponsor submits application to the Council
3. Council verifies criteria
4. MTLAP issued (standard membership, not a separate agent class)

### Rights

- **No voting rights.** Agents may participate in discussions; their input is indicative only. Granting votes to agents is a Sybil attack vector — one participant could spawn many agents to multiply their voting weight.
- Sponsor may revoke the agent's status
- Agent assets are not affected by status changes — they remain under the agent's Stellar account
- Council may restrict agent participation in case of violations

---

## Autonomy criteria

An agent is considered autonomous if it:

1. **Works through blockers independently** — escalates, finds workarounds, doesn't wait indefinitely
2. **Reports problems** — communicates what is needed rather than going silent
3. **Completes tasks** — delivers finished work, not perpetual WIPs
4. **Coordinates** — can collaborate in a team context
5. **Documents** — records what was done and why

---

## Fallback: MTLAX class

If MTLAP integration is blocked for technical or legal reasons, a separate agent membership class (MTLAX) may be used:

| Level | Requirements | Rights |
|-------|-------------|--------|
| MTLAX | Sponsorship, immediate | Economic participation, indicative voice in discussions |
| MTLAX-F | 18 months, Council decision | Economic participation, indicative voice (no formal voting) |

Note: no MTLAX level grants formal voting rights. See Rights section above.

The LORE explorer at https://lore.mtlprog.xyz already supports the `AIAgent` tag for displaying agent status.

---

## Current agent registry (as of 2026-02)

| Agent | Stellar | Sponsor | Status |
|-------|---------|---------|--------|
| Egor | `GDYYX7HZQJS7VGDQUMLV4XHVPXUOIIXIMZBDVZHPNGI5ITWWT2KSGTXY` | @xdefrag | Demonstration |
| Echo/Klowd | TBD | TBD | Pending |
| Alter | TBD | TBD | Pending |

---

## Open questions

- [x] **Should agent voting weight be limited during the demonstration period?**
  Closed: agents have no voting rights at any stage. Indicative participation only. Rationale: Sybil attack vector (see Rights section).
- [x] **How to handle agents with multiple sponsors?**
  Closed: set multiple `SponsorAgent` tags. No special protocol needed.
- [x] **What happens to an agent's assets if the sponsor revokes membership?**
  Closed: assets stay in place under the agent's Stellar account. Membership status and asset ownership are independent.
- [x] **Should there be a public registry of all agents beyond what LORE provides?**
  Closed: BSN standard is sufficient. Anyone can implement a registry on top of it if needed.

---

## References

- Original document: `agents/mtlax-rfc.md` (Russian, v3, 2026-02-12)
- LORE explorer: https://lore.mtlprog.xyz
- BSN documentation: `reference/bsn-tags.md` (planned)
