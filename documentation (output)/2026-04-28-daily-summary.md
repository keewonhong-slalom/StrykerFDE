# Daily Summary — 2026-04-28

**Sources:**
- `raw/04-28/Stryker_ Quick Debrief.docx` — 42-minute debrief session (2:00 PM) where Victoria Austin, Rachel James, and Kee-Won Hong evaluated and compared the two use cases from the week's deep dives (Ortho Labeling and PMCH), aligned on prototype focus, and discussed tooling and workflow.
- `raw/04-28/Stryker FDE Team Daily Meeting.docx` — 19-minute daily standup (3:30 PM) with the same core team plus Jennifer Kwapis, covering next steps, scheduling follow-ups, work tracking, the FDE Flywheel process framework, and Obsidian/note-taking tooling.

---

## Key Information & Highlights

- **First deep dives completed this week.** The FDE team ran its first use case deep dives with two business units: Ortho Labeling and PMCH (Post-Market Complaints Handling). The team is now debriefing, prioritizing, and planning follow-ups.

- **PMCH is the higher-priority follow-up.** The team aligned that PMCH has more unknowns requiring a faster follow-up meeting, while Victoria has enough context on Ortho Labeling to begin prototyping independently.

- **PMCH prototype focus narrowed to the intake form.** The primary opportunity is an AI-powered intelligent intake form that improves user experience and pulls failure mode classification earlier in the process (currently the classifier runs too late, after the user is no longer interacting with the system). A 50-person team currently handles complaints manually — high volume, high value.

- **Ortho Labeling use case decomposed into sub-use cases.** Claude's analysis (and independent team thinking) confirmed these should be treated separately: (1) label revision, (2) label creation, and (3) system migration to Prism 360. Migration is low priority (one-time ETL); revision and creation are the prototype focus.

- **FDE team is unique in the broader organization.** Unlike other FTE pods that focus on delivering a specific use case, the FDE team is the first to evaluate and prototype use cases. No comparable process artifact exists elsewhere — they are building this process from scratch ("greenfield").

- **FDE Flywheel process document being developed.** Victoria created an initial "FDE Flywheel" page in OneNote describing the end-to-end FDE process for working a use case (deep dive → intake template → process shadow → prototype → future state diagram → productionization plan). The team intends to mature this into a formal checklist.

- **Work tracking to be set up.** The team agreed to establish a lightweight Kanban board (Microsoft Teams Planner or similar) to track use cases, prototype work, and backlog items. This will also support the prioritized use case list Alfonso has requested.

- **Swag scoring for Alfonso's Wednesday check-in.** The team plans to bring high-level priority scores (aligned to Alfonso's report format) for Ortho label revision and creation and PMCH to the midweek check-in. Rachel will take the first pass on PMCH.

- **Note-taking workflow changing.** The team agreed to move away from OneNote toward markdown-native note-taking (Obsidian or VS Code), with notes committed directly to the FDE repo's daily folder. Kee-Won is also exploring an O365 MCP connector as a potential bridge.

- **Data team follow-up deferred to ~May 5.** Not enough concrete data examples from use cases yet. Jennifer Kwapis will look at scheduling a meeting with the data team leader around the week of May 4–5.

---

## Decisions Made

1. **PMCH is higher-priority follow-up than Ortho Labeling.**
   - **Rationale:** More unknowns on PMCH; Victoria can progress independently on labeling without the follow-up.
   - **Owner:** Kee-Won Hong to schedule.

2. **Ortho label migration is out of scope for prototyping.**
   - **Rationale:** One-time ETL project, low ongoing value. Revision and creation are the prototype focus.
   - **Owner:** Full team aligned.

3. **PMCH prototype scope = AI-powered intelligent intake form only.**
   - **Rationale:** Production value requires the full system, but prototyping the form demonstrates the art of the possible and generates useful questions for the follow-up. Avoids scoping the full re-architecture of their current RPA/Power Automate solution.
   - **Owner:** Full team aligned.

4. **Claude will do first-pass scoring template completion; team will review and iterate.**
   - **Rationale:** Effective way to filter signal from noise on large transcripts; team reviews and corrects as needed.
   - **Owner:** Kee-Won Hong (workflow owner).

5. **Note-taking will move to markdown-native, committed directly to the FDE repo.**
   - **Rationale:** OneNote export-to-PDF workflow is not sustainable; markdown notes fed directly to Claude as context is the preferred approach. Each team member commits their own notes to a date-based folder.
   - **Owner:** Full team; trial on next deep dive.

6. **Work tracking: lightweight Kanban, low friction, accessible via Teams (e.g., Planner).**
   - **Rationale:** No mandatory Stryker tool identified; preference for something everyone can access without many barriers. Status deck remains communication vehicle.
   - **Owner:** Kee-Won Hong to set up.

7. **For Wednesday Alfonso check-in: present swag scores using his report column format.**
   - **Rationale:** Aligns FDE output with Alfonso's existing framework; demonstrates use cases are moving through stages, not stuck in ideation.
   - **Owner:** Rachel James and Kee-Won Hong to prepare scores.

---

## Action Items & Tasks

| # | Task | Owner | Due Date | Priority | Source |
|---|------|-------|----------|----------|--------|
| 1 | Diagram future state PMCH flow (art of the possible, focus on intake form) | Rachel James | Before PMCH follow-up | High | Quick Debrief |
| 2 | Begin solutioning / prototyping for Ortho label revision and creation | Victoria Austin | This week | High | Quick Debrief |
| 3 | Schedule PMCH follow-up meeting (same attendees as initial deep dive) | Kee-Won Hong | ASAP | High | Daily Meeting |
| 4 | Schedule Ortho Labeling follow-up (Kee-Won or Joel to message the group) | Kee-Won Hong / Joel | This week | Medium | Daily Meeting |
| 5 | Swag priority scores for PMCH use case (first pass) | Rachel James | By Wed 04-29 | High | Quick Debrief |
| 6 | Swag priority scores for Ortho use cases (label revision, creation, migration separately) | Kee-Won Hong | By Wed 04-29 | High | Quick Debrief |
| 7 | Set up lightweight Kanban/task board (Teams Planner or equivalent) | Kee-Won Hong | TBD | Medium | Daily Meeting |
| 8 | Set up prioritized use case list board (for Alfonso's report) | Kee-Won Hong | TBD | Medium | Daily Meeting |
| 9 | Get screenshot of Alfonso's report columns from Joe (for scoring alignment) | Victoria Austin / Team | By Wed 04-29 | Medium | Quick Debrief |
| 10 | Consolidate and move working docs to FDE Teams channel (not FDE Investment folder) | Full team | TBD | Low | Daily Meeting |
| 11 | Revisit data team follow-up; check whether concrete examples are ready | Kee-Won Hong | May 5 (in calendar) | Medium | Daily Meeting |
| 12 | Explore O365 MCP connector for OneNote (Teams permissions) | Kee-Won Hong | TBD | Low | Daily Meeting |
| 13 | Set up Obsidian + explore Git integration plugin | Kee-Won Hong | TBD | Low | Daily Meeting |
| 14 | Update FDE Flywheel OneNote page; team to add observations | Victoria Austin (primary) / Full team | TBD | Medium | Daily Meeting |
| 15 | Explore scheduling data leader meeting for the week of May 4–5 | Jennifer Kwapis | TBD | Medium | Daily Meeting |
| 16 | Trial markdown-native note-taking (Obsidian/VS Code → repo commit) on next deep dive | Full team | Next deep dive | Medium | Daily Meeting |

---

## Risks & Blockers

- **PMCH has a long tail to production value.** The prototype (intake form) can demonstrate the concept, but real value is only realized when the system is in the hands of field reps — requiring full productionization. This is a scope/expectation management risk with the business unit and Alfonso.
  - **Impact:** Could be perceived as an FDE effort beyond typical prototype scope if not framed carefully.
  - **Mitigation:** Frame prototype as "art of the possible" for the intake experience; defer re-architecture discussion.

- **RPA/UiPath dependency unknown.** It is unclear whether PMCH is locked into UiPath/Power Automate or open to alternative tooling. This affects both prototype scope and production pathway.
  - **Impact:** Could constrain solution approach significantly.
  - **Mitigation:** Ask in the follow-up meeting.

- **Prism 360 implications for Ortho Labeling not yet understood.** The team does not know whether Prism 360 is a storage system or an active review/approval platform, which affects how the label revision and creation prototype should integrate.
  - **Impact:** Could invalidate prototype approach if integration requirements are significant.
  - **Mitigation:** Clarify in Ortho follow-up meeting; add as agenda item.

- **PMCH Phase 1 architecture not fully understood.** The failure mode classification AI (Phase 1) exists but its inputs, outputs, and API surface are unknown. The prototype goal of "plugging it into the intake form earlier" depends on this.
  - **Impact:** May not be technically feasible or may require significant PMCH team involvement.
  - **Mitigation:** Deep dive on Phase 1 architecture in the follow-up meeting.

- **Insufficient data examples for data team follow-up.** Not enough concrete use case data patterns yet to bring to the Stryker data team with meaningful asks.
  - **Impact:** Delays data readiness assessment and any dependent work.
  - **Mitigation:** Deferred to May 5; Jennifer Kwapis flagged; continue deep dives to gather examples.

- **Note-taking/collaboration workflow in flux.** The team is mid-transition between OneNote and markdown/repo-native tooling. Until this is settled, context capture will be inconsistent.
  - **Impact:** Meeting notes and analysis context may not make it into the repo reliably.
  - **Mitigation:** Trial the new approach on the next deep dive; decision to be finalized then.

---

## Open Questions & Parking Lot

1. Is Prism 360 a data storage platform or an active label review/workflow tool? How does the current workflow interact with it for label revision and creation?
2. Why was the PMCH solution built with Power Automate/UiPath? Is the team open to replacing it, or is there a constraint?
3. What exactly is PMCH Phase 1 (deployed last year)? What are the inputs, outputs, and architecture of the failure mode classifier?
4. What are the exact scoring columns in Alfonso's prioritization report? (Rachel to share screenshot.)
5. Can Kee-Won get an O365 MCP connector for OneNote, or is it blocked by current Stryker permissions?
6. Is there value in a brief interview session with another FTE pod about their use case process, even if they focus on delivery rather than evaluation?
7. For the PMCH prototype, does the output need to reach SharePoint/Trackwise, or is the intake form itself sufficient to demonstrate value?
8. Can the PMCH failure mode classification be generalized to other complaint-handling processes elsewhere at Stryker?

---

## Next Steps & Follow-Ups

- **Wednesday, April 29 — Alfonso midweek check-in:** Come prepared with high-level swag scores for Ortho (revision, creation, migration as separate sub-use cases) and PMCH, aligned to Alfonso's report format. Rachel and Kee-Won to prepare; bring open questions as explicit gaps.
- **This week (ASAP) — PMCH follow-up meeting:** Kee-Won to schedule with the same attendees. Agenda should cover: PMCH Phase 1 architecture and inputs/outputs, the current intake form and RPA process at a high level, art of the possible discussion for the intake form, and the question of UiPath vs. alternative tooling.
- **This week — Ortho Labeling follow-up:** Lower urgency; Kee-Won or Joel to message the Ortho group. Agenda: understand label creation and revision workflow in detail, process shadow for label review, Prism 360 role, collect sample label PDFs and source-of-truth documents, Prism upload file examples.
- **May 5 (in calendar) — Data team follow-up check-in:** Kee-Won to revisit whether enough concrete data examples have accumulated to bring to the Stryker data team. Jennifer Kwapis to explore scheduling a session with the data team leader around that week.
- **Next deep dive — Trial new note-taking workflow:** Team to use markdown notes (Obsidian or VS Code) and commit directly to the FDE repo in a date-based folder rather than OneNote.
- **Ongoing — FDE Flywheel document:** Victoria to continue building out the FDE ways of working checklist in OneNote; team to contribute observations. Goal is a reproducible checklist for onboarding any new use case or business unit.
