# Chore Pilot – User Stories (v1)

User stories for the first-stage proof-of-concept. **Objects** are the primary entity; each object can have a warranty and an associated list of **chores** (recurring maintenance, repairs, seasonal work). All chore stories assume the chore is tied to an object.

Format: *As a … I want … So that …*

---

## Objects

**US-1** – As a homeowner, I want to create an object (e.g. Boiler, Gutters, Lawn) with a name and optional description, so that I can group warranties and chores by the thing I am maintaining.

**US-2** – As a homeowner, I want to list all my objects, so that I can see at a glance what I am managing and open any one of them.

**US-3** – As a homeowner, I want to edit an object’s name or description, or remove an object, so that I can keep my list accurate and remove things I no longer track.

---

## Warranty

**US-4** – As a homeowner, I want to add a warranty to an object (provider name, end date, optional notes), so that I know who provided the warranty and when it expires.

**US-5** – As a homeowner, I want to see which objects have a warranty and when each warranty expires, so that I can plan before coverage runs out.

**US-6** – As a homeowner, I want to edit or remove the warranty on an object, so that I can correct details or clear warranty when it is no longer relevant.

---

## Chores – Recurring maintenance

**US-7** – As a homeowner, I want to add a recurring chore to an object (e.g. boiler service every 12 months), so that the system can track when it is next due.

**US-8** – As a homeowner, I want to view the “next due” date for recurring chores on an object (or across objects), so that I know what maintenance is coming up.

**US-9** – As a homeowner, I want to record that a recurring chore was completed and set the next due date, so that my schedule stays up to date.

---

## Chores – Repairs

**US-10** – As a homeowner, I want to log a repair as a chore on an object (what was done, when, cost, materials), so that I have a record of repairs and expenses.

**US-11** – As a homeowner, I want to view repairs done and due per object, so that I can see the repair history and any pending repair work.

---

## Chores – Seasonal

**US-12** – As a homeowner, I want to add a seasonal chore to an object (e.g. clean gutters in autumn, mow lawn in summer), so that I can track seasonal work by object.

**US-13** – As a homeowner, I want to view seasonal chores for the current (or chosen) season, grouped by object, so that I know what seasonal work is relevant now.

---

## Cross-cutting

**US-14** – As a homeowner, I want to see a single list of “what’s due soon” across all objects (maintenance, repairs, seasonal), so that I can prioritise without opening each object.

**US-15** – As a homeowner, I want to mark a chore as complete with a date and optional notes, so that I have a record of when work was done.

**US-16** – As a homeowner, I want to view one object with its warranty (if any) and all its chores, so that I can manage that object in one place.

---

## Authentication and invitations

**US-17** – As a homeowner, I want to invite others by email, so that they can join my household and see the same objects, warranties, and chores.

**US-18** – As an invited person, I want to receive an invitation (e.g. by email) and create my own password to join the household, so that I can access Chore Pilot and contribute without the homeowner having to set up my account.

---

## Reminders

**US-19** – As a homeowner, I want to receive push notifications when a chore is due or due soon, so that I don’t forget to do maintenance or repairs.

---

## Summary

| ID     | Area           | Summary |
|--------|----------------|--------|
| US-1   | Objects        | Create object (name, optional description) |
| US-2   | Objects        | List all objects |
| US-3   | Objects        | Edit or remove object |
| US-4   | Warranty       | Add warranty to object (provider, end date, notes) |
| US-5   | Warranty       | View objects with warranty and expiry |
| US-6   | Warranty       | Edit or remove warranty |
| US-7   | Chores recurring | Add recurring chore to object |
| US-8   | Chores recurring | View next due for recurring chores |
| US-9   | Chores recurring | Record completion and set next due |
| US-10  | Chores repairs | Log repair on object (what, when, cost, materials) |
| US-11  | Chores repairs | View repairs per object |
| US-12  | Chores seasonal | Add seasonal chore to object |
| US-13  | Chores seasonal | View seasonal chores by season, by object |
| US-14  | Cross-cutting  | List “what’s due soon” across objects |
| US-15  | Cross-cutting  | Mark chore complete (date, notes) |
| US-16  | Cross-cutting  | View one object with warranty and all chores |
| US-17  | Auth & invitations | Homeowner invites others by email |
| US-18  | Auth & invitations | Invitee creates password and joins household |
| US-19  | Reminders         | Push notifications when chore is due or due soon |

Acceptance criteria for each story are in [AcceptanceCriteria.md](AcceptanceCriteria.md).
