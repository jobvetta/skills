---
name: company-hiring-signals
description: Retrieve live employer job openings, department hiring velocity, and tech-stack hiring signals for B2B account enrichment, GTM outbound research, and company due diligence via the Jobvetta API. Use when analyzing what roles, departments, tools, or geographies a target company is actively hiring for.
---

# Jobvetta Company Hiring Signals Skill

Inspect open headcount and hiring velocity directly from an organization's official career portal via `GET https://api.jobvetta.com/v1/companies/{company}/jobs`.

## Authentication

Set `Authorization: Bearer $JOBVETTA_API_KEY` (`jvk_...`, free key with 25 calls/day at https://www.jobvetta.com/api).

## Workflow

1. **Fetch Total Open Roles & Sample Openings for Target Company**:
   URL-encode the company name (for example `Datadog`, `Cisco%20Systems`, `Stripe`):
   ```bash
   curl -fsSL "https://api.jobvetta.com/v1/companies/Datadog/jobs?limit=25" \
     -H "Authorization: Bearer $JOBVETTA_API_KEY"
   ```
2. **Filter by Department, Tooling, or Geography**:
   Pass `q` (for example `Security`, `Kubernetes`, `Account Executive`, `GenAI`) and/or `location` to measure targeted team expansion:
   ```bash
   curl -fsSL "https://api.jobvetta.com/v1/companies/Datadog/jobs?q=Security&location=United+States&limit=25" \
     -H "Authorization: Bearer $JOBVETTA_API_KEY"
   ```
3. **Hydrate Tech Stack & Requirements**:
   Pass `job_id` from key roles to `GET https://api.jobvetta.com/v1/jobs/{job_id}` to extract `skills_required[]`, `responsibilities[]`, and `salary_min`/`salary_max` as concrete buying-intent and budget signals.
