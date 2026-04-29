---
description: "Use when: moving transcripts, importing meeting notes, staging daily files, moving downloads to raw folder for a date. Trigger phrases: 'move transcripts', 'import today's files', 'stage transcripts for [date]', 'move downloads to raw'."
name: "Move Transcripts to Daily Folder"
argument-hint: "Date to stage files for (e.g. 04-29, today). Defaults to today if omitted."
agent: "agent"
tools: [run_in_terminal, list_dir, file_search]
---

Move all files from `~/Downloads/Daily Transcripts/` into the correct dated `raw/` folder in this repository.

## Step 1 — Resolve the Date

- If the user provided a date, accept formats like `04-29`, `2026-04-29`, `April 29`, `today`, or `yesterday`.
- If no date was provided, default to today's date.
- Normalize to the folder format used in this repo: `MM-DD` (e.g. `04-29`).

## Step 2 — Verify Source Folder

- Check that `~/Downloads/Daily Transcripts/` exists and is not empty.
- List the files found and confirm with the user before moving if there are more than 5 files.
- If the folder is empty or does not exist, tell the user and stop.

## Step 3 — Ensure Target Folder Exists

- Target path: `raw/<MM-DD>/` within the repo root (`/Users/keewonhong/Desktop/Stryker/FDE Repo/StrykerFDE/raw/<MM-DD>/`).
- If the folder does not exist, create it.

## Step 4 — Move Files

- Move all files from `~/Downloads/Daily Transcripts/` into the target folder using `mv`.
- Do NOT copy — move, so the source folder is emptied.

## Step 5 — Confirm

- List the contents of the target `raw/<MM-DD>/` folder after moving.
- Confirm how many files were moved and their names.
- Suggest running the Daily Summary Agent next: "Run the daily summary agent for <MM-DD> to generate notes from these files."
