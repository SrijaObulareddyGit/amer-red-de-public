# AMER Red Accounts — Digital Engagement RCA Dashboard (Public Methodology Demo)

A redacted, methodology-only copy of an OrgCS executive dashboard that performs
root-cause analysis on the AMER-region Red Accounts carrying open Service –
Digital Engagement (DE) Support cases.

**All customer-identifying content has been removed.** Account names, account
IDs, case numbers, owner names, case subjects, case descriptions, and customer
verbatim quotes have been replaced with stable pseudonyms (`Account 01`,
`ACCT-01`, `CASE-0001`, `Owner 01`, …) or redacted outright. What remains is
the structure, the filter/UX behaviour, the driver taxonomy, and the ranking
methodology — not any real customer data.

Open [`index.html`](./index.html) in a browser.

## What the dashboard shows

- **Executive summary KPIs** – open DE case count, affected account count,
  Sev 1/Sev 2 counts, DE share of open red volume.
- **Success Plan filter + Attribution filter** – sticky controls that scope
  every section below (plan-level roll-ups, driver bars, highest-volume
  accounts, open-case table).
- **Section A – Red Accounts by Success Plan** – distribution of DE-impacted
  accounts across Signature, Premier, Premier+, Partner Premier, Basic,
  Standard, including plans with zero DE representation (reported honestly
  rather than silently omitted).
- **Section B – Highest-volume accounts** – per-account open-case roll-up
  with lifetime DE case count and open-DE share.
- **Section C – Top DE Support case drivers** (the headline analysis).
  - Horizontal bar chart of 16 drivers, descending by qualifying case count.
  - 16-row detail table: rank, driver, cases, % of total, distinct accounts,
    channel, representative cases, Omni/Messaging/Einstein chips, suggested
    investigation action.
  - **Counting rules** – each case contributes exactly one primary driver
    (first regex match wins); additional matches tracked as secondary so
    primary totals never double-count.
- **Section D – Signature vs Premier side-by-side** – top-7 drivers for
  each plan, so you can see where the DE pain pattern diverges by tier.
- **Section E – Critical / unresolved issues** – open Sev 1 / Sev 2 /
  escalated case table with per-case subject, status, record type.
- **Section F – Root-cause summary** – themes, release regressions,
  closed-but-recurring pattern, recommended P1/P2/P3 actions.
- **Section G – Data validation** – source scope definition, snapshot date,
  record-type validation, plan validation (including plans with zero DE
  overlap), proxy-field disclosures.

## Methodology notes

- **Scope filter**: `Open_Red_Account__c = true` AND `IsClosed = false` AND
  `Cloud__c = 'Service-Digital Engagement'` AND `RecordType.Name = 'Support'`
  AND `Account.Region__c = 'AMER'`.
- **Driver taxonomy**: 24 priority-ordered regex patterns over case subject +
  description, covering WhatsApp, SMS, Facebook/Instagram DM, SCV/Command
  Center, Einstein Bots & Agentforce, Einstein AI (summarization / knowledge /
  replies), BYOC, Omni-Channel routing & queue, Agent capacity/presence,
  MIAW / Embedded Service, chat/messaging session errors, Enhanced Messaging,
  Flow/Screenflow, API integration, performance, Email-to-Case, SSO, push
  notifications, reporting/analytics, pricing/billing, case data, deployment,
  follow-up. Pattern-match order encodes conflict-resolution priority.
- **No fabrication**: in the live internal version, every account name, plan
  tier, severity, status, case number, and subject is pulled verbatim from
  Salesforce via SOQL — no synthetic examples. Here, all identifying tokens
  are pseudonymised post-hoc.

## What this public repo is **not**

- Not a live link. The file is a static snapshot.
- Not a reusable library. Everything is inlined into one HTML file so it can
  be shared as a single artifact.
- Not source-of-truth data. The internal copy of this report is maintained
  in a separate, access-controlled Salesforce internal GHE repository.

## File inventory

```
index.html                 # the dashboard (sanitised)
amer-red-accounts-de.html  # identical copy under the original filename
README.md                  # this file
```
