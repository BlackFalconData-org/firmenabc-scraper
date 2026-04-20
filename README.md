# FirmenABC Scraper

Scrape FirmenABC — Austria's largest business directory with 800,000+ companies. Keyword+location search, direct URLs, or full-sitemap crawl. Extracts balance sheet, Firmenbuchnummer, managers, VAT ID, contact, GPS. Incremental mode.

**[FirmenABC Scraper on Apify →](https://apify.com/blackfalcondata/firmenabc-scraper?fpr=1h3gvi)**

---

## Key features

**Search with filters** — Search by keyword and location.

**Incremental mode** — Only get new or changed listings since your last run. Content hash per listing — no duplicates, no re-processing.

**Change classification** — Track unchanged, expired across runs. Build audit trails of how listings evolve over time.

**Compact output** — Emit core fields only (AI-agent / MCP-friendly). Keeps response size small for LLM workflows.

**Result cap** — Stop after N listings. Set to 0 for the full catalog.

**Export anywhere** — Download as JSON, CSV, or Excel. Stream via Apify API, webhooks, or integrations with Make, Zapier, Airbyte, Keboola.

**Structured data** — Every listing returns the same schema with consistent field naming. All fields always present — `null` when unavailable, never omitted.

---

## Use cases

**Data pipeline automation**
Integrate with your ETL pipeline to collect structured listings from the source on a schedule. Export to CSV, JSON, or directly to your database. Use compact mode to control output size.

**Market research**
Monitor listings, track trends, and analyze market dynamics with structured, deduplicated data from the source.

**Change monitoring**
Run daily or hourly in incremental mode to capture only new, updated, or expired listings. Perfect for price-tracking, churn analysis, and alerting pipelines.

**Lead generation**
Extract employer contact details alongside listings to build outreach lists for recruiters, staffing agencies, or B2B sales teams.

**AI / LLM training data**
Structured JSON per listing is ready for RAG pipelines, embeddings, and agent workflows. Compact mode trims tokens for LLM context windows.

---

## Quick start

```json
{
  "query": "Bäckerei",
  "location": "Wien",
  "maxResults": 10
}
```

---

## Input parameters

| Parameter | Type | Default | Description |
|-----------|------|---------|-------------|
| `query` | string | — | Keyword to search for (e.g. "Bäckerei", "IT-Dienstleistungen", "Steuerberater"). Combine with location to narrow results. |
| `location` | string | — | Austrian federal state or city to filter by (e.g. "Wien", "Oberösterreich", "Graz"). Leave empty to search all of Austria. |
| `startUrls` | array | — | Optional: provide specific FirmenABC company detail URLs to scrape directly (e.g. https://www.firmenabc.at/wien-holding-gmbh_ocT). Ignored if query is set. |
| `maxResults` | integer | `100` | Maximum number of companies to return. 0 = no limit. Use a small number for testing. |
| `compact` | boolean | `false` | Return only core fields (name, url, address, telephone, vatId, rechtsform, changeType). Ideal for AI-agent and MCP workflows to reduce token usage. |
| `incrementalMode` | boolean | `false` | Only emit companies that are new or have changed since the last run. Requires stateKey. Saves cost on repeated runs. |
| `stateKey` | string | — | Unique identifier for this tracking session (e.g. "at-all-companies"). Required when incrementalMode is true. |
| `emitUnchanged` | boolean | `false` | When incremental mode is on, also emit companies with no detected changes (changeType=UNCHANGED). |
| `emitExpired` | boolean | `false` | When incremental mode is on, also emit companies that disappeared since the last run (changeType=EXPIRED). |

---

## Output fields

Every listing returns the same 42-field schema. Missing values are `null` — never omitted.

- `listingId`
- `name`
- `rechtsform`
- `city`
- `region`
- `telephone`
- `email`
- `website`
- `vatId`
- `firmenbuchnummer`
- `balanceTotalAssets`
- `balanceYear`
- `url`
- `changeType`
- `fax`
- `street`
- `postalCode`
- `country`
- `latitude`
- `longitude`
- `logoUrl`
- `categories`
- `foundingDate`
- `balanceNetIncome`
- `balanceFixedAssets`
- `balanceEquity`
- `balanceCurrentAssets`
- `balanceProvisions`
- `balanceLiabilities`
- `balanceReceivables`
- `balancePrepaidExpenses`
- `managers`
- `listingKey`
- `portalUrl`
- `sourceDomain`
- `scrapedAt`
- `firstSeenAt`
- `lastSeenAt`
- `previousSeenAt`
- `expiredAt`
- `trackedHash`
- `stateKey`

---

## Pricing

Pay only for what you extract. No subscription required — Apify's free $5 credit covers thousands of results.

| Event | Price (USD) |
| --- | --- |
| Actor Start | $0.005 |
| Business details extracted | $0.004 |
| Business found | $0.0015 |

See the [actor on Apify](https://apify.com/blackfalcondata/firmenabc-scraper?fpr=1h3gvi) for current pricing.

---

## FAQ

**How much does it cost?**
Pay-per-event pricing — you only pay for listings extracted. Apify's free $5 credit is enough to run thousands of results before you pay anything.

**How does incremental mode work?**
Each listing gets a content hash. On subsequent runs, only new or changed listings are emitted — saving time, compute, and storage. Expired listings can be tracked separately.

**Do I need an API key or credentials?**
No. Just sign up for Apify, paste your input, and click Start. No credit card required.

---

## Related products by Black Falcon Data

- [StepStone Scraper](https://apify.com/blackfalcondata/stepstone-scraper?fpr=1h3gvi) — Job listings from 18 European portals
- [Indeed Job Scraper](https://apify.com/blackfalcondata/indeed-job-scraper?fpr=1h3gvi) — Indeed job listings with salary data
- [Glassdoor Job Scraper](https://apify.com/blackfalcondata/glassdoor-job-scraper?fpr=1h3gvi) — Glassdoor listings with company ratings
- [Arbeitsagentur Scraper](https://apify.com/blackfalcondata/arbeitsagentur-scraper?fpr=1h3gvi) — Germany's official job portal (1M+ listings)
- [SEEK Scraper](https://apify.com/blackfalcondata/seek-scraper?fpr=1h3gvi) — Australia & NZ's largest job board
- [Naukri Scraper](https://apify.com/blackfalcondata/naukri-scraper?fpr=1h3gvi) — India's largest job portal

---

## Getting started with Apify

New to Apify? [Create a free account with $5 credit](https://console.apify.com/sign-up?fpr=1h3gvi) — no credit card required.

1. Sign up — $5 platform credit included
2. Open [FirmenABC Scraper](https://apify.com/blackfalcondata/firmenabc-scraper?fpr=1h3gvi) and configure your input
3. Click **Start** — export results as JSON, CSV, or Excel

Need more later? [See Apify pricing](https://apify.com/pricing?fpr=1h3gvi).

---

## About Black Falcon Data

Black Falcon Data builds production-grade web scrapers for job boards and marketplace data. Browse our full actor catalog at [www.blackfalcondata.com](https://www.blackfalcondata.com).

---

*Last updated: 2026 04*
