# TODO (internal use — Claude Code)

This file is maintained by Claude Code across sessions; it is not a user-facing artifact. Maintenance rules:
- Whenever a task is completed in this conversation/session, check it off here (`- [x]`) before finishing.
- Whenever a new task comes up (requested by the user or discovered during work), add it to the matching section.
- Covers the project's full lifecycle, from requirements gathering to deployment — not just implementation.
- RF/RN references point to `REQUIREMENTS.md`; database conventions are in `docs/database-schema.md`.

## 0. Requirements and documentation
- [x] Create GitHub repository (private) and configure remote
- [x] Add `.gitignore` (Node/JavaScript)
- [x] Add `README.md`
- [x] Add `LICENSE` (MIT)
- [x] Rename `requisitos.md` to `REQUIREMENTS.md`
- [x] Remove co-author trailer from commit history
- [x] Add future expansion (Vestuário, TI) to context
- [x] Add item condition (new/under_maintenance/damaged) and repair flow
- [x] Fix late-return/low-stock notifications for supervision (weekly report instead of instant notification)
- [x] Add profile editing and weekly report configuration (RF06)
- [x] Fill in Data Model (draft) with conceptual ER diagram (Section 7)
- [x] Create `docs/database-schema.md` (detailed technical schema, snake_case conventions)
- [x] Replace "References and Attachments" with Cronograma (Section 11)
- [x] Remove time estimates from the cronograma, keep only ordering
- [x] Add UI/UX Design step to the cronograma
- [x] Merge Order/Phase columns in the MVP Test Milestone row
- [x] Create `CLAUDE.md`
- [x] Create `TODO.md` and point `CLAUDE.md` to it
- [x] Translate `TODO.md` to English; establish English-only documentation/naming policy (app UI stays in Portuguese)
- [ ] Decide whether to translate `REQUIREMENTS.md`, `README.md`, and `docs/database-schema.md` to English (pending user decision)
- [ ] Define and fill in a new "References and Attachments" section (if needed)

## 1. Setup
- [ ] Configure CI/CD
- [ ] Configure development environment (Ubuntu 24.04 LTS local)
- [ ] Create initial database schema (see `docs/database-schema.md`)
- [ ] Scaffold backend (Node.js)
- [ ] Scaffold frontend (React)
- [ ] Implement authentication with password hashing
- [ ] Configure HTTPS

## 2. UI/UX Design
- [ ] Wireframes for the main screens: login, item registration, search, checkout/return
- [ ] Clickable prototype
- [ ] Present and validate the prototype with stakeholders (SENAI coordination/supervisors)

## 3. MVP
- [ ] RF06 — user registration
- [ ] RF01 — item registration
- [ ] RF04 — item search
- [ ] RF02 simplified — checkout/return without business-rule validation (only current user + last returner tracked)
- [ ] Responsive interface (mobile/tablet/desktop)

## Milestone: MVP Test
- [ ] Acceptance test with a reduced pilot (one class/workshop)
- [ ] Validate responsiveness on all three device types
- [ ] Collect feedback and apply fixes before moving on

## 4. Business rules
- [ ] RN1/RN2 — return deadlines by shift/profile
- [ ] RF02 complete — movement states (pending/approved/denied/available/overdue)
- [ ] RN6 — approval by teacher/supervisor depending on workshop/axis
- [ ] Damaged item/repair flow (RF02)
- [ ] RF03 — low-stock alerts
- [ ] RN3 — late-return notifications
- [ ] RF07 — purchase request

## 5. Reports and configuration
- [ ] RF05 — reports (history, most/least used items, inventory, movement by user)
- [ ] RF05 — export to PDF/Excel
- [ ] RF05 — weekly report
- [ ] RF06 — profile editing (all users)
- [ ] RF06 — weekly report configuration by supervisor (day/time, toggles)

## 6. Non-functional and hardening
- [ ] Audit log
- [ ] Automated daily backup
- [ ] Backup restoration test
- [ ] Protection against SQL injection, XSS, and CSRF
- [ ] Load test (30–50 concurrent users)

## 7. Staging and pilot launch
- [ ] Deploy to staging environment
- [ ] Final acceptance test (UAT) with teachers and supervisors
- [ ] User training
- [ ] Deploy to production (VPS)
- [ ] Post-launch monitoring (hypercare)
