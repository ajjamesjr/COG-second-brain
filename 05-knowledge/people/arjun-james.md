---
type: reference
domain: professional
updated: "2026-09-23"
tags:
  - people
  - crm
---

# Arjun James

## Compiled Truth

### Executive Snapshot
- ST-012 in the packt-data-platform-v2 BA corpus (Packt's data-platform migration engagement, delivered by Oakland); registered stakeholder and owner of two source systems: Keepa (SRC-029) and Amazon Brand Analytics (SRC-031). [Source: packt-data-platform-v2 repo, registry/stakeholders.yml, registry/source-systems.yml | 2026-09-21 | confidence: high]
- His own "Book Market Radar" brief (filed as `EV-0006`) is the corpus's primary source for competitor/market-intelligence data, and is what first put Keepa, Amazon Brand Analytics, and NPD/Circana BookScan onto the platform team's source registry. [Source: packt-data-platform-v2 repo, EV-0006, docs/architecture/current-state/04-market-intelligence.mmd | 2026-09-21 | confidence: high]
- Beyond that one cited document, he turns up as a direct participant or facilitator across at least five more BA corpus sessions unrelated to his own market-intelligence work — see Role & Responsibilities.

### Role & Responsibilities
- Owns SRC-029 (Keepa) and SRC-031 (Amazon Brand Analytics) in the platform's source-system registry. [Source: packt-data-platform-v2 repo, registry/source-systems.yml | 2026-09-21 | confidence: high]
- Facilitates the first of three finance sales-channel knowledge-transfer sessions (`EV-0021`, 2026-09-08) — functioning as an Oakland-side session facilitator on this engagement, not only as a cited stakeholder. [Source: packt-data-platform-v2 repo, ba-corpus/evidence/EV-0021 | 2026-09-08 | confidence: high]
- Owns/reviews the Book Market Database & Competitor Analysis project, now organized as a sub-project of this same engagement (see [[../../04-projects/data-platform-migration/book-market-database/PROJECT-OVERVIEW|Book Market Database]]): ran the 17 Sept 2026 independent cross-validation review of `model_v7` that found its in-sample 78-81% accuracy claim didn't hold up out-of-sample. [Source: Competitor Analysis/handover_ds/model_v7_Review_Process_and_Findings.md | 2026-09-17 | confidence: high]

### Working Style
- Names data gaps directly and in real time rather than letting them pass: flagged live in the email-marketing discovery session that a weekly catalogue export he'd been handed "is not the full data" (`FND-0056`, `EV-0024`); reflected a finding back to a stakeholder mid-session on trade sales being invisible in BI ("so that is a missing or a hole in our current process," `FND-0061`, `EV-0022`); named the specific source of a recurring "the number is wrong" complaint about Power BI live in a session (`FND-0052`, `EV-0023`, 52:30). [Source: packt-data-platform-v2 repo, ba-corpus/findings/FND-0052,0056,0061 | 2026-09-08/22 | confidence: high]
- Corrects errors on the record rather than letting them stand: fixed an ASR mis-hearing of "Saad Khan" for "Saad Kamal" and named two team members (Karan Shinde, Parth Sethi) in the events-product discovery session (`EV-0017`, 58:09). [Source: packt-data-platform-v2 repo, ba-corpus/evidence/EV-0017 | 2026-09-08 | confidence: high]
- Acknowledges unused capability rather than overstating readiness: quoted in `Q-0002` confirming Packt already has Amazon SP-API access it isn't using ("we have access to it, it's just that we are not using it with this," 45:04). [Source: packt-data-platform-v2 repo, ba-corpus/questions/Q-0002 | 2026-09-21 | confidence: high]

### Strengths
- Independent, skeptical review of handed-over model claims: caught that `model_v7`'s headline accuracy figure was measured in-sample only, and ran a proper 5-fold GroupKFold cross-validation showing a 5-9 point accuracy gap — worst in the segment (Independent Creator/Amazon-native) that matters most for the market-decline question the project exists to answer. [Source: Competitor Analysis/handover_ds/model_v7_Review_Process_and_Findings.md | 2026-09-17 | confidence: high]

### Open Threads
- `REQ-0011` (self-published titles in competitor market reporting), drafted partly from his own `EV-0006` report, is still blocked on `Q-0014` (accuracy bar) — the requirement record itself flags that he's a participant in both corroborating sources. [Source: packt-data-platform-v2 repo, ba-corpus/requirements/REQ-0011 | 2026-09-21 | confidence: high]
- Whether the Keepa bronze→silver migration (proposed in his own `EV-0006` next-steps) becomes shared scope with the platform-migration workstream is unresolved. [Source: 04-projects/data-platform-migration/book-market-database/PROJECT-OVERVIEW.md | 2026-09-21 | confidence: medium]

---

## Timeline (Append-Only)

### 2026-08-28
- Session notes describe him co-owning the competitor/market-sizing problem with [[kunal-chaudhari|Kunal Chaudhari]], per Amit Ramadas Manikketh's recommendation. [Source: Session Notes - Book Market Database & SP-API.md | 2026-08-28 | confidence: high]

### 2026-09-08
- Facilitates finance sales-channel KT session 1 (`EV-0021`). [Source: packt-data-platform-v2 repo, ba-corpus/evidence/EV-0021 | 2026-09-08 | confidence: high]
- Named directly in the events-product discovery session (`EV-0017`), correcting an ASR mis-hearing and naming two team members. [Source: packt-data-platform-v2 repo, ba-corpus/evidence/EV-0017 | 2026-09-08 | confidence: high]

### 2026-09-09
- Registered as stakeholder ST-012 with corrected email (arjunj@packt.com) in the platform's stakeholder registry, after three prior instances of the wrong email (ajames@packt.com). [Source: packt-data-platform-v2 repo, registry/stakeholders.yml, EV-0006 | 2026-09-09 | confidence: high]

### 2026-09-10
- Named in finance KT session 3 (`EV-0023`) as the source of the "Marin May" reference explaining a recurring Power BI complaint. [Source: packt-data-platform-v2 repo, ba-corpus/evidence/EV-0023 | 2026-09-10 | confidence: high]

### 2026-09-17
- Ran an independent cross-validation review of `model_v7` (the Book Market Database's rank-to-units estimator), finding its claimed 78-81% within-2x accuracy was in-sample only. [Source: Competitor Analysis/handover_ds/model_v7_Review_Process_and_Findings.md | 2026-09-17 | confidence: high]

### 2026-09-22
- Speaks directly in the email-marketing discovery session (`EV-0024`), flagging that a weekly catalogue export is incomplete. [Source: packt-data-platform-v2 repo, ba-corpus/evidence/EV-0024 | 2026-09-22 | confidence: high]
