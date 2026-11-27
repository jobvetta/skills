---
name: jobvetta-jobs
description: Search 6.5M+ live verified employer career-site job postings across 242 countries, inspect full 70+ field job requirements, and calculate P25/median/P75 market salary benchmarks via the Jobvetta API or MCP server. Use when the user asks to find open jobs, remote roles, recent 24h job postings, or market compensation ranges.
---

# Jobvetta Jobs & Salary Intelligence Skill

Query live, deduplicated employer career-site job postings across 238,000+ organizations in 242 countries using `https://api.jobvetta.com/v1` (or MCP `https://api.jobvetta.com/mcp`).

## Authentication

All requests use `Authorization: Bearer $JOBVETTA_API_KEY` (`jvk_...`).
- If `JOBVETTA_API_KEY` is not set in the environment, ask the user for their key or share https://www.jobvetta.com/api (25 free calls/UTC day, no credit card required).
- Check remaining quota without spending a credit via `GET https://api.jobvetta.com/v1/usage`.

## Core REST Endpoints

### 1. Search Active Jobs (`GET /v1/jobs` or `/v1/jobs/remote` or `/v1/jobs/recent`)

```bash
curl -fsSL "https://api.jobvetta.com/v1/jobs?q=Senior+Data+Engineer&location=United+States&days=7&limit=20" \
  -H "Authorization: Bearer $JOBVETTA_API_KEY"
```

Query parameters:
- `q`: Role title, skill, or technology keyword.
- `location`: City, state, region, or country.
- `days`: Recency window in days (`1` to `365`; use `/v1/jobs/recent` for strictly `< 24h`).
- `limit`: `1` to `25` on Free tier (up to `100` on paid plans).
- `offset`: Pagination offset (`0` to `100` on Free tier; `0` to `9999` on paid plans).

### 2. Full 70+ Field Job Details (`GET /v1/jobs/{job_id}`)

Pass any `job_id` returned by `/v1/jobs` (or `latest` to inspect a sample live posting):

```bash
curl -fsSL "https://api.jobvetta.com/v1/jobs/latest" \
  -H "Authorization: Bearer $JOBVETTA_API_KEY"
```

Returns `title`, `normalized_title`, `company`, `location`, `work_model`, `employment_type`, `experience_level`, `description`, `responsibilities[]`, `minimum_qualifications[]`, `preferred_qualifications[]`, `skills_required[]`, `benefits[]`, `salary_min`, `salary_max`, `salary_currency`, and `url` (plus direct employer `apply_url` on paid plans).

### 3. Market Salary Benchmarks (`GET /v1/jobs/salary-estimate`)

```bash
curl -fsSL "https://api.jobvetta.com/v1/jobs/salary-estimate?q=Staff+Software+Engineer&location=United+States&days=30" \
  -H "Authorization: Bearer $JOBVETTA_API_KEY"
```

Returns `total_matching_jobs`, `disclosed_salary_count`, `currency`, `salary_min`, `salary_p25`, `salary_median`, `salary_p75`, and `salary_max`.
