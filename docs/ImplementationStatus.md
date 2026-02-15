# Chore Pilot – Implementation Status

This document tracks the implementation status of Chore Pilot. It is updated when the PRD or UserStories change, and when code or delivered features change (per [documentation rules](.cursor/rules/documentation.mdc)).

---

## Specification (v1 proof-of-concept)

| Document | Status | Notes |
|----------|--------|--------|
| [PRD.md](PRD.md) | Done | Chore Pilot; objects, warranty, chores; recurrence (appointment-style); per-chore “due soon”; auth and invite; push notifications (v1); repairs as “work done” (planned repairs v2); server + mobile app; conceptual only. |
| [UserStories.md](UserStories.md) | Done | 19 user stories (US-1–US-19): objects, warranty, recurring/repair/seasonal chores, cross-cutting, auth and invitations (US-17, US-18), push notifications (US-19). |
| [AcceptanceCriteria.md](AcceptanceCriteria.md) | Done | Acceptance criteria for each user story (including US-17, US-18, US-19). |
| [NonGoals.md](NonGoals.md) | Done | v1 non-goals defined (includes data export; reminders/notifications removed – v1 has push). |
| [AssumptionsAndOpenQuestions.md](AssumptionsAndOpenQuestions.md) | Done | Assumptions and resolved items; open questions cleared (reminders→v1 push; currency; export→NonGoals; planned repairs→v2). |
| [PlannedForNextVersions.md](PlannedForNextVersions.md) | Done | Multi-object chores, undo/soft delete, planned/scheduled repairs (v2). |

---

## Implementation

| Area | Status | Notes |
|------|--------|--------|
| Server | Not started | No backend implementation. |
| Mobile app | Not started | No client implementation. |
| API | Not started | No API defined yet; [API.md](API.md) to be created when endpoints are designed. |

**Current phase:** Specification complete for v1 proof-of-concept. No technology choices or code yet. Next step: decide stack and begin implementation; when API or code is added, this document and API.md (if applicable) will be updated.
