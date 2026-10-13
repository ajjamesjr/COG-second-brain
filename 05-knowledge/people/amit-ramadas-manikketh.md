---
type: reference
domain: professional
updated: "2026-09-21"
tags:
  - people
  - crm
---

# Amit Ramadas Manikketh

## Compiled Truth

### Executive Snapshot
- Runs a shadow BI tool scraping Amazon review sentiment (positive/negative, not just star rating), currently US-only and monthly; wants it extended to all territories and moved off scraping (Amazon account-block risk) onto native SP-API/Brand Analytics access via Databricks. [Source: Meeting/Data Catchup.docx | 2026-08-27 | confidence: high]
- New ask (27 Aug 2026): capture the go-live timestamp of any A+/Premium A+ Content, PDP metadata, or ad-campaign change and correlate it against subsequent glance views/units/rank/price; cites Amazon's own claim of ~+3-5% performance lift for standard A+ and ~+20% for Premium A+. Already has an A+ templating engine built — just needs the correlation layer. [Source: Meeting/Data Catchup.docx | 2026-08-27 | confidence: high]

### Role & Responsibilities
- Builds the "P3" data platform team; no longer works the book-publishing side (per his own statement), focused on building systems. [Source: Meeting/Data Catchup.docx | 2026-08-27 | confidence: high]

### Working Style
- Same review-sentiment tool correlates CRM "endorsement" events against subsequent glance-view/unit momentum shifts; blocked by lack of UTM tracking — a tool called "Bit.link" was meant to solve link-level attribution and doesn't. [Source: Meeting/Data Catchup.docx | 2026-08-27 | confidence: high]
- Separately runs a manual monthly O'Reilly review scrape (data owned by "Metallics") and wants it automated to daily/weekly via cron — O'Reilly doesn't block scrapers the way Amazon does. [Source: Meeting/Data Catchup.docx | 2026-08-27 | confidence: medium]

### Collaboration Notes
- Recommends Sunith and Kunal Chaudhari as the right people for book-publishing-side data questions. [Source: Meeting/Data Catchup.docx | 2026-08-27 | confidence: high]
- This 27 Aug call and the Kunal Chaudhari call were both prep for a 28 Aug 2026 discovery call where Arjun pitched two starting projects (competitor dashboard, Amazon data) to Amit's P3 platform team. [Source: Meeting/Data Catchup.docx | 2026-08-27 | confidence: medium]

### Open Threads
- Doesn't know why Packt is an Amazon Vendor rather than a Seller, when Arjun raised it directly. [Source: Meeting/Data Catchup.docx | 2026-08-27 | confidence: medium]

---

## Timeline (Append-Only)

### 2026-08-27
- Data catch-up call with Arjun: described shadow BI review-sentiment tool and its scaling/attribution blockers, O'Reilly scrape automation ask, new A+/PDP/ad-change correlation ask, and recommended Sunith and Kunal Chaudhari for book-publishing data questions. Could not explain Packt's Vendor-vs-Seller status when asked. [Source: Meeting/Data Catchup.docx | 2026-08-27 | confidence: high]
