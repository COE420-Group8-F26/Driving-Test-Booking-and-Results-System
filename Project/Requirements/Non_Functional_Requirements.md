# Non-Functional Requirements

## Areej Contributions

- **NFR-01 — Security:** To protect applicant and examiner information from unauthorized access, the system shall encrypt all sensitive details and test results in transit and at rest.
- **NFR-02 — Performance:** The system shall return a confirmation to the user within 2 seconds considering normal load conditions, after processing a test booking or rescheduling request.
- **NFR-03 — Reliability/Availability:** The system shall be available at least 99% of the time to ensure administrators, applicants, and driving examiners can access system functions without major disruptions.
- **NFR-04 — Usability:** The system user interface should be simple and easy to navigate such that a new applicant can register and book a test within 5 minutes without additional assistance.
- **NFR-05 — Scalability:** The system shall accommodate 500 or more concurrent users performing booking, cancellation, rescheduling, or result submission operations without response times degrading.

## Zainab Contributions

- **NFR-06 — Maintainability:** The system shall be built using modular components for all major features (booking, results, notifications) so that a fault or update in one module can be fixed or deployed without requiring changes to the others.
- **NFR-07 — Portability:** The system's web interface shall function correctly on the latest two versions of major browsers (Chrome, Firefox, Safari, Edge) without requiring browser-specific workarounds.
- **NFR-08 — Robustness:** If a booking request fails due to a system or network error, the system shall display a clear error message and leave no partial or duplicate booking record in the database.
- **NFR-09 — Size:** The system shall support storage and retrieval of at least 100,000 applicant booking and result records without a noticeable decrease in page load performance.
- **NFR-10 — Recoverability:** In the event of a system failure or crash, the system shall automatically back up booking and result data at least every 24 hours and restore the system to its last saved state within 4 hours.

## Aira Contributions

- **NFR-11 — Security:** The system shall enforce role-based access control so that applicants, examiners, and administrators can only access the functions assigned to their role, and any unauthorized request (e.g., an applicant opening the admin dashboard) shall be rejected with an access-denied response in 100% of tested cases.
- **NFR-12 — Performance:** The system shall display available test slot search results within 3 seconds for at least 95% of search requests under normal load conditions.
- **NFR-13 — Reliability:** The system shall guarantee that a test slot is never assigned to more than one applicant: when 100 simultaneous booking requests are sent for the same slot, exactly one shall be confirmed and the other 99 shall be rejected.
- **NFR-14 — Usability:** The system's web interface shall display all pages correctly on screen widths from 360 px (mobile) to 1920 px (desktop) without requiring horizontal scrolling.
- **NFR-15 — Performance:** The system shall deliver notifications (booking confirmation, rescheduling, examiner assignment, and result availability) within 60 seconds of the triggering event for at least 95% of notifications under normal load conditions.

## Farah Contributions

- **NFR-16 — Security:** The system shall temporarily lock a user account for 15 minutes after 5 consecutive failed login attempts.
- **NFR-17 — Auditability:** The system shall create an audit record for 100% of booking creation, booking cancellation, test-slot modification, and result-submission actions, including the user, action performed, and timestamp.
- **NFR-18 — Performance:** Any change to test-slot or examiner availability shall be reflected throughout the system within 5 seconds of being saved under normal load conditions.
- **NFR-19 — Data Integrity:** Every booking record shall be linked to a valid applicant and test slot, and every submitted test result shall be linked to a valid booking, with zero orphan records in database integrity tests.
- **NFR-20 — Accessibility:** All primary booking, cancellation, and result-related functions shall be fully operable using keyboard-only navigation.