# Chore Pilot – Assumptions & Open Questions (v1)

This document records assumptions made for the v1 specification and open questions that may affect design or implementation. No technology choices are made here; the focus is on product and scope.

---

## Assumptions

- **Single household** – v1 is designed for one household or one “context”. Multi-property or multi-household support is out of scope (see [NonGoals.md](NonGoals.md)).
- **One warranty per object** – Each managed object has at most one warranty. If a user needs to track multiple warranties (e.g. parts vs labour), that is not in v1; we assume one warranty record per object is enough for the proof-of-concept.
- **Chores belong to one object (v1)** – In v1, every chore is associated with exactly one object. There are no “global” or unassigned chores, and no chore is linked to multiple objects. Chores that might apply to multiple areas (e.g. “general garden”) are modelled by creating an object like “Garden” and attaching chores to it. Multi-object chores are planned for a future version (see [PlannedForNextVersions.md](PlannedForNextVersions.md)).
- **Authentication is required** – Users must be able to identify themselves (e.g. login). A core use case is: the **homeowner invites others by email**; **invitees receive an invitation and can create their own password** to join the household and access the same objects, warranties, and chores. This is in scope for v1 (see [PRD](PRD.md) and [UserStories](UserStories.md)).
- **“Due soon” is configurable per chore** – The window for “what’s due soon” is not global. Each chore can have its own setting (e.g. “show as due soon 7 days before” or “30 days before”), so the aggregated “what’s due soon” list respects per-chore configuration.
- **Recurrence is like appointment creation in email/calendar apps** – Repeating chores are planned similarly to recurring appointments in email or calendar applications: the user can define frequency (e.g. daily, weekly, monthly, yearly, or every N days/weeks/months), optional end date, and the system computes “next due” from that. The exact UI and options (e.g. “on day X of month”) follow familiar calendar-appointment patterns.
- **Seasonal chore semantics** – Seasonal chores are tied to a season (e.g. autumn, summer). Whether a “seasonal” chore repeats every year or is one-off, and how “current season” is determined (user location, manual choice, or fixed calendar), is implementation-defined; the spec requires that the user can add seasonal chores and view them for a chosen/current season.
- **v1 includes push notifications for reminders** – v1 includes push notifications to remind the user when a chore is due (or due soon). Other reminder channels (e.g. email, in-app) are implementation-defined; push is in scope (see [PRD](PRD.md), [UserStories](UserStories.md) US-19).
- **Currency and units** – For repair cost, v1 uses free text or a single currency per context; multi-currency is out of scope.

---

## Open questions

(Currently none. When new open questions arise, add them here and reflect resolutions in the PRD, UserStories, or AcceptanceCriteria as appropriate.)
