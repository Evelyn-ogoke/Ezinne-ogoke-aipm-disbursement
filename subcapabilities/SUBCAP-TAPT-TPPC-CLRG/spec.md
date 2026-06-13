---
id: SUBCAP-TAPT-TPPC-CLRG
name: Aptpay Clearing Tool
capability: CAPABILITY-TAPT-TPPC — Third Party Processing
platform: TAPT
status: active
personas:
  - partner-institution
  - operations-team
  - developer
channels:
  - API
  - INTERNAL_SYSTEM
problem: Acquirers using MPGS and CyberSource payment gateways must manually extract
  transaction data from daily gateway files (MPGS Draft Capture Files, CyberSource TC 33
  Capture Files), segregate on-us transactions, and produce separate clearing files for
  each card scheme. This process is labour-intensive, error-prone, and causes delays in
  end-of-day clearing and settlement.
design_refs:
engineering_refs:
deprecation_reason:
---

## Description

The Aptpay Clearing Tool automates the end-of-day clearing process for acquirers that
route transactions through MPGS and CyberSource gateways. It ingests raw gateway files,
parses and extracts transaction data, performs on-us transaction segregation, and
produces scheme-compliant clearing output files (Visa IPM, Mastercard Base II) alongside
settlement and transaction reports in CSV format. Output files are written to a designated
output folder for downstream submission to card schemes — submission itself is handled
outside the system. The tool eliminates manual data extraction, reduces handling errors,
and compresses the end-of-day clearing cycle.

## Success Metrics

| Metric | Target |
|---|---|
| Output generation time after input file upload | Seconds (TBD baseline after first run) |
| Settlement report accuracy vs. spec | 100% |
| Transaction report accuracy vs. spec | 100% |
| Clearing file validation pass rate (e.g. clearing optimizer) | 100% |

## Scope Boundaries

**In scope:**
- Ingestion of MPGS Draft Capture Files (DCF) and CyberSource TC 33 Capture Files
- Parsing and extraction of transaction data from gateway files
- On-us transaction segregation
- Production of scheme-compliant clearing files: Visa IPM and Mastercard Base II
- Generation of settlement report (CSV)
- Generation of transaction report (CSV)
- Handling of known failure modes: malformed gateway files, missing or duplicate
  transactions, late file arrival, and scheme format validation failures

**Out of scope:**
- Submission of clearing files to Visa/Mastercard (handled outside the system after
  output folder generation)
- Settlement reconciliation (handled within CAPABILITY-TAPT-TPPC)
- Dispute and chargeback initiation (handled within CAPABILITY-TAPT-TPPC)
- Scheme connectivity (handled within CAPABILITY-TAPT-TPPC)

## Dependencies

- MPGS providing Draft Capture Files (DCF) on a daily cadence
- CyberSource providing TC 33 Capture Files on a daily cadence
- Visa IPM format specification (scheme-defined)
- Mastercard Base II format specification (scheme-defined)
- CAPABILITY-TAPT-TRXN — Transaction Processing Suite, for on-us transaction
  reference data used during segregation

## Open Questions

- What is the defined SLA for file arrival from MPGS and CyberSource? Late arrival
  handling behaviour may need parameterising.
- Should the tool support multiple gateway files in a single run (batch), or one
  file per run?
