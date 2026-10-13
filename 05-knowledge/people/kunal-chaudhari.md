---
type: reference
domain: professional
updated: "2026-09-21"
tags:
  - people
  - crm
---

# Kunal Chaudhari

## Compiled Truth

### Executive Snapshot
- On a 27 Aug 2026 call, raised that BookScan shows the US book market declining 10-15%/yr historically but ~20-25% since Dec 2025; suspects this is partly a BookScan measurement artifact, since BookScan misses an estimated 60-70% of independently-published titles — a segment he believes is growing fast. [Source: Meeting/Call with Kunal Chaudhari.docx | 2026-08-27 | confidence: high]
- Corrected the assumption that Keepa is a superset of BookScan: the two panels are complementary but only partially overlapping. His view: use Keepa for market shape/size, BookScan for direct competitor comparison. [Source: Meeting/Call with Kunal Chaudhari.docx | 2026-08-27 | confidence: high]

### Role & Responsibilities
- Co-owns the competitor/market-sizing problem at Packt alongside Arjun's team; the book-publishing-side data contact (per Amit Ramadas Manikketh's recommendation). [Source: Session Notes - Book Market Database & SP-API.md | 2026-08-28 | confidence: high]
- Stated data-ask priority order: (1) Keepa-based market size, (2) Brand Analytics user behavior, (3) Amazon Advertising API (keyword/competitor-ASIN click attribution across ~13,000-30,000 ad campaigns) as a secondary layer; also wants pricing-to-conversion analysis (sale price vs list price) for Packt and competitor titles via Keepa, segmented by vertical. [Source: Meeting/Call with Kunal Chaudhari.docx | 2026-08-27 | confidence: high]

### Working Style
- Runs the competitor/market-sizing process personally — a monthly job with 2-3 scripts per taxonomy vertical run by hand; called this a bus-factor risk himself, and separately assessed the 2024 scripts he built with Raaj Sarma as "really bad" (his own words). [Source: Meeting/Call with Kunal Chaudhari.docx | 2026-08-27 | confidence: high]
- Drafting a taxonomy ticket (skill -> vertical/tool/language labels) for Arjun's team to automate against; explicitly noted Arjun's team "might not use the same scripts" as his own. [Source: Meeting/Call with Kunal Chaudhari.docx | 2026-08-27 | confidence: medium]

### Strengths
- Independently validated the (then-existing) Keepa rank-to-units estimator against BookScan and found it "wildly off" (outside a 10% margin) for ~60-70% of titles, worse at both distribution extremes (over-predicts weak titles, under-predicts strong ones); did this analysis with AI assistance under time pressure from stakeholder Dave. [Source: Meeting/Call with Kunal Chaudhari.docx | 2026-08-27 | confidence: high]

### Collaboration Notes
- His team later handed Arjun a production successor model (model_v7, a two-stage hurdle model) for review; Arjun's 17 Sept 2026 independent review found its headline 78-81% "within-2x" accuracy claim was in-sample only (no held-out fold), with a genuine out-of-sample rebuild showing 5-9 points lower accuracy, weakest in the fast-growing Independent Creator/Amazon-native segment. [Source: Competitor Analysis/handover_ds/model_v7_Review_Process_and_Findings.md | 2026-09-17 | confidence: high]

### Open Threads
- Whether Kunal's taxonomy ticket and Arjun's automation script will align (unresolved as of 28 Aug 2026). [Source: Session Notes - Book Market Database & SP-API.md | 2026-08-28 | confidence: low]

---

## Timeline (Append-Only)

### 2026-08-27
- Call with Arjun: raised BookScan decline anomaly, corrected Keepa/BookScan overlap assumption, shared validation findings on the Keepa rank-to-units estimator, stated data-ask priorities, and described the manual monthly market-sizing process as a bus-factor risk. [Source: Meeting/Call with Kunal Chaudhari.docx | 2026-08-27 | confidence: high]

### 2026-08-28
- Referenced in session notes as co-owner of the competitor/market-sizing problem and drafter of a taxonomy ticket; open question on alignment with Arjun's automation script. [Source: Session Notes - Book Market Database & SP-API.md | 2026-08-28 | confidence: medium]

### 2026-09-17
- Team's model_v7 (two-stage hurdle model) reviewed independently by Arjun; in-sample accuracy claim did not hold up out-of-sample, particularly in the Independent Creator/Amazon-native segment. [Source: Competitor Analysis/handover_ds/model_v7_Review_Process_and_Findings.md | 2026-09-17 | confidence: high]
