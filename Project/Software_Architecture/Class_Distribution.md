# Class Distribution

**Project:** Driving Test Booking and Results System  
**Course:** COE420L — Software Engineering, Lab 8  
**Exercise:** 3 — Identify Components and Distribute Project Classes

The table assigns all classes from the consolidated Lab 5 UML Class Diagram to one primary component, following the distribution specified in Exercise 3 of the Lab 8 report.

| ID | Component Name | Architectural Layer | Included Classes |
|---|---|---|---|
| CO1 | Web User Interface | Presentation | None. Lab 5 is a domain model consisting of no UI classes. |
| CO2 | Account and Access Control | Application | User, Applicant, Examiner, Administrator, Role, RecordStatus, Session, PasswordResetToken |
| CO3 | Booking and Scheduling | Application | BookingManager, ScheduleManager |
| CO4 | Results and Certification | Application | ResultManager |
| CO5 | Notification and Audit | Application | NotificationService, Notification, NotificationType, AuditLog, ActionType |
| CO6 | Data Management | Data | Booking, BookingStatus, TestSlot, Availability, ExaminerAssignment, AssignmentStatus, TestResult, Outcome, Certificate |

## Distribution Rationale

- **CO1** contains no classes from the Lab 5 domain model; it provides the user interface without direct data-layer access.
- **CO2** groups user accounts, roles, sessions, and password-reset functionality.
- **CO3** groups the managers responsible for booking operations and examiner scheduling.
- **CO4** contains the manager responsible for results and certification.
- **CO5** groups notification and audit functionality and related types.
- **CO6** groups shared records and related status/outcome types, maintaining data integrity.

Each class is assigned to one primary component, and the distribution matches the six components identified in Exercise 3.
