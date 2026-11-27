# Jobvetta Official Claude Code Plugin, Gemini CLI Extension & Agent Skills

Official AI Agent Skills (`SKILL.md`), **Claude Code Plugin**, and **Gemini CLI Extension** for [Jobvetta](https://www.jobvetta.com) - covering 6.5M+ live verified employer career-site job postings across 238,000+ companies in 242 countries.

## 1. Install in Claude Code (Plugin + Skills + MCP)

```bash
/plugin marketplace add jobvetta/skills
/plugin install jobvetta@jobvetta
```

## 2. Install via `skills.sh` (Cursor, Copilot, Windsurf, Codex, OpenClaw, Antigravity)

```bash
npx skills add jobvetta/skills
```

## 3. Install in Gemini CLI

```bash
gemini extensions install https://github.com/jobvetta/skills
```

## Included Skills & MCP Tools

- **`jobvetta-jobs`** (`skills/jobvetta-jobs/SKILL.md`): Search 6.5M+ live employer postings, retrieve 70+ field structured job details, and benchmark P25/median/P75 market salaries.
- **`company-hiring-signals`** (`skills/company-hiring-signals/SKILL.md`): Enrich B2B accounts, sales prospects, and investment research with live employer hiring velocity and open headcount by department.
- **Bundled MCP Server (`.mcp.json`)**: Connects `jobvetta-mcp` (`search_jobs`, `get_company_jobs`, `estimate_salary`, `get_job`, `get_usage`).

## API Key

Generate a free Jobvetta API key (`25` calls/day, no credit card required) at **https://www.jobvetta.com/api** and set `export JOBVETTA_API_KEY=jvk_...`.
