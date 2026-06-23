# ShiftSwap Requirements (Structured from Unstructured Inputs)

## User Stories & Acceptance Criteria

### 1) Post Open Shift
**User Story:** As an hourly employee, I want to post a shift I cannot work, so that qualified coworkers can cover it.

**Acceptance Criteria**
- Employee can create an open shift request with required details (date, time, location/team, role).
- Open shifts are visible in a shared list for eligible coworkers.
- The posted shift has a clear status (Open, Claimed, Approved, Denied, Expired).
- Posting action is timestamped and tied to the employee in the audit trail.

### 2) Claim Open Shift
**User Story:** As an hourly employee, I want to claim an open shift, so that I can pick up additional work.

**Acceptance Criteria**
- Eligible employees can claim only open shifts.
- A shift cannot be claimed by more than one employee at the same time.
- The claim action records claimant identity and timestamp.
- Claimed shifts move to Pending Approval status.

### 3) Cancel Claim Before Approval
**User Story:** As a coworker who claimed a shift, I want to cancel my claim before manager approval, so that I am not locked into a shift if plans change.

**Acceptance Criteria**
- Claimer can cancel only while status is Pending Approval.
- After manager approval, claim cancellation is blocked in-app.
- Cancellation returns the shift to Open status.
- Cancellation event is logged with timestamp and actor.

### 4) Manager Approval Gate
**User Story:** As an operations manager, I want to approve or deny claimed swaps, so that no shift change is finalized without oversight.

**Acceptance Criteria**
- Every claimed shift requires explicit manager approval or denial.
- No swap is marked final until approved.
- Manager decision includes timestamp and decision maker in the audit trail.
- Manager can view and act on pending approvals from a centralized queue.

### 5) Notifications for Time-Sensitive Events
**User Story:** As an employee or manager, I want timely notifications for shift-swap events, so that actions happen before shifts are impacted.

**Acceptance Criteria**
- System notifies relevant users when a shift is posted, claimed, and approved/denied.
- SMS is supported for MVP notifications.
- If a shift remains unclaimed, manager receives an escalation alert by default 4 hours before shift start.
- Notification delivery attempts are logged for operational follow-up.

### 6) Mobile-Friendly, Lightweight Access
**User Story:** As a frontline employee, I want a mobile-friendly experience and simple login, so that I can use ShiftSwap without a laptop or complex authentication.

**Acceptance Criteria**
- Core workflows (post, browse, claim, status check) are usable on mobile web.
- MVP login supports employee ID-based authentication.
- SSO is not required for MVP use.
- Access assumptions account for users with basic phones by relying on SMS notifications for key events.

### 7) Audit Trail & 90-Day Export
**User Story:** As an HR director, I want a complete, exportable audit trail of shift swaps, so that we can satisfy compliance and payroll audit needs.

**Acceptance Criteria**
- Audit trail captures who posted, claimed, approved/denied, and when.
- Audit data is queryable for at least the trailing 90 days.
- Managers/HR can export swap history as CSV.
- Export includes required timestamps and actor fields for audits.

### 8) Overtime Risk Flagging
**User Story:** As a manager, I want overtime risk flags when a swap may push someone over 40 hours/week, so that I can review and decide appropriately.

**Acceptance Criteria**
- System calculates or checks projected weekly hours for claimant at review time.
- If projected hours exceed 40/week, the swap is flagged for manager review.
- Overtime flag is informational in MVP (does not auto-block approval).
- Overtime review context is retained in swap records.

### 9) Manager Visibility of Swap Activity
**User Story:** As a manager, I want to see current and recent swap activity in one place, so that I can manage coverage and intervene when needed.

**Acceptance Criteria**
- Manager dashboard shows open, pending, approved, denied, and unclaimed-at-risk items.
- Manager can filter/sort to find urgent items quickly.
- History view supports at least 90-day operational lookback.
- Dashboard data aligns with audit-log source records.

## Conflicts & Open Questions
- **Notification channel priority changed during discovery.** Early input suggested push/email/text were all possible; later discussion prioritized SMS for MVP because many frontline staff lack smartphones/data plans.  
  **Sources:** Email #1 (Maria), Slack 9:30 AM, Requirements Session.
- **Timeline inconsistency.** Working context says one 2-week Sprint 1 MVP, while kickoff transcript mentions "about two sprints."  
  **Sources:** Kickoff transcript vs. project framing.
- **Manager can swap on behalf of employee is unresolved.** Mentioned in sticky notes but not confirmed in requirements session outcomes.  
  **Source:** Sticky notes.
- **Users with flip phones/basic phones may not reliably use web app.** Inputs require mobile web and also note non-smartphone users; exact fallback UX (SMS reply flows vs. notify-only SMS) is not specified.  
  **Sources:** Sticky notes, Email #1, Slack 9:24-9:26 AM.
- **Unclaimed-shift escalation timing is partly defined.** "4 hours before shift starts" was proposed and accepted in-session, but configurability and owner for changing threshold were not defined.  
  **Source:** Requirements Session.

## Deferred / Out of Scope
- **Slack integration for shift notifications/posts** — explicitly deprioritized to later phase.  
  **Sources:** Sticky notes ("later??"), Slack 9:31 AM, Requirements Session closing.
- **Direct payroll/timekeeping integration** — explicitly excluded from first release due to risk.  
  **Sources:** Email #2 item 4, Slack 9:14 AM and 9:32 AM, Kickoff transcript.
- **Advanced overtime automation/blocking** — only flagging is required in MVP; deeper automation deferred.  
  **Sources:** Email #1 ("phase 2"), Slack 9:18-9:19 AM.
- **Enterprise SSO/advanced identity features** — explicitly not needed for MVP (employee ID login preferred).  
  **Sources:** Sticky notes, Slack 9:33 AM, Requirements Session.
