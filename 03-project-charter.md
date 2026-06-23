# Project Charter — ShiftSwap MVP

## Project Purpose
ShiftSwap will replace ad hoc shift-coverage coordination (texts and calls) with a simple web app where hourly employees can post shifts they cannot work, coworkers can claim those shifts, and managers approve or deny swaps before they are final.

## Scope Definition
Detailed scope is maintained in `scope.md`:
- In-scope Sprint 1 MVP items
- Out-of-scope/deferred items

## Objectives
1. Deliver a usable MVP in a single 2-week Sprint 1.
2. Enable the full core flow: post shift -> claim shift -> manager decision.
3. Improve shift coverage speed and visibility for operations.
4. Provide HR with an auditable swap history for compliance review.
5. Validate readiness for pilot rollout at Sprint Review.

## Stakeholders & Roles
| Stakeholder | Role | Primary Responsibility |
|---|---|---|
| Operations Manager | Business Owner | Defines operational priorities, approves workflow fit |
| HR Director | Compliance Owner | Defines audit and policy requirements |
| Dev Lead | Technical Lead | Delivers MVP scope within sprint constraints |
| Frontline Employees | End Users | Use the system and provide usability feedback |

## Success Criteria
- Employees can post and claim open shifts without manager intervention in the posting/claiming steps.
- No swap is finalized until a manager approves it.
- Managers can quickly identify pending swaps and act on them.
- Required swap events are logged with timestamps for auditability.
- Stakeholders accept Sprint 1 MVP during Sprint Review for pilot use.

## High-Level Timeline
- **Days 1-2:** Finalize MVP scope, user stories, and acceptance criteria.
- **Days 3-9:** Build and integrate core workflow, approvals, notifications, and audit logging.
- **Days 10-12:** Conduct QA/UAT and resolve priority defects.
- **Days 13-14:** Sprint Review, stakeholder sign-off, and pilot go/no-go decision.

## Assumptions & Constraints
- Project is constrained to one 2-week sprint for MVP delivery.
- Team capacity is fixed; only must-have functionality is included in Sprint 1.
- Solution must support frontline usage with mobile-friendly web access.
- Manager approval and audit trail are mandatory for release.
- Additional integrations and advanced features are deferred to later phases.
