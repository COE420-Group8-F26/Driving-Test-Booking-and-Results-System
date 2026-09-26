# Driving Test Booking and Results System

The Driving Test Booking and Results System organizes and centralizes the process of scheduling driving tests and managing their results for applicants, driving examiners, and administrators.

Developed for **COE 420 – Software Engineering (Section 02)**, Fall 2026, American University of Sharjah.

## Overview

Applicants can register, view available test slots, manage their bookings, and access their results. Driving examiners can view assigned tests and submit pass or fail results. Administrators manage schedules, bookings, examiner assignments, and test records.

A test booking moves through different states, from booking to completion or cancellation. Once a test is completed, the examiner records a pass or fail result, and the system updates the applicant's record accordingly. The system also sends notifications when relevant changes occur, such as a booking being rescheduled or a result becoming available.

**Core functionality:**
- Account management (registration, role-based login)
- Test booking, rescheduling, and cancellation with conflict prevention
- Examiner assignment
- Result submission and record updates
- Notifications
- Test history

**Out of scope (for now):** online payment integration, government ID verification integration, multi-language support, third-party driving-school integrations.

## Team — Group 8

| Name | Major |
|---|---|
| Areej Syed | Computer Science |
| Farah Tawalbeh | Computer Engineering |
| Aira Khawar | Computer Science |
| Zainab Kashif | Computer Science |

Contact details and individual skill sets are listed under [`Team/`](./Team).

## Repository Structure

```
.
├── Documents/                          # Supplementary project documents
├── Project/
│   ├── Project_Title.md
│   ├── Project_Description.md
│   ├── Scope.md
│   ├── Feasibility_Study.md
│   ├── Process_Model.md
│   ├── Risk_Register.md
│   ├── Stakeholder.md
│   └── Requirements/
│       ├── Use_Cases.md
│       ├── Scenarios.md
│       ├── Functional_Requirements.md
│       └── Non_Functional_Requirements.md
├── Source_Code/                        # Application source code (in progress)
└── Team/
    ├── Team_Members.md
    ├── Skills.md
    └── Contact_Information.md
```

## Development Approach

The team is using an **Incremental Model**: the system is broken into functional increments (e.g., registration/login, then booking/scheduling, then examiner assignment, results, and notifications), with each increment integrated and tested before the next begins. See [`Project/Process_Model.md`](./Project/Process_Model.md) for details.

## Tech Stack

Frontend, backend language, and database are still being finalized. Candidates under consideration:
- **Frontend:** HTML, CSS, JavaScript
- **Backend:** Python or Java
- **Database:** PostgreSQL or MySQL

This section will be updated once the stack is locked in.

## Requirements & Design Docs

- [Project Scope](./Project/Scope.md)
- [Feasibility Study](./Project/Feasibility_Study.md)
- [Stakeholder Analysis](./Project/Stakeholder.md)
- [Risk Register](./Project/Risk_Register.md)
- [Use Cases](./Project/Requirements/Use_Cases.md)
- [Scenarios](./Project/Requirements/Scenarios.md)
- [Functional Requirements](./Project/Requirements/Functional_Requirements.md)
- [Non-Functional Requirements](./Project/Requirements/Non_Functional_Requirements.md)

## Project Status

🚧 In progress — requirements and design stage complete (scope, feasibility study, risk register, stakeholder analysis, use cases, scenarios, functional and non-functional requirements). Source code development has not yet started.

## License

TBD
