# Chore Pilot – Acceptance Criteria (v1)

One section per user story from [UserStories.md](UserStories.md). Criteria are testable conditions that must hold for the story to be done. Format: Given/When/Then or “User can …” / “System shall …”.

---

## US-1 – Create object (name, optional description)

- **AC-1.1** – User can create a new object by providing a name. The system stores the object and associates it with the user’s context (e.g. household).
- **AC-1.2** – User can optionally provide a description when creating an object. The system stores the description with the object.
- **AC-1.3** – The system shall require a non-empty name. If the name is empty, the system shall not create the object and shall indicate that the name is required.
- **AC-1.4** – After successful creation, the user can see the new object in the list of objects (see US-2).

---

## US-2 – List all objects

- **AC-2.1** – User can request a list of all objects. The system returns all objects the user manages, each with at least name and optional description.
- **AC-2.2** – The list is ordered in a consistent way (e.g. by name or creation order); the exact order is defined by the implementation.
- **AC-2.3** – User can open an object from this list to view its details (warranty and chores) as in US-16.

---

## US-3 – Edit or remove object

- **AC-3.1** – User can edit an existing object’s name. The system updates the object and the new name is shown in the list and on the object’s detail view.
- **AC-3.2** – User can edit an existing object’s description (including clearing it). The system updates the object accordingly.
- **AC-3.3** – User can remove (delete) an object. The system removes the object and its warranty and chore data from the user’s context. The object no longer appears in the list.
- **AC-3.4** – The system shall require a non-empty name when saving an edit. Removal is irreversible within the scope of v1 (no “undo” required).

---

## US-4 – Add warranty to object (provider, end date, notes)

- **AC-4.1** – User can add a warranty to an object by providing at least an end date. The system stores the warranty and associates it with that object.
- **AC-4.2** – User can optionally provide a provider name (e.g. installer or manufacturer) and notes. The system stores these with the warranty.
- **AC-4.3** – An object has at most one warranty. If the user adds a warranty when one already exists, the system replaces it (or the flow is “edit warranty”; behaviour is equivalent to one warranty per object).
- **AC-4.4** – After adding, the user can see the warranty on the object’s detail view (US-16) and in any “warranty expiry” view (US-5).

---

## US-5 – View objects with warranty and expiry

- **AC-5.1** – User can request a view of objects that have a warranty. The system lists those objects and shows each warranty’s end date (and optionally provider).
- **AC-5.2** – The list is ordered in a consistent way (e.g. by expiry date or object name). User can see at a glance which warranties expire soonest.
- **AC-5.3** – Objects without a warranty do not appear in this view (or are clearly separated); the main object list (US-2) still shows all objects.

---

## US-6 – Edit or remove warranty

- **AC-6.1** – User can edit the warranty on an object: change provider name, end date, or notes. The system updates the warranty; the new data is shown in object detail and warranty views.
- **AC-6.2** – User can remove the warranty from an object. The object then has no warranty until the user adds one again. The object still appears in the object list; it no longer appears in the “objects with warranty” view (US-5) until a new warranty is added.

---

## US-7 – Add recurring chore to object

- **AC-7.1** – User can add a recurring chore to an object. The user provides at least a description and a recurrence rule similar to appointment creation in email/calendar apps (e.g. daily, weekly, monthly, yearly, or every N days/weeks/months; optional end date). The system computes “next due” from the rule.
- **AC-7.2** – The system stores the chore as associated with that object and treats it as recurring (has a next-due date that can be updated when completed or advanced from the rule, see US-9).
- **AC-7.3** – The new chore appears on the object’s detail view (US-16) and in “next due” views (US-8, US-14).

---

## US-8 – View next due for recurring chores

- **AC-8.1** – User can view recurring chores with their “next due” date, either for a single object or across all objects. The system shows each recurring chore and its next due date.
- **AC-8.2** – The list is ordered in a consistent way (e.g. by next due date). User can see what maintenance is coming up soonest.
- **AC-8.3** – Chores that are past due are still shown (e.g. included in “next due” or “overdue”); behaviour is consistent and visible to the user.

---

## US-9 – Record completion and set next due (recurring)

- **AC-9.1** – User can mark a recurring chore as completed on a given date. The system records the completion (date and optional notes, per US-15).
- **AC-9.2** – User can set the next due date for that recurring chore (e.g. 12 months from completion, or a chosen date). The system updates the chore’s next-due date accordingly.
- **AC-9.3** – After completion, the chore remains on the object and appears in “next due” views with the new date; it no longer appears as “due” for the old date.

---

## US-10 – Log repair on object (what, when, cost, materials)

- **AC-10.1** – User can add a repair chore to an object. The user provides at least a description of what was done (or what is due) and when (date).
- **AC-10.2** – User can optionally provide cost and materials. The system stores these with the repair chore.
- **AC-10.3** – The repair is stored as a chore associated with that object. It appears on the object’s detail view (US-16) and in repair views (US-11).

---

## US-11 – View repairs per object

- **AC-11.1** – User can view repairs (done or due) for a single object. The system lists repair chores for that object with at least description and date; cost and materials are shown if present.
- **AC-11.2** – User can view repairs across objects (e.g. all repairs in a time range or “pending repairs”). The list is grouped or filterable by object so the user can see which object each repair belongs to.
- **AC-11.3** – Repairs are distinguishable from recurring and seasonal chores (e.g. by type or label) so the user can tell what kind of chore it is.

---

## US-12 – Add seasonal chore to object

- **AC-12.1** – User can add a seasonal chore to an object. The user provides at least a description (e.g. “Clean gutters”) and the season or frequency (e.g. autumn, or “quarterly”).
- **AC-12.2** – The system stores the chore as associated with that object and marks it as seasonal. The chore can be shown in seasonal views (US-13) and in “what’s due soon” (US-14) when the season is relevant.
- **AC-12.3** – The new chore appears on the object’s detail view (US-16).

---

## US-13 – View seasonal chores by season, by object

- **AC-13.1** – User can view seasonal chores for a chosen season (e.g. current season or a specific one). The system lists seasonal chores that apply to that season.
- **AC-13.2** – The list is grouped by object (or shows object name with each chore) so the user can see which object each seasonal chore belongs to.
- **AC-13.3** – User can see at a glance what seasonal work is relevant for the selected period.

---

## US-14 – List “what’s due soon” across objects

- **AC-14.1** – User can request a single list of “what’s due soon” that combines recurring chores (by next due date), repairs that are due (if applicable), and seasonal chores for the current (or relevant) period.
- **AC-14.2** – Each item in the list is identifiable as to type (recurring, repair, seasonal) and to object, so the user can prioritise and navigate to the right object or chore.
- **AC-14.3** – “Due soon” is configurable per chore (e.g. “show 7 days before” or “30 days before”). The aggregated list respects each chore’s setting. The list is ordered in a consistent way (e.g. by date or priority).

---

## US-15 – Mark chore complete (date, notes)

- **AC-15.1** – User can mark any chore (recurring, repair, or seasonal) as complete. The user provides at least the completion date; the system stores it.
- **AC-15.2** – User can optionally add notes when marking complete. The system stores the notes with the completion.
- **AC-15.3** – For recurring chores, the user can then set the next due date (US-9). For one-off repairs or seasonal chores, “complete” means the chore is done; it may still appear in history or past-chore views but not as “due” in “what’s due soon” (unless the implementation supports “repeat” seasonal chores).
- **AC-15.4** – Completed chores are distinguishable from incomplete ones (e.g. in object detail view and in lists).

---

## US-16 – View one object with warranty and all chores

- **AC-16.1** – User can open a single object and see its details: name, optional description, warranty (if any) with provider, end date, and notes, and the full list of chores for that object.
- **AC-16.2** – Chores are shown with enough information to identify type (recurring, repair, seasonal) and key dates (e.g. next due, completion date). User can act on them (e.g. mark complete, edit) as allowed by other stories.
- **AC-16.3** – If the object has no warranty, the warranty section is empty or clearly “none”. If the object has no chores, the chore list is empty or clearly “no chores”.

---

## US-17 – Homeowner invites others by email

- **AC-17.1** – A user who is a homeowner (or household owner) can invite another person by entering that person’s email address. The system sends an invitation (e.g. by email) to that address.
- **AC-17.2** – The invitation contains enough information for the invitee to accept and join the household (e.g. a link or code). The invitee is not yet able to access the household’s data until they complete the join flow (US-18).
- **AC-17.3** – The homeowner can see pending invitations (e.g. email and status) and, if the implementation supports it, cancel or resend them. Duplicate invites for the same email can be handled by implementation (e.g. idempotent send or “already invited” message).
- **AC-17.4** – After the invitee joins (US-18), they see the same objects, warranties, and chores as the rest of the household.

---

## US-18 – Invitee creates password and joins household

- **AC-18.1** – An invited person receives the invitation (e.g. by email) and can open a flow to join the household. The flow prompts them to create their own password (and any required identity fields, e.g. display name).
- **AC-18.2** – The system shall require a password that meets implementation-defined security rules. The invitee sets the password; the homeowner does not set it for them.
- **AC-18.3** – After the invitee successfully completes the flow, they are a member of the household and can log in with their email and password. They then have access to the same household data (objects, warranties, chores) as other members.
- **AC-18.4** – Invitations can expire or be invalidated (e.g. after use or after a time limit); behaviour is implementation-defined but must be clear to the user (e.g. “link expired”).

---

## US-19 – Push notifications when chore is due or due soon

- **AC-19.1** – The user can receive push notifications on their device when a chore is due or due soon. “Due soon” respects the per-chore “due soon” configuration (see US-14).
- **AC-19.2** – The user can enable or disable push notifications (globally or per chore/category); the implementation may offer defaults (e.g. enabled for “due soon”).
- **AC-19.3** – A notification identifies the chore and the object (and optionally the due date) so the user can act on it. Tapping the notification can open the app to the relevant chore or object (implementation-defined).
- **AC-19.4** – Notifications are sent by the server (or a backend) based on chore due dates and the user’s device registration; the mobile app can receive and display them when permitted by the user and OS.

---

## Summary

| Story | Acceptance criteria count |
|-------|---------------------------|
| US-1  | 4 |
| US-2  | 3 |
| US-3  | 4 |
| US-4  | 4 |
| US-5  | 3 |
| US-6  | 2 |
| US-7  | 3 |
| US-8  | 3 |
| US-9  | 3 |
| US-10 | 3 |
| US-11 | 3 |
| US-12 | 3 |
| US-13 | 3 |
| US-14 | 3 |
| US-15 | 4 |
| US-16 | 3 |
| US-17 | 4 |
| US-18 | 4 |
| US-19 | 4 |

All criteria are testable and technology-agnostic; they describe user-visible or system behaviour required for the v1 proof-of-concept.
