# AIPM Reference Repo — Claude Configuration

This repo is a Teamapt AIPM onboarding repository. It uses the PM Coaching plugin for
structured artifact creation.

## Repo identity

- **Platform:** TAPT (Teamapt — pre-platformisation)
- **Platform code:** TAPT
- **Onboarding manager:** Idris Aliyu (ialiyu@teamapt.com)
- **Process reference:** https://aipm-process.development.moniepoint.com/

## Repo structure

- `capabilities/` — platform-level capability anchors (do not edit without Idris approval)
- `subcapabilities/` — team-level subcapabilities (APM owns)
- `epics/` — epic and story files (APM owns)
- `release/` — change spec for the current working branch
- `templates/` — blank templates to copy

## ID conventions

| Artifact | Format | Example |
|---|---|---|
| Capability | `CAPABILITY-TAPT-[4-CHAR]` | `CAPABILITY-TAPT-DDBT` |
| Subcapability | `SUBCAP-TAPT-[CAP-4CHAR]-[4-CHAR]` | `SUBCAP-TAPT-DDBT-MAND` |
| Epic | `EPIC-[SUBCAP-ID]-EP[00001]` | `EPIC-TAPT-DDBT-MAND-EP00001` |
| Story | `STORY-[EPIC-ID]-[00001]` | `STORY-TAPT-DDBT-MAND-EP00001-00001` |

## Capabilities in this repo

| ID | Name | APM |
|---|---|---|
| CAPABILITY-TAPT-DDBT | Direct Debit Operations | Nancy Muorah |
| CAPABILITY-TAPT-DISB | Disbursement Processing | Ezinne Ogoke |
| CAPABILITY-TAPT-COLL | Collections and Payments | David Redemi |
| CAPABILITY-TAPT-PTSP | Terminal Service Provider Operations | Mark Momoh |
| CAPABILITY-TAPT-TPPC | Third Party Processing | Ruth Adetunji |
| CAPABILITY-TAPT-TRXN | Transaction Processing Suite | Khadijat Musa |
| CAPABILITY-TAPT-MCOB | Monnify Channels and Onboarding | Toluwanimi Maku |

## Behaviour rules

- Capabilities in `capabilities/` are owned by the Head of Platform (Idris). Do not modify them without explicit approval.
- Each APM works only on their own subcapabilities and epics.
- Always run the pre-merge gate before committing an epic file.
- Jira sync flows Git to Jira — never edit Jira stories manually after sync.
- The `release/` folder on the main branch contains the worked example. On a working branch, it contains the APM's active change spec.

## Worked example

The full worked example lives on the `main` branch:
- `subcapabilities/SUBCAP-TAPT-DDBT-MAND.md` — Direct Debit Mandate Management
- `epics/EPIC-TAPT-DDBT-MAND-EP00001.md` — Mandate Creation and Activation
- `release/change-spec.md` — Change spec for the above

Read these before creating your first artifact.
