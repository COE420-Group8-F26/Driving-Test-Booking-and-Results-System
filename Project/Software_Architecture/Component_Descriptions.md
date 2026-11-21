# Component Descriptions – Lab 8

The system follows a closed 3-layer architecture (see Architectural_Style_Selection.md). A component may only use components in its own layer or the layer directly below.

## Components

| ID | Component | Layer | Responsibilities | Included Classes |
|---|---|---|---|---|
| CO1 | Web User Interface | Presentation | Provides the web pages and dashboards for applicants, examiners and administrators. Collects user input, sends every request to the application layer, and displays results and error messages. It never accesses the data layer directly (closed architecture, NFR-11). | None. Lab 5 is a domain model with no UI classes. |
| CO2 | Account and Access Control | Application | Registration, profile updates, password reset, login and logout. Authenticates users, implements the 15-minute lockout after 5 failed logins (NFR-16), checks role permissions before calling any other component, and validates sessions (DG-01, NFR-11). After a result, updates the applicant's record status (FR15). | User, Applicant, Examiner, Administrator, Role, RecordStatus, Session, PasswordResetToken |
| CO3 | Booking and Scheduling | Application | Searches available slots; creates, reschedules and cancels bookings; enforces the 30-minute cutoff (FR16) and booking-conflict rules (FR07); reserves slots atomically to prevent double booking (FR03, NFR-13, DG-02). Records and removes examiner availability, and assigns and reassigns examiners while preventing schedule clashes (FR10, FR24, FR28, FR29). Provides booking lists, filters and booking details for administrators (FR12, FR21). | BookingManager, ScheduleManager |
| CO4 | Results and Certification | Application | Checks that the examiner is assigned and the test time has passed (FR20), records one result per booking (FR04, FR19), marks the booking completed, provides results and test history (FR11), and issues certificates only for PASS results (FR26). | ResultManager |
| CO5 | Notification and Audit | Application | Creates and sends notifications for booking, rescheduling, cancellation, examiner assignment, reassignment and result events (FR05, NFR-15), and lets users view their notifications (FR30). Retries failed notifications up to 3 times and alerts the administrator if they still fail (FR27). Writes append-only audit entries for audited actions (NFR-17). | NotificationService, Notification, NotificationType, AuditLog, ActionType |
| CO6 | Data Management | Data | Stores the shared domain records used by more than one application component: bookings, test slots, availability, examiner assignments, results and certificates. Enforces consistency rules to prevent orphan records (NFR-19) and ensures only one active booking per slot and one active assignment per booking. | Booking, BookingStatus, TestSlot, Availability, ExaminerAssignment, AssignmentStatus, TestResult, Outcome, Certificate |

## Component Interfaces

| # | Interface | Provider | Required By | Main Operations |
|---|---|---|---|---|
| 01 | IAccountService | CO2 | CO1 | register(), login(), logout(), changePassword(), resetPassword(), updateProfile() |
| 02 | IAccessControlService | CO2 | CO1, CO3, CO4 | isValid(), getUser(), updateRecordStatus() |
| 03 | IBookingService | CO3 | CO1 | searchAvailableSlots(), validateCutoff(), checkBookingConflict(), createBooking(), cancelBooking(), rescheduleBooking(), getBookingHistory(), getUpcomingBooking(), getBookingDetails(), filterBookings() |
| 04 | ISchedulingService | CO3 | CO1 | recordAvailability(), removeAvailability(), getAvailableExaminers(), assignExaminer(), reassignExaminer(), getScheduleFor() |
| 05 | IResultService | CO4 | CO1 | canSubmitResult(), submitResult(), getResult(), getTestHistory(), issueCertificate() |
| 06 | INotificationService | CO5 | CO1, CO3, CO4 | notifyBookingConfirmed(), notifyBookingCancelled(), notifyBookingRescheduled(), notifyExaminerAssigned(), notifyAssignmentRevoked(), notifyResultAvailable(), getNotificationsFor(), alertNotificationFailure() |
| 07 | IAuditService | CO5 | CO2, CO3, CO4 | createEntry() |
| 08 | IAccountData | CO6 | CO2 | getUserByEmail(), saveUser(), saveSession(), savePasswordResetToken() |
| 09 | IBookingData | CO6 | CO3, CO4 | createBookingRecord(), confirm(), cancel(), reschedule(), markCompleted(), reserve(), release(), isAvailable() |
| 10 | IScheduleData | CO6 | CO3, CO4 | saveAvailability(), getAvailability(), createAssignment(), getActiveAssignment(), revoke() |
| 11 | IResultData | CO6 | CO4 | createResult(), getResult(), isPass(), saveCertificate() |
| 12 | INotificationData | CO6 | CO5 | saveNotification(), getNotificationsFor(), saveAuditEntry() |

Full signatures (parameters and return types) are shown in Component_Diagram/Software_Architecture_Component_Diagram.pdf.
