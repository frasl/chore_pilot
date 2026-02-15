# Chore Pilot – Non-Goals (v1)

This document lists what we are **not** building in the first-stage proof-of-concept. The PRD and UserStories are limited to the scope described there; the following are explicitly out of scope for v1.

- **Multiple properties** – Managing more than one property or household in a single instance. v1 assumes a single household/context.
- **Sharing beyond invited household members** – v1 supports authentication and inviting others by email (invitees create their own password and join the household). Out of scope: public sharing, sharing with people who are not invited to the household, or fine-grained per-user permissions beyond “member of household”.
- **Advanced reporting and analytics** – Charts, spend over time, export to spreadsheet, or similar. v1 is focused on listing and updating objects, warranties, and chores.
- **Document or receipt attachment** – Storing PDFs, images, or receipts against objects or chores. v1 may allow free-text notes only.
- **Offline-first or sync** – Complex offline editing and conflict resolution. v1 can assume a connected client or simple sync; detailed behaviour is not specified here.
- **Public or multi-tenant deployment** – Hosting many unrelated users with isolation. v1 is a proof-of-concept; deployment model is not defined.
- **Data export** – Exporting objects, warranties, and chores (e.g. to file or another system). v1 does not provide export; data portability is not in scope for now.

These may be revisited in later stages; this document reflects the current v1 boundary.
