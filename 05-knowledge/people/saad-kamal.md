---
type: reference
domain: professional
updated: "2026-09-21"
tags:
  - people
  - crm
---

# Saad Kamal

## Compiled Truth

### Executive Snapshot
- Packt's data platform lead (registered as stakeholder ST-004 in the `packt-data-platform-v2` repo's registry) and the sole decider of record on all six architecture decisions (DEC-0001 through DEC-0006) governing the data platform migration. [Source: packt-data-platform-v2 repo, ba-corpus/decisions/DEC-0001..0006 | 2026-09-21 | confidence: high]

### Role & Responsibilities
- Owns platform-level architecture decisions for the Databricks migration: chose Databricks on AWS as the single data engine (replacing Redshift, Airflow, dbt, Meltano, Fivetran, Matillion, and Hevo entirely), decided 21 Aug 2026, explicitly accepting higher platform spend in exchange for a smaller team. [Source: packt-data-platform-v2 repo, ba-corpus/decisions/DEC-0001 | 2026-08-21 | confidence: high]
- Decided the rebuild is greenfield, not lift-and-shift — each legacy source is onboarded "as a business process," not reproduced as a table (DEC-0002); also decided infrastructure-as-code/CI-CD/RBAC from day one (DEC-0003), a GitHub monorepo (DEC-0004), Linear for work tracking (DEC-0005), and a metadata-driven architecture over pipeline-per-process (DEC-0006). [Source: packt-data-platform-v2 repo, ba-corpus/decisions/DEC-0002..0006 | 2026-09-21 | confidence: high]

### Working Style
- Not yet established from available sources — only one commit under his account (`saadk-packt`) in the repo; his decisions are recorded via the DEC record process rather than direct code contribution. [Source: packt-data-platform-v2 repo, git shortlog | 2026-09-21 | confidence: medium]

### Open Threads
- Not yet directly contacted by Arjun in the source material reviewed so far — connection is currently through the shared platform repo (Arjun is ST-012, a registered stakeholder and source-system owner in the same registry Saad's decisions govern). [confidence: low]

---

## Timeline (Append-Only)

### 2026-08-21
- Decided DEC-0001: Databricks on AWS as the platform's data engine, decommissioning the full legacy stack. [Source: packt-data-platform-v2 repo, ba-corpus/decisions/DEC-0001 | 2026-08-21 | confidence: high]

### 2026-09-21
- Confirmed as decider of record on DEC-0002 through DEC-0006 (greenfield scope, IaC/CI-CD/RBAC, GitHub monorepo, Linear, metadata-driven architecture). [Source: packt-data-platform-v2 repo, ba-corpus/decisions/DEC-0002..0006 | 2026-09-21 | confidence: high]
