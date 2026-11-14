# Architectural Design Goals

**System:** Driving Test Booking and Results System

## Summary

| Goal ID | Design Goal | Related Requirements | Priority |
|:--|:--|:--|:--|
| DG-01 | Security | NFR-01, NFR-11, NFR-16, FR-06 | High |
| DG-02 | Reliability and Data Integrity | NFR-13, NFR-08, NFR-19, FR-03 | High |

## DG-01: Security

| Field | Description |
|:--|:--|
| **Goal ID** | DG-01 |
| **Design Goal** | Security |
| **Description** | Only authenticated users may use the system, each user may use only the functions of their role, and applicant, examiner and result data are protected from unauthorized access. |
| **Related Requirement** | NFR-01 (encryption in transit and at rest), NFR-11 (role-based access control), NFR-16 (account lockout after 5 failed logins); FR-06 (role-based login and redirection) |
| **Priority** | High |
| **Justification** | The system stores personal data and official test results. A breach or a role violation, such as an applicant opening the admin dashboard, would harm users and the testing authority. Security rules also have to be enforced in one place, because every use case depends on Log In. |

## DG-02: Reliability and Data Integrity

| Field | Description |
|:--|:--|
| **Goal ID** | DG-02 |
| **Design Goal** | Reliability and Data Integrity |
| **Description** | The system must never leave bookings or results in an inconsistent state. A slot is never given to two applicants, failed requests leave no partial records, and every record points to a valid parent record. |
| **Related Requirement** | NFR-13 (one confirmed booking out of 100 simultaneous requests), NFR-08 (no partial or duplicate booking after a failure), NFR-19 (no orphan records); FR-03 (prevent double booking) |
| **Priority** | High |
| **Justification** | Double bookings and half-saved records are the most damaging failures for this system, because applicants arrive for tests that cannot happen. These guarantees must be enforced centrally with database transactions, not left to individual features. |