# MLS-IDX-Data-Ingestion

### Ingest MLS/IDX real-estate feeds: RESO Web API, incremental syncs, deduplication, and the messy reality of listing data.

![Chain N](https://img.shields.io/badge/Chain%20N-059669?style=for-the-badge) [![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue?style=for-the-badge)](LICENSE-GPL) [![License: AGPL v3](https://img.shields.io/badge/License-AGPLv3-blue?style=for-the-badge)](LICENSE-AGPL)

[📖 Lesson Plan](docs/LESSON_PLAN.md)

<!-- SCREENSHOT PLACEHOLDER: docs/screenshots/overview.png -->

> ⬜ **Scaffold pending.** Directory created to portfolio standard; full content (README, lesson plan, tour + quiz, skeleton code) still to be built. Part of **Chain N — PropTech & Real-Estate Engineering**.

## Why This Was Built

Listing data is the lifeblood of every real-estate product, and it arrives in the least convenient form
imaginable — vendor-specific feeds, inconsistent field names, photos by URL, and records that change
underneath you. Anyone building in this space hits MLS/IDX ingestion on day one.

I want to build the pipeline properly: pull incrementally rather than re-downloading everything, detect
what actually changed, dedupe the same property listed by two agents, and survive a feed that goes down
mid-sync. This is unglamorous plumbing, and it's exactly the kind of thing that decides whether a PropTech
product works.

## Why This Matters (Industry Application)

RESO Web API skills are a genuine niche — a data engineer who has already handled MLS quirks is worth
noticeably more to any real-estate company than one starting cold. The general skills transfer everywhere
(incremental sync, idempotent upserts, schema drift), but the domain specificity is the moat.

## Topics Covered

| Area | What this project covers |
|------|--------------------------|
| RESO Web API | The industry standard feed format and its authentication model |
| Incremental sync | Watermarks and change detection instead of full reloads |
| Deduplication | One property, several listings — matching and merging |
| Schema drift | Vendor field variation and defensive normalization |
| Idempotency | Upserts that survive a retried or partial sync |
| Media handling | Photo URLs, ordering, and refresh policy |

## How This Connects

Chain N (PropTech & Real-Estate Engineering). Applies the pipeline patterns from **Web-Scraper-Postgres-Pipeline** and **Chain D**; feeds listings to the AVM and geospatial projects.

---
Dual licensed — [GPL v3](LICENSE-GPL) and [AGPL v3](LICENSE-AGPL).
