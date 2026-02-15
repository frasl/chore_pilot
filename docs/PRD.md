# Chore Pilot – Product Requirements Document

## Product name

**Chore Pilot**

(This name is used consistently across all product documentation.)

---

## Product overview

Chore Pilot is a house repair and maintenance management product. It helps users track recurring maintenance (e.g. boiler servicing), repairs (expenses, materials, warranty), and seasonal work (e.g. cleaning gutters, cutting grass). The product consists of a server and a mobile app. This document describes the first stage: a lean, simple proof-of-concept that handles a small set of key use cases.

---

## Target users

- **Homeowners** who want to stay on top of home maintenance and repairs.
- **Property managers** who need to track maintenance and warranties across one or more properties (v1 may focus on a single household; see Assumptions).

---

## Problem statement

Users today struggle with:

- **Forgotten servicing** – Recurring maintenance (e.g. annual boiler service) is easy to miss when there is no central place to track “next due”.
- **Lost warranty and expense info** – Repair dates, costs, materials, and warranty end dates are stored in emails, receipts, or memory and are hard to find when needed.
- **Seasonal tasks slipping** – Work that depends on season (gutters, lawn, HVAC checks) is not clearly tied to a schedule or to the thing being maintained.

---

## Solution summary

Chore Pilot provides a central place to:

- **Manage objects** – Things in or around the house (boiler, roof, gutters, lawn, etc.) that the user cares about.
- **Attach warranty to objects** – Record who provides the warranty and when it ends, so the user can see what is covered and when it expires.
- **Associate chores with objects** – Every chore (recurring maintenance, repair, or seasonal task) belongs to an object, so the user sees what needs to be done per object and overall.

Users can track recurring maintenance (schedule and next due), repairs (what was done, cost, materials, and object-level warranty), and seasonal work (e.g. by season), and see “what’s due soon” across all objects.

---

## Domain model – Managed objects

- **Objects** – Things the user manages in or around the house (e.g. boiler, HVAC, roof, gutters, lawn). Each object has a name and optionally a description. Objects are the primary entity; chores and warranty are tied to them.
- **Warranty** – An object can have at most one warranty. The warranty is provided by someone (installer, manufacturer, etc.) and has at least an end date; optionally provider name and notes. The user can see which objects have warranty and when it expires.
- **Chores** – Each object has an associated list of chores. A chore is one of:
  - **Recurring maintenance** – e.g. annual boiler service; has a schedule and “next due” date.
  - **Repair** – one-off or occasional; can record what was done, when, cost, and materials.
  - **Seasonal** – e.g. clean gutters, mow lawn; tied to a season or frequency.

Chores are always linked to an object; there are no “floating” chores.

---

## Key capabilities (v1 proof-of-concept)

1. **Objects and warranty**
   - Create, list, edit, and remove objects (name, optional description).
   - Add warranty to an object (provider name, end date, optional notes).
   - View which objects have warranty and when it expires.
   - Edit or remove warranty from an object.

2. **Recurring maintenance**
   - Add a recurring chore to an object with recurrence defined like appointment creation in email/calendar apps (e.g. daily, weekly, monthly, yearly, or every N days/weeks/months; optional end date). The system computes “next due” from the recurrence rule.
   - View “next due” for recurring chores (per object and in a combined view).
   - Record completion and set the next due date (or the system advances it from the recurrence rule).

3. **Repairs**
   - Log a repair as a chore on an object (what was done, when, cost, materials). v1 focuses on recording work done; planned/scheduled repairs (e.g. “repair due next week”) are planned for v2 (see [PlannedForNextVersions.md](PlannedForNextVersions.md)).
   - View repairs (and optionally “needs doing”) per object.
   - Warranty is tracked at object level (see above); repair-level warranty notes can be included in the repair chore if needed.

4. **Seasonal work**
   - Add a seasonal chore to an object (e.g. clean gutters in autumn, mow lawn in summer).
   - View seasonal chores for the current (or chosen) season, grouped by object.

5. **Cross-cutting**
   - List “what’s due soon” across all objects (maintenance, repairs, seasonal). “Due soon” is configurable per chore (e.g. show 7 or 30 days before due); the aggregated list respects each chore’s setting.
   - Mark a chore complete (with date and optional notes).
   - View a single object with its warranty (if any) and all its chores.
   - **Push notifications** – The user can receive push notifications when a chore is due or due soon, so they are reminded without having to open the app.

6. **Authentication and invitations**
   - Users authenticate (e.g. login with email and password).
   - The homeowner can invite others by email. Invitees receive an invitation (e.g. by email) and can create their own password to join the household. Once joined, they see the same objects, warranties, and chores as the rest of the household.

---

## Out of scope for v1

Explicit non-goals are listed in [NonGoals.md](NonGoals.md). They include, for example: multiple properties, sharing beyond invited household members, advanced reporting, and data export. The PRD and UserStories do not define behaviour for those areas in v1.

---

## Success criteria for proof-of-concept

The first stage is successful when:

- A user can create objects and attach warranty (provider, end date).
- A user can add recurring, repair, and seasonal chores to objects.
- A user can record chore completion and see “next due” (or equivalent) for recurring and seasonal work.
- A user can see “what’s due soon” across objects (with per-chore “due soon” configuration) and view a single object with its warranty and chores.
- A homeowner can invite others by email, and invitees can create a password and join the household.

No specific technology or stack is mandated; the above is described in terms of user-visible behaviour.

---

## Architecture (conceptual only)

- **Server** – Backend logic and data storage. Responsible for persisting objects, warranties, and chores, and for any business rules (e.g. computing “next due”).
- **Mobile app** – User-facing client used to manage objects, warranties, and chores. Communicates with the server.

Technology choices (languages, frameworks, protocols, deployment) are out of scope for this document and will be decided later.
