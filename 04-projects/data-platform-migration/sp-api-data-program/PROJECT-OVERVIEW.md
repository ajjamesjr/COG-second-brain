---
type: project-overview
project: SP-API Data Program
slug: sp-api-data-program
parent_project: data-platform-migration
created: 2026-09-21
status: active
tags: ["#project", "#overview", "#amazon", "#sp-api"]
---

# SP-API Data Program

## What is this project?
The effort to make full use of Packt's existing Amazon selling-partner access (Vendor Central 1P + Brand Analytics) [Source: Amazon/SP-API Data Program - Vendor & Seller Data Opportunity.docx | 2026-08-28 | confidence: high]. Current production use is narrow: only two metrics — unit sales (Vendor Sales report) and glance views (Brand Analytics) — feed the Book Market Database, despite a much wider 2021 Brand Analytics grant (buy-box %, real-time hourly sales, basket data, switching, search-term rank, repeat-purchase %, demographics) that was never operationalized into a running pipeline [Source: Amazon/SP-API Data Program - Vendor & Seller Data Opportunity.docx | 2026-08-28 | confidence: high]. In other words: Packt has held broad Amazon data-access rights for years, and the gap this project addresses is between what's *granted* and what's *plumbed*.

## Current Status
As of the 28 Aug 2026 v3 draft, Data & Analytics (Arjun's team) reframed its role from "build 8 ML models ourselves" (the earlier v2 framing) to "support stakeholder builds" — shared Databricks access, taxonomy mapping, technical spikes [Source: Amazon/SP-API Data Program - Vendor & Seller Data Opportunity.docx | 2026-08-28 | confidence: high]. That's a deliberate scope-down: rather than D&A owning model development, it owns the shared infrastructure and lets domain owners build on top of it.

Two stakeholder-led builds are proceeding independently:
- [[../../../05-knowledge/people/amit-ramadas-manikketh|Amit Ramadas Manikketh]]'s P3 platform — review-sentiment analysis, A+ Content/listing-change attribution, with Databricks as a shared source [Source: Amazon/SP-API Data Program - Vendor & Seller Data Opportunity.docx | 2026-08-28 | confidence: high].
- [[../../../05-knowledge/people/kunal-chaudhari|Kunal Chaudhari]]'s competitor-intelligence work — Amazon Advertising API access, pricing-to-conversion data [Source: Amazon/SP-API Data Program - Vendor & Seller Data Opportunity.docx | 2026-08-28 | confidence: high].

On 27-28 Aug 2026, Arjun ran prep calls with both stakeholders ahead of a discovery call pitching two starting projects (competitor dashboard, Amazon data) to the P3 team [Source: Meeting/Data Catchup.docx | 2026-08-27 | confidence: medium].

## Key Open Questions
These recur across almost every source document and are unresolved as of the last review:

- **Vendor vs. Seller status.** Why Packt is an Amazon Vendor rather than a Seller is unresolved — [[../../../05-knowledge/people/amit-ramadas-manikketh|Amit]] didn't know the answer when asked directly [Source: Meeting/Data Catchup.docx | 2026-08-27 | confidence: medium]. This isn't cosmetic: Vendor vs. Seller status determines which SP-API report families and dashboards Packt can even see.
- **Dashboard staleness.** Vendor Central's promotion/coupon dashboards run 10-15 days stale; whether SP-API reports would actually be faster is untested [Source: Amazon/SP-API Data Program - Vendor & Seller Data Opportunity.docx | 2026-08-28 | confidence: medium].
- **No review access.** Packt as a Vendor doesn't get access to its own product reviews; a prior escalation attempt (by someone named Gemma) got no result [Source: Session Notes - Book Market Database & SP-API.md | 2026-08-28 | confidence: medium]. This is a direct blocker for Amit's review-sentiment build — if the underlying review data isn't accessible via the vendor relationship, his P3 platform has to source it another way (likely scraping, which carries its own risk — see below).
- **Missing attribution tooling.** A missing UTM-tracking/link-attribution tool (Bit.link was supposed to solve it, didn't) blocks tying CRM "endorsement" events to unit/glance-view momentum [Source: Meeting/Data Catchup.docx | 2026-08-27 | confidence: medium]. Without this, marketing can't prove that an endorsement or campaign drove a sales bump — the causal chain from CRM event to Amazon metric is broken at the link layer.
- **Shared account-block risk.** Whether Amit's review-sentiment scraping and Kunal's Keepa-based scraping carry the same Amazon account-block risk is untested [Source: Amazon/SP-API Data Program - Vendor & Seller Data Opportunity.docx | 2026-08-28 | confidence: low]. If both workstreams scrape against the same underlying Amazon account or IP range, a block triggered by one could take down the other.

## Recommended Next Steps
From the v3 doc [Source: Amazon/SP-API Data Program - Vendor & Seller Data Opportunity.docx | 2026-08-28 | confidence: high]:
1. Turn on Databricks as a shared Amazon data source, so both stakeholder builds (Amit's and Kunal's) draw from one plumbed pipeline instead of duplicating ingestion work.
2. Scope Advertising-API access for Kunal — his #2 priority behind Keepa-based market sizing.
3. Run technical spikes on three specific unknowns before committing further: the sale-price field, promotion freshness (does SP-API actually beat the 10-15 day Vendor Central lag), and the Vendor-vs-Seller question.

## People Involved
- **Arjun James** — owner
- [[../../../05-knowledge/people/amit-ramadas-manikketh|Amit Ramadas Manikketh]] — P3 platform (review-sentiment, listing-change attribution)
- [[../../../05-knowledge/people/kunal-chaudhari|Kunal Chaudhari]] — competitor intelligence (Advertising API, pricing-to-conversion)

## Relationship to Other Projects
This is a sub-project of [[../PROJECT-OVERVIEW|Data Platform Migration]] — Packt's Amazon Vendor/Seller access underlies the source systems (Keepa, Amazon Brand Analytics, SP-API) that the sibling sub-project [[../book-market-database/PROJECT-OVERVIEW|Book Market Database & Competitor Analysis]] depends on, and that the platform migration's own source registry tracks as SRC-029/SRC-031 under Arjun's ownership.

## Project Resources
- [[braindumps/|Project Braindumps]]
- [[competitive/|Competitive Intelligence]]
- [[content/|Content & Assets]]
- [[planning/|Planning Documents]]
- [[resources/|Resources]]

## Notes
A general-purpose facilitator guide for vendor/Finance data-mapping workshops exists at `Meeting/vendor-data-workshop-guide.docx` [Source: Meeting/vendor-data-workshop-guide.docx | undated | confidence: medium]. It's reusable methodology material for the broader data-platform migration work rather than something specific to this initiative, but it's relevant if similar stakeholder discovery sessions are needed here — e.g. structuring the discovery call with the P3 team referenced above.

## Next Steps
- [ ] Run the discovery call with the P3 team pitching the competitor dashboard and Amazon data starting projects
- [ ] Get a definitive answer on Vendor vs. Seller status and its implications for report access
- [ ] Assess shared account-block exposure between Amit's and Kunal's scraping workstreams before either scales up

---

*This overview helps COG organize your project-related thoughts and updates.*
