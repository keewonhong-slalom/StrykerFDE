---
description: "Use when: committing and pushing changes, end-of-day git push, staging and committing daily work, pushing repo updates. Trigger phrases: 'commit and push', 'push changes', 'stage and push', 'commit today's work'."
name: "Commit and Push"
argument-hint: "Optional commit message override. If omitted, message is generated from today's summary."
agent: "agent"
tools: [run_in_terminal, read_file, file_search]
---

Stage all changes, write a commit message derived from today's work, and push to origin.

## Step 1 — Check Status

Run `git status` in the repo root (`/Users/keewonhong/Desktop/Stryker/FDE Repo/StrykerFDE`).

- If there is nothing to commit, tell the user and stop.
- List the files that are staged or unstaged.

## Step 2 — Stage All Changes

Run `git add -A` to stage all untracked and modified files.

## Step 3 — Write the Commit Message

If the user provided a commit message argument, use it exactly.

Otherwise, derive a conventional commit message automatically:
1. Look for a daily summary file in `documentation (output)/` matching today's date (e.g. `2026-04-29-daily-summary.md`).
2. If found, read the **Key Information & Highlights** section and use it to write a concise message.
3. Format: `docs(<MM-DD>): <one-line summary of what was added or changed>`
   - Examples:
     - `docs(04-29): add daily summary, raw transcripts, and Teams message for 04-29`
     - `docs(04-28): add debrief and daily meeting transcripts with summary`
4. If no summary file exists, fall back to a generic message based on the staged files: `docs: add <date> raw transcripts and output`.

Keep the message under 72 characters.

## Step 4 — Commit

Run `git commit -m "<message>"` with the message from Step 3.

## Step 5 — Pull and Push

1. Run `git pull --rebase` to incorporate any remote changes.
2. If the rebase succeeds, run `git push`.
3. If there are conflicts, stop and describe them to the user — do not attempt to resolve automatically.

## Step 6 — Confirm

Report the final commit hash, message, and branch that was pushed. Confirm success to the user.
