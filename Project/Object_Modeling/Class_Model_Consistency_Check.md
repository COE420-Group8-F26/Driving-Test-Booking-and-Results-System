# Class Model Consistency / Traceability Check

**Project:** Driving Test Booking and Results System (COE 420 Sec 02, Group 8)

## 1. Traceability to Use Cases

| Use Case | Supporting Classes |
|---|---|
| UC-01 | User, Administrator, Examiner, Session |
| UC-02 | BookingManager, TestSlot |
| UC-03 | BookingManager, Booking, TestSlot, AuditLog, NotificationService |
| UC-04 | BookingManager, Booking, TestSlot, NotificationService |
| UC-05 | Administrator, ScheduleManager, ExaminerAssignment, Availability, Notification |
| UC-06 | User, Applicant |
| UC-07 | ResultManager, TestResult, AuditLog, NotificationService |
| UC-08 | Notification, NotificationService, NotificationType |
| UC-09 | Administrator |
| UC-10 | ResultManager, Certificate, TestResult |
| UC-11 | BookingManager, Booking |
| UC-12 | BookingManager, Booking, TestSlot, AuditLog, NotificationService |
| UC-13 | Booking, TestResult, ResultManager |
| UC-14 | Examiner, ExaminerAssignment |
| UC-15 | User, PasswordResetToken, Administrator, Examiner |
| UC-16 | User, Applicant, AuditLog |
| UC-17 | Examiner, Availability, ExaminerAssignment, ScheduleManager |
| UC-18 | Administrator, ScheduleManager |
| UC-19 | User, Session |
| UC-20 | Administrator, Availability, ScheduleManager |

Every class in the inventory (C01 to C20) maps to at least one use case, and every use case above maps to at least one class. Verify the use case titles against `Requirements/Use_Cases.md` before submission.

## 2. Traceability to Requirements

| Requirement | Where it appears in the class model |
|---|---|
| FR15 (record status) | Applicant.recordStatus, RecordStatus enum, note on Applicant |
| FR23 (profile edits) | Applicant.updateProfile(address, phone) |
| FR25 (logout) | User.logout(), Session.invalidate(), note on Session |
| NFR16 (lockout) | User.failedLoginCount, isLocked, lockedUntil, note on User |
| NFR17 (audit) | AuditLog, ActionType, append-only note |
| 30-minute booking cutoff | BookingManager.validateCutoff, note on BookingManager |

## 3. Consistency with DFD / Data Stores

| Data Store / Process | Class(es) |
|---|---|
| D5 Results | TestResult (and Certificate) |
| Process 4.0 (examiner scheduling) | ScheduleManager, Availability, ExaminerAssignment |
| Process 5.0 (results) | ResultManager, TestResult, Certificate |

TODO (team): add rows for D1 to D4 and the remaining processes by checking `Data_Flow_Modeling/Core_Processes_Matrix.md` and the Level 0 DFD.

## 4. Relationships and Multiplicities

| Association | Name | Multiplicity | Justification |
|---|---|---|---|
| Applicant to Booking | makes | 1 to 0..* | An applicant may hold several bookings over time. |
| Booking to TestSlot | reserves | 0..* to 1 | Slots are reusable after cancellation. |
| Booking to ExaminerAssignment | is covered by | 1 to 0..* | Revoked assignments are kept as history. |
| Examiner to ExaminerAssignment | is assigned to | 1 to 0..* | One examiner covers many bookings. |
| Administrator to ExaminerAssignment | makes | 1 to 0..* | Records who assigned. |
| Examiner to Availability | submits | 1 to 0..* | An examiner declares many time blocks. |
| Booking to TestResult | is evaluated by | 1 to 0..1 | At most one result per booking. |
| Examiner to TestResult | submits | 1 to 0..* | An examiner submits many results. |
| TestResult to Certificate | earns | 1 to 0..1 | Only PASS results earn one certificate. |
| User to Session | has | 1 to 0..* | A user may have several logins. |
| User to PasswordResetToken | requests | 1 to 0..* | Several reset requests possible. |
| User to Notification | receives | 1 to 0..* | Many notices per user. |
| User to AuditLog | performs | 1 to 0..* | Every action traces to a user. |
| Applicant, Examiner, Administrator to User | inheritance | n/a | The only genuine generalization. |

## 5. Verification Checklist

- [x] No duplicate classes remain (see Integration_Notes.md, Section 1).
- [x] Each enumeration is defined once.
- [x] Foreign key attributes removed; relationships carried by named associations.
- [x] Every association has a name and multiplicities.
- [x] Inheritance used only for User.
- [ ] Use case titles and DFD data stores D1 to D4 confirmed against earlier labs (team to complete).
