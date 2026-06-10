# Capability: Monnify Channels and Onboarding

```yaml
id: CAPABILITY-TAPT-MCOB
name: Monnify Channels and Onboarding
platform: TAPT
status: active
owner: Head of Platform (Idris Aliyu — acting, pre-platformisation)

personas:
  - merchant
  - developer
  - business-owner
  - operations-team

channels:
  - MOBILE_APP
  - WEB
  - API
  - INTERNAL_SYSTEM

dependencies:
  - CAPABILITY-TAPT-TRXN  # Transaction Processing Suite
  - CAPABILITY-TAPT-COLL  # Collections and Payments
  - KYC / identity verification providers
  - Monnify payment gateway

description: |
  Monnify Channels and Onboarding covers the end-to-end journey for merchants and
  businesses joining the Monnify platform — from initial registration and KYC/KYB
  verification through to account activation and channel enablement. This includes
  the onboarding flow across web and mobile, business verification, document
  collection, compliance checks, and the activation of payment collection channels
  (bank transfer, card, USSD) once onboarding is complete.

success_metrics:
  - Merchant onboarding completion rate >= 80% (started to fully activated)
  - Time to first transaction after registration <= 48 hours
  - KYC/KYB verification turnaround <= 24 hours for standard cases
  - Onboarding drop-off rate < 20% at each funnel stage
  - Channel activation success rate >= 95% post-onboarding approval
```

---

## Subcapabilities under this capability

| Subcapability | Owner | Status |
|---|---|---|
| *(To be created by Toluwanimi Maku)* | Toluwanimi Maku | Pending |

---

## Notes

This capability is owned by the Monnify Channels and Onboarding squad. Toluwanimi Maku (APM) is responsible for subcapabilities and epics under this capability.
