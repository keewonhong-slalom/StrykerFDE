---
description: "Use when: generating today's daily summary, summarizing meeting transcripts for a date, running end-of-day notes, creating the daily digest. Trigger phrases: 'generate daily summary', 'summarize today', 'run daily notes', 'create daily digest for [date]'."
name: "Generate Daily Summary"
argument-hint: "Date to summarize (e.g. 04-29, today, yesterday). Defaults to today."
agent: "Daily Summary Agent"
---

Run the Daily Summary Agent for the date provided (or today if none given).

- Accept date formats: `04-29`, `2026-04-29`, `April 29`, `today`, `yesterday`
- Normalize to the `MM-DD` folder format for locating files under `raw/`
- Read all files in `raw/<MM-DD>/`, synthesize into a structured daily summary, save to `documentation (output)/<YYYY-MM-DD>-daily-summary.md`, and generate a Teams channel message
