# Class Inventory

**Project:** Driving Test Booking and Results System
**Course:** COE 420 Sec 02, Fall 2026, Group 8
**Instructor:** Yara Kaddoura

## Team Members and Contributions

| Name | ID | Model Component | Classes |
|---|---|---|---|
| Zainab Kashif | @00101246 | Users and Security | C01 to C07 |
| Farah Tawalbeh | @00099768 | Reservation and Booking | C08 to C10 |
| Areej Syed | @00098262 | Examiner Scheduling, Admin Oversight, Notifications | C11 to C17 |
| Aira Khawwar | @00101622 | Results and Certificates | C18 to C20 (also shares C15, C17) |

## Approved Classes

| Class ID | Class Name | Purpose / Responsibility | Related Use Case(s) | Contributor |
|---|---|---|---|---|
| C01 | User (abstract) | Generalization of all system users. Holds shared account data (name, email, hashed password, role, failed-login count, lock status). Handles registration validation, authentication, the 15-minute lockout after 5 failed logins (NFR16), and password changes. | UC-01, UC-06, UC-15, UC-16, UC-19 | Zainab |
| C02 | Applicant | A person applying for a driving test. Extends User with unique ID number, address, phone, and overall record status ("Licensed" / "Retest Required", FR15). Allows editing of profile fields (FR23). | UC-06, UC-16 | Zainab |
| C03 | Administrator | A user who manages bookings and examiner assignments. Extends User with staff ID and department. Views and filters all bookings. | UC-01, UC-15, UC-05, UC-09, UC-18, UC-20 | Zainab, Areej |
| C04 | Examiner | A user who conducts tests. Extends User with examiner number and license categories. Linked to availability, assignments and results. | UC-01, UC-14, UC-15, UC-17 | Zainab, Areej |
| C05 | PasswordResetToken | Single-use, time-limited token emailed to a user for password reset. Tracks expiry and whether it has been used. | UC-15 | Zainab |
| C06 | Session | Represents an authenticated login. Holds the session token, creation and expiry times, and active status. Invalidated on logout (FR25). | UC-01, UC-19 | Zainab |
| C07 | AuditLog | Permanent, read-only record of important actions (user, action type, affected record, timestamp). Supports NFR17. Entries can be created but never edited or deleted. | UC-16, UC-03, UC-12, UC-07 | Zainab |
| C08 | TestSlot | An available driving test appointment (date, start and end time, location, availability). Ensures a slot can only be reserved once and can be released after cancellation or rescheduling. | UC-02, UC-03, UC-04, UC-12 | Farah |
| C09 | Booking | A driving test reservation made by an applicant. Stores booking reference, status, creation and cancellation dates, test type, and associated slot. Tracks the lifecycle: confirmation, cancellation, rescheduling, completion. | UC-03, UC-04, UC-11, UC-12, UC-13 | Farah |
| C10 | BookingManager | Controller for booking operations: searching slots, validating the 30-minute cutoff, checking conflicting reservations, creating, cancelling and rescheduling bookings. | UC-02, UC-03, UC-04, UC-11, UC-12 | Farah |
| C11 | Availability | A block of time (date, start, end) an examiner declares available. Validates whether it covers a test slot or overlaps another block. | UC-05, UC-17, UC-20 | Areej |
| C12 | ExaminerAssignment | Links one examiner to a booking, with the assigning admin, time and status (active or revoked). Kept separate to preserve assignment history. | UC-05, UC-14, UC-17 | Areej |
| C13 | ScheduleManager | Controller for Process 4.0. Records availability, checks examiner availability, prevents double assignment, creates and reassigns assignments, logs audit entries, triggers notifications, builds examiner schedules. | UC-05, UC-14, UC-17, UC-18, UC-20 | Areej |
| C14 | Notification | A message sent to a user about an event, with type, text, time sent and read status. Covers all six notification types (examiner assignment, revocation, result available, booking confirmed, cancelled, rescheduled). | UC-05, UC-08 | Areej |
| C15 | NotificationService | Creates and sends notifications: assignment, result and booking notices, plus listing a user's notifications. | UC-03, UC-04, UC-07, UC-08, UC-12 | Areej, Aira |
| C16 | AssignmentStatus (enum) | ACTIVE, REVOKED | UC-05, UC-14 | Areej |
| C17 | NotificationType (enum) | EXAMINER_ASSIGNED, ASSIGNMENT_REVOKED, RESULT_AVAILABLE, BOOKING_CONFIRMED, BOOKING_CANCELLED, BOOKING_RESCHEDULED | UC-08 | Areej, Aira |
| C18 | TestResult | Driving test outcome: pass or fail, score, remarks, submitting examiner, submission time. At most one result per booking. This is the D5 Results record. | UC-07, UC-10, UC-13 | Aira |
| C19 | Certificate | Document issued to applicants who passed. Unique certificate number, issue date, link to the result that earned it. Exists only for PASS results. | UC-10 | Aira |
| C20 | ResultManager | Controller for Process 5.0. Checks examiner assignment and that the test time has passed, records one result per booking, validates fields, returns an applicant's results and history, issues certificates for PASS, writes audit entries and triggers result notification. | UC-07, UC-08, UC-10, UC-13 | Aira |

## Enumerations Added During Consolidation

| Enum | Values | Used by |
|---|---|---|
| Role | APPLICANT, ADMINISTRATOR, EXAMINER | User |
| RecordStatus | LICENSED, RETEST_REQUIRED | Applicant |
| BookingStatus | CONFIRMED, CANCELLED, RESCHEDULED, COMPLETED | Booking |
| Outcome | PASS, FAIL | TestResult |
| ActionType | ACCOUNT_REGISTERED, PROFILE_UPDATED, BOOKING_CREATED, BOOKING_CANCELLED, BOOKING_RESCHEDULED, AVAILABILITY_SUBMITTED, AVAILABILITY_REMOVED, EXAMINER_ASSIGNED, EXAMINER_REASSIGNED, RESULT_SUBMITTED, CERTIFICATE_ISSUED | AuditLog |

## Individual Models

| Student | Diagram file(s) |
|---|---|
| Zainab Kashif | `Individual_Models/Zainab_Kashif/UserandSecurity` |
| Farah Tawalbeh | `Individual_Models/Farah_Tawalbeh/ReservationandBooking` |
| Areej Syed | `Individual_Models/Areej_Syed/ExaminerScheduling`, `AdminOversight`, `Notifications` |
| Aira Khawwar | `Individual_Models/Aira_Khawwar/ResultsandCertificates` |
