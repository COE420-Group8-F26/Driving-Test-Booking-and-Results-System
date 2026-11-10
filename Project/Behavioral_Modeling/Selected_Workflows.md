# Selected Workflows – Lab 7 Activity Diagram Modeling

The activity diagrams model the same use cases selected for sequence diagram modeling in Lab 6 (see [Selected_Use_Cases.md](Selected_Use_Cases.md)). Each diagram gives a workflow view of its use case and complements the matching sequence diagram in `Sequence_Diagrams/`.

| Use Case | Workflow | Diagram File | Swimlanes | Key Decisions | Fork/Join | Traces To |
|---|---|---|---|---|---|---|
| UC-01 | Log In | [AD_UC01_Log_In](Activity_Diagrams/AD_UC01_Log_In.png) | Registered User, System | Account locked? Password correct? failedLoginCount >= 5? Forgot password? Try again? | None (no parallel activities) | FR06, NFR16, «extend» UC-15 (R-10) |
| UC-03 | Book Test Slot | [AD_UC03_Book_Test_Slot](Activity_Diagrams/AD_UC03_Book_Test_Slot.png) | Applicant, BookingManager, NotificationService, AuditLog | Session valid? Cutoff valid? Conflicting booking? Slot available? | Notification and audit entry run in parallel | FR02, FR03, FR05, FR07, FR08, FR16, FR17, NFR13, NFR17 |
| UC-05 | Assign Examiner to Booking | [AD_UC05_Assign_Examiner](Activity_Diagrams/AD_UC05_Assign_Examiner.png) | Administrator, System (ScheduleManager), NotificationService, AuditLog | Session valid? Booking CONFIRMED? Already has an ACTIVE examiner? Examiner free and available? | Notification and audit entry run in parallel | FR10, FR12, «include» UC-20 (R-16) |
| UC-07 | Submit Test Result | [AD_UC07_Submit_Test_Result](Activity_Diagrams/AD_UC07_Submit_Test_Result.png) | Examiner, ResultManager, Booking, TestResult, Applicant | Submission conditions satisfied? Booking active? Result PASS or FAIL? | None | FR04, FR05, FR15, FR19, FR20, NFR17 |

## Notes
- Activity diagrams show workflow and control flow; sequence diagrams show message exchanges. The two views of each use case do not contradict each other.
- Each folder contains the diagram exports (PNG/PDF).
