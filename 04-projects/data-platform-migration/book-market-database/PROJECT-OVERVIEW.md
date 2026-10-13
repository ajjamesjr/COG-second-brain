---
type: project-overview
project: Book Market Database & Competitor Analysis
slug: book-market-database
parent_project: data-platform-migration
created: 2026-09-21
status: active
tags: ["#project", "#overview", "#amazon", "#bookscan", "#modeling"]
---

# Book Market Database & Competitor Analysis

## What is this project?
Sizes the competitive US book market beyond Packt's own titles by combining three data panels: NPD/Circana BookScan (verified POS but reactionary, covers only the top ~10,000 US titles), Keepa (broad Amazon-scrape coverage, up to ~673,000 ASINs in 2024, proxy signals only), and Amazon Brand Analytics (first-party, Packt titles only) [Source: Session Notes - Book Market Database & SP-API.md | 2026-08-28 | confidence: high]. Feeds a Power BI project (`Competitor Analysis/Book Market Database.pbip` + Report + SemanticModel) and a standalone HTML dashboard artifact. Scope is the Computers & Technology category on Amazon (98% of titles), all print formats (79% paperback, 19.4% hardcover) [Source: Competitor Analysis/handover_ds/handover_ds/QUESTIONS.md, via internal pipeline review | 2026-09-17 | confidence: high].

Each panel alone is insufficient: BookScan is trustworthy but blind to ~98% of the catalog by title count, Keepa is broad but a proxy (sales rank, not units), and Brand Analytics only covers Packt's own titles. The project exists to reconcile the three into one usable market picture.

## Business Driver
[[../../../05-knowledge/people/kunal-chaudhari|Kunal Chaudhari]] flagged (27 Aug 2026) that BookScan shows the US book market declining 10-15%/yr historically, but ~20-25% since Dec 2025 — possibly a BookScan measurement artifact from undercounting independently-published titles (BookScan misses an estimated 60-70% of them) — a question a stakeholder named [[../../../05-knowledge/people/dave|Dave]] is pushing urgency on [Source: Meeting/Call with Kunal Chaudhari.docx | 2026-08-27 | confidence: high]. The stakes are directly business-critical: if the decline is real, it changes strategic planning; if it's a panel-coverage artifact, the company would be reacting to a measurement error.

## Central Technical Problem
Estimating true unit sales for the ~660,000+ titles outside BookScan's panel. Three separate, largely uncoordinated modeling attempts have been made:

1. **Publisher-level OLS model.** R²=0.359, Durbin-Watson 0.663 (flags autocorrelation), 87 duplicate rows, 87% of imprints tagged "Unknown" [Source: Session Notes - Book Market Database & SP-API.md | 2026-08-28 | confidence: high]. Weak fit and a data-quality problem (imprint tagging) that undermines any aggregation by publisher.
2. **Single-feature title-level log-linear model.** `log(units) ~ log(30-day avg Keepa sales rank)`, trained on ~1,800 Packt titles, R²=0.70 in log space — but extrapolates absurdly, predicting ~5.79M units/month at rank #1 against a training max of 1,538. Independently confirmed "wildly off" by Kunal Chaudhari [Source: Session Notes - Book Market Database & SP-API.md | 2026-08-28 | confidence: high]. A single-feature log-linear fit trained on a narrow (Packt-only) range has no business extrapolating four orders of magnitude beyond its training data.
3. **`model_v7`** — a two-stage hurdle model (HistGradientBoosting classifier + regressor on log(units), monotone in rank, Duan-smeared, calibrated), handed over by Kunal Chaudhari's team, now in production in the pipeline scripts, replacing the old `predicted_units` column [Source: Competitor Analysis/handover_ds/model_v7_Review_Process_and_Findings.md | 2026-09-17 | confidence: high].

## Validation Finding
Arjun's independent 17 Sept 2026 review of `model_v7` found the handover's claimed accuracy (78-81% "within-2x") was in-sample only — the shipped model was trained on 100% of the data with no held-out fold. A genuine 5-fold GroupKFold cross-validation gave materially lower out-of-sample accuracy: 69-76% within-2x annually, only 59% at monthly granularity — a 5-9 point gap per fiscal year, weakest in the Independent Creator/Amazon-native segment (only 11.6% of that catalog has a BookScan-tracked ISBN; the model estimates 582k FY2026 units vs. BookScan's 73k visible) [Source: Competitor Analysis/handover_ds/model_v7_Review_Process_and_Findings.md | 2026-09-17 | confidence: high]. The strong point: the classifier separating "sells vs. doesn't" has AUC 0.93 [Source: Competitor Analysis/handover_ds/model_v7_Review_Process_and_Findings.md | 2026-09-17 | confidence: high] — the model is good at the binary question, materially weaker at the continuous unit-volume estimate, and weakest exactly where the market-decline debate (independently-published, Amazon-native titles) needs it to be strong.

## External Framing vs. Internal Record
The polished external-facing brief (`Competitor Analysis/Book Market Radar - Competitor Intelligence.docx`, v3) deliberately describes the rank-to-units estimator as "a completed, well-received pilot" whose precision "wasn't at the level needed to replace NPD" — softer language than the raw findings above. Day-to-day reporting currently reverts to NPD/BookScan as the trusted baseline, with the model's output kept as supplementary color [Source: Competitor Analysis/Book Market Radar - Competitor Intelligence.docx | 2026-08-28 | confidence: high]. Worth keeping this gap visible: the internal technical record (in-sample-only claims, a 5-9 point cross-validated accuracy gap, weakest performance exactly in the segment the market-decline question is about) is more open and more uncertain than the external brief's language suggests.

## Supporting Workstream: WMDB Tagging
A separate LLM-batch pipeline (OpenAI Batch API, gpt-5) classifies the 1.2M-row book/product catalog against a taxonomy. Currently only the TechPro/NotTechPro dimension is wired end-to-end; 9 other planned taxonomy dimensions — audience, skills, tones, tools, types, usps, vendors, languages, cert — are defined but not yet coded into a batch/parse pipeline. As of the last run, only ~186,610 of 1.2M rows (~15%) have been tagged and combined [Source: internal pipeline inspection of WMDB Tagging/ directory | 2026-09-21 | confidence: high].

This taxonomy work feeds `model_v7`'s vertical/skill/audience/approach features directly — and those features were themselves flagged in the 17 Sept review as generated by unaudited LLM-labelling batches with documented prior errors: one run had 67 of 95 skill strings "subtly wrong" from being typed from memory rather than copied verbatim [Source: Competitor Analysis/handover_ds/model_v7_Review_Process_and_Findings.md | 2026-09-17 | confidence: high]. That's a second, compounding data-quality risk sitting underneath the model's already-weaker segment: feature inputs generated by an unaudited process feed a model that's already least reliable in the Independent Creator segment.

## Open Questions
From the pipeline handover's QUESTIONS.md, unresolved as of Sept 2026 [Source: Competitor Analysis/handover_ds/handover_ds/QUESTIONS.md, per internal review | 2026-09-17 | confidence: high]:
- Panel restatement/backfill mechanics when Keepa is re-scraped monthly — does a missing title-month mean zero sales or an uncaptured title? Flagged as mattering most for aggregation.
- Missing listing-date/first-seen endpoints — only ~10% of titles pre-order enough to infer time-to-market.
- Confirmation that the scrape's intended scope (US, Computers & Technology, all print formats) matches what BookScan calibration assumes.

## Recommended Next Steps
From the Book Market Radar brief [Source: Competitor Analysis/Book Market Radar - Competitor Intelligence.docx | 2026-08-28 | confidence: high]:
1. Stabilize ingestion & cleaning first — automate the personally-run monthly Keepa pipeline into Databricks bronze→silver and fix the 87%-"Unknown" publisher tagging.
2. Treat further estimator investment as a business decision, not a default next sprint — the cross-validated accuracy gap means more modeling work isn't obviously the highest-leverage move until ingestion is stable.
3. Automate taxonomy mapping once Kunal's labels land, replacing the current unaudited manual/memory-based labelling process.

## People Involved
- **Arjun James** — owner/reviewer
- [[../../../05-knowledge/people/kunal-chaudhari|Kunal Chaudhari]] — co-owns market-sizing, model_v7 handover
- [[../../../05-knowledge/people/karan|Karan]] — runs the WMDB scraping scripts, flagged training data as 2+ years old
- [[../../../05-knowledge/people/raaj-sarma|Raaj Sarma]] — ran historical Keepa scrape jobs
- [[../../../05-knowledge/people/erol|Erol]] — owns product-detail scraping team
- [[../../../05-knowledge/people/oliver-huggins|Oliver Huggins]] — senior leadership, board-level visibility
- [[../../../05-knowledge/people/dave|Dave]] — drives urgency on the market-decline question

## Relationship to Other Projects
This is a sub-project of [[../PROJECT-OVERVIEW|Data Platform Migration]], not a separate initiative — its evidence is directly inside that engagement's BA corpus. Arjun's own "Book Market Radar" brief is filed as evidence record `EV-0006`; he's registered as stakeholder `ST-012` and as owner of source systems `SRC-029` (Keepa) and `SRC-031` (Amazon Brand Analytics) in the platform's own registry. `REQ-0011` (self-published market coverage) is the live, not-yet-`agreed` requirement thread that would fold this project's rank-to-units work into the future Databricks platform, currently blocked on `Q-0014` (accuracy bar). See the parent overview for the full platform-side picture, including how deep Arjun's own involvement in that BA corpus runs beyond this one evidence document. Also see the sibling sub-project [[../sp-api-data-program/PROJECT-OVERVIEW|SP-API Data Program]], which covers the underlying Amazon Vendor/Seller access this project's Keepa and Brand Analytics feeds depend on. [Source: packt-data-platform-v2 repo, EV-0006, REQ-0011, registry/stakeholders.yml, registry/source-systems.yml | 2026-09-21 | confidence: high]

## Project Resources
- [[braindumps/|Project Braindumps]]
- [[competitive/|Competitive Intelligence]]
- [[content/|Content & Assets]]
- [[planning/|Planning Documents]]
- [[resources/|Resources]]

## Next Steps
- [ ] Confirm with the data-platform-migration workstream whether the Keepa bronze→silver migration is shared scope
- [ ] Decide whether to invest further in `model_v7` improvement or hold at current accuracy given the cross-validation findings
- [ ] Push resolution on the taxonomy-labelling audit given the documented "subtly wrong" error rate feeding model features

---

*This overview helps COG organize your project-related thoughts and updates.*
