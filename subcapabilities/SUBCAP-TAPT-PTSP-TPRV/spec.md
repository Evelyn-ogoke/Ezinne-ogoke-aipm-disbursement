---
id: SUBCAP-TAPT-PTSP-TPRV
name: Terminal Provisioning
capability: CAPABILITY-TAPT-PTSP — Terminal Service Provider Operations
platform: TAPT — Teamapt (pre-platformisation)
status: active
personas:
  - operations-team
  - agent
  - merchant
channels:
  - INTERNAL_SYSTEM
problem: |
  Terminal provisioning is tightly coupled to Moniepoint's internal operations,
  making it difficult for Teamapt to offer PTSP services to other PTSP operators
  who want to outsource terminal provisioning and management without taking on
  the associated operational overhead. There is no decoupled provisioning path
  that allows backoffice admins to assign and manage terminals on behalf of
  external PTSP operators independently of Moniepoint's own estate.
design_refs:
engineering_refs:
deprecation_reason:
---

## Description

Terminal Provisioning covers the end-to-end flow by which Teamapt and Moniepoint
backoffice admins provision POS terminals and assign them to registered merchants
or super agents. The subcapability decouples provisioning from Moniepoint's
internal estate, enabling Teamapt to offer PTSP services to third-party PTSP
operators who wish to outsource terminal operations without the associated
operational overhead.

All terminal assignment actions are subject to a maker-checker gate: the admin
who initiates an assignment cannot also approve it. Terminals already assigned
to Moniepoint cannot be reassigned to other merchants or super agents.

## Success Metrics

| Metric | Target |
|---|---|
| Agent onboarding cycle time (terminal provisioning leg) | <= 3 business days |

## Scope Boundaries

**In scope**
- Decoupled terminal provisioning supporting assignment to any fully onboarded
  registered merchant or super agent across multiple PTSP operators
- Backoffice-initiated terminal assignment via INTERNAL_SYSTEM with mandatory
  maker-checker approval gate
- Hard block on reassignment of already-assigned Moniepoint terminals to any
  other merchant or super agent
- Rejection of assignment attempts targeting merchants or super agents not yet
  fully onboarded in the system
- Rejection of duplicate terminal serial number submissions
- Graceful failure and retry path when TMS is unavailable during a provisioning
  attempt

**Out of scope**
- Physical terminal logistics and delivery tracking
- Terminal decommissioning, recall, or swap
- Self-service terminal requests initiated by merchants or agents directly
- Terminal configuration beyond assignment (parameter loading, key injection)

## Dependencies

- **TMS** — Terminal Management System must be reachable for all provisioning
  and assignment operations
- **Agent records** — assignee must exist as a fully onboarded agent in the
  platform before assignment can proceed
- **Merchant records** — assignee must exist as a fully onboarded merchant in
  the platform before assignment can proceed
- **Maker-checker framework** — platform-level approval workflow must be
  available; maker and checker must be distinct users

## Open Questions

- Should the maker-checker gate be synchronous (assignment pending until
  checker acts) or asynchronous with a timeout escalation?
- Is there a maximum number of terminals assignable to a single merchant or
  super agent, or is this uncapped at the platform level?
