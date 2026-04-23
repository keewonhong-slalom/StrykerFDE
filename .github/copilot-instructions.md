# Stryker FDE — Context Repository

This repo is the single source of truth for the Stryker FDE project's institutional knowledge.
It stores raw inputs and AI-processed outputs from discussions, meetings, design sessions, and other artifacts.

## Purpose

- Capture raw artifacts (meeting notes, design docs, images/diagrams) in `raw/`
- Store processed, synthesized, or AI-generated outputs in `context/`
- Enable future AI agents and team members to query and build on stored context

## Folder Structure

```
raw/           # Unedited or minimally edited source material
  meetings/    # Meeting notes, discussion transcripts
  design/      # Design documents, architecture decision records (ADRs)
  media/       # Images, diagrams, exported files
context/       # AI-generated or human-synthesized outputs
  summaries/   # Condensed summaries of raw artifacts
  decisions/   # Extracted decisions and action items
  analyses/    # Deeper analysis or synthesis across multiple artifacts
```

## Conventions

- **File naming**: descriptive kebab-case with an ISO date prefix where relevant — `2026-04-23-kickoff-meeting.md`
- **Raw files**: store as-is; do not edit for style. Add a one-line frontmatter comment if the source is not obvious.
- **Context files**: include a `Source:` link or reference to the raw artifact(s) they were derived from.
- **Images/diagrams**: store under `raw/media/`; reference them from processed docs with relative paths.

## AI Task Guidelines

When working in this repo, Copilot should:

- **Summarize** raw documents into concise, action-oriented processed summaries in `context/summaries/`
- **Extract** decisions and action items into `context/decisions/` with owner and due-date fields where inferable
- **Link** related artifacts by adding a `Related:` section at the bottom of context outputs
- **Answer questions** by searching across both `raw/` and `context/` before responding
- **Write or edit** context outputs in clear, professional prose suitable for an engineering audience
- **Never overwrite** raw source material — treat `raw/` as append-only

## Project Context

**FDE** = Field Development Engineering (Stryker business unit context; update this line as needed)
Ask the user for clarification if domain terminology is ambiguous.
