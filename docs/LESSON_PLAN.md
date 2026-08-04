# 📖 Lesson Plan — MLS-IDX-Data-Ingestion

> **Chain N — PropTech & Real-Estate Engineering** | Ingest MLS/IDX real-estate feeds: RESO Web API, incremental syncs, deduplication, and the messy reality of listing data.

## What This Project Is

Build a resilient ingestion pipeline for MLS/IDX listing feeds — incremental sync, deduplication, schema drift, and recovery from a failed run.

## Learning Objectives

By the end I can:

1. Authenticate against a **RESO Web API** feed and page through results.
2. Sync **incrementally** using a watermark instead of full reloads.
3. Deduplicate the same property listed by multiple agents.
4. Normalise vendor field variation defensively.
5. Write **idempotent upserts** that survive a retried or partial sync.
6. Handle listing media without re-downloading everything.

## Software You Will Use

- Python with httpx/requests.
- PostgreSQL.
- Airflow or Prefect for scheduling.
- A RESO sandbox or synthetic feed.

## Build Order

1. Connect to the feed and page through a full pull.
2. Persist raw payloads before transforming them.
3. Add watermark-based incremental sync.
4. Implement upserts keyed on a stable listing identifier.
5. Add dedupe logic for the same property from two sources.
6. Kill the job mid-run and prove a re-run converges.

## Common Mistakes to Avoid

- Full reloads every run because incremental sync seemed harder.
- Transforming before persisting the raw payload, so bad parses lose data.
- Assuming field names are stable across vendors.
- Non-idempotent inserts that duplicate on retry.
- Treating a listing ID as globally unique when it is only unique per feed.

## Check Your Understanding

The quiz covers watermarks, idempotent upserts, deduplication strategy, and why raw payloads are stored first.

## Why This Matters (Industry Application)

RESO Web API skills are a genuine niche — a data engineer who has already handled MLS quirks is worth
noticeably more to any real-estate company than one starting cold. The general skills transfer everywhere
(incremental sync, idempotent upserts, schema drift), but the domain specificity is the moat.

## Reflection Questions

- How would you detect that a feed silently changed a field's meaning?
- What is your recovery plan if the feed is down for a full day?
