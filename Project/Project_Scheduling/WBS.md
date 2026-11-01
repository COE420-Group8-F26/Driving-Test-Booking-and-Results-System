# Work Breakdown Structure (WBS)

| **ID** | **Task Name** | **Description** | **Predecessor(s)** | **Duration (Days)** |
| --- | --- | --- | --- | --- |
| **T1** | Requirements Refinement | Finalize the list of scenarios, functional requirements, non-functional requirements, and use cases for the Driving Test Booking and Results System. | - | **2** |
| **T2** | Database Design | Design the database (how the information is going to be stored) for things like user accounts, test slots, bookings, examiner availability, test results, and applicant records while maintaining the data’s relationships and data integrity. | T1 | **3** |
| **T3** | User Interface Design | Design the applicant, examiner, and administrator interfaces: login, booking, scheduling, results, test history, and dashboard pages. | T1 | **3** |
| **T4** | Account Management Increment | Implement registration, role-based login, logout, password reset, and applicant profile updates. | T2, T3 | **4** |
| **T5** | Booking and Scheduling Increment | Implement important applications like searching available test slots, booking, viewing upcoming bookings, cancellation, rescheduling, booking references, and also the prevention of double-booking. | T4 | **6** |
| **T6** | Examiner Management Increment | Implementing the admin/examiner side of scheduling: examiner availability, administrator viewing of examiner availability, examiner assignment to bookings, and examiner access to assigned tests. | T4 | **4** |
| **T7** | Results and Test History Increment | Implement pass/fail result submission, completion of bookings, applicant result viewing, test history, applicant record updates, and the downloadable result certificates. | T5, T6 | **5** |
| **T8** | Notification Integration | Implement automated notifications for booking confirmations, cancellations, rescheduling, examiner assignments, and result availability. | T7 | **3** |
| **T9** | System Integration and Testing | Integrate all the completed increments and also test the functionality of the system: security, access control, booking conflicts, data integrity, performance, and error handling. | T8 | **5** |
| **T10** | Deployment and Final Release | Deploy the fully developed Driving Test Booking and Results System to production. Perform final deployment checks, configure the system for real-world use, verify that all modules are operational, and officially release the system for applicants, examiners, and administrators. | T9 | **3** |
