# Driving Test Booking and Results System

A web-based system for scheduling driving tests and managing their results for applicants, driving examiners, and administrators.

**Course:** COE 420 – Software Engineering (Sec 02), Fall 2026
**University:** American University of Sharjah, College of Engineering
**Team:** Group 8

---

## Overview

The system digitizes and centralizes the driving test process:

- **Applicants** register, view available test slots, book, reschedule or cancel tests, and view their results and test history.
- **Driving examiners** declare their availability, view assigned tests, and submit pass/fail results.
- **Administrators** view and filter bookings, view examiner availability, and assign or reassign examiners.

## Core Features

- **Account management:** registration, role-based login and logout, password reset, applicant profile updates; account lockout for 15 minutes after 5 failed logins
- **Booking and scheduling:** real-time slot availability, 30-minute booking cutoff, conflict checks, and double-booking prevention
- **Examiner assignment:** examiner availability, assignment and reassignment with schedule-clash checks
- **Result management:** pass/fail submission by examiners (one result per booking), automatic update of the applicant's record status, and downloadable certificates for passed tests
- **Notifications:** booking confirmed/rescheduled/cancelled, examiner assigned/removed, result available; failed notifications are retried 3 times, then the administrator is alerted
- **Test history:** past bookings, results, and record status for applicants
- **Audit log:** append-only record of key actions

## Out of Scope

- Online payment gateway integration for test fees
- Integration with external national ID / government verification systems
- Multi-language support
- Integration with third-party driving school or lesson-booking platforms

## Development Approach

- **Process model:** Incremental. Each increment adds functionality to the previous version (account management, booking and scheduling, examiner management, results and test history), followed by notification integration, system integration and testing, and deployment.
- **Architecture:** 3-layer closed architecture (presentation, application, data), where each layer only calls the layer directly below it.

## Tech Stack

Not yet finalized. Candidates:

- **Frontend:** HTML, CSS, JavaScript
- **Backend:** Python or Java
- **Database:** PostgreSQL or MySQL

## Project Status

- Requirements, planning, modeling, and architecture design: complete
- Source code development: in progress

## Repository Structure

````
Driving-Test-Booking-and-Results-System/
├── Documents/
│   └── .gitkeep
├── Project/
│   ├── Behavioral_Modeling/
│   │   ├── Activity_Diagrams/
│   │   │   ├── AD_UC01_Log_In.png
│   │   │   ├── AD_UC03_Book_Test_Slot.png
│   │   │   ├── AD_UC05_Assign_Examiner_to_Booking.pdf
│   │   │   └── AD_UC07_Submit_Test_Result.png
│   │   ├── Sequence_Diagrams/
│   │   │   ├── UC-01.png
│   │   │   ├── UC-03.png
│   │   │   ├── UC-05.png
│   │   │   └── UC-07.png
│   │   ├── Selected_Use_Cases.md
│   │   └── Selected_Workflows.md
│   ├── Data_Flow_Modeling/
│   │   ├── Context_Diagram/
│   │   │   └── Context Diagram.png
│   │   ├── Level_0_DFD/
│   │   │   └── lvl0 diagram.png
│   │   ├── Core_Processes_Matrix.md
│   │   └── DFD_Consistency_Check.md
│   ├── Function_Point_Analysis/
│   │   ├── FPA_Report.pdf
│   │   ├── Function_Point_Calculations.xlsx
│   │   └── Function_Point_Components.xlsx
│   ├── Object_Modeling/
│   │   ├── Class_Diagram/
│   │   ├── Individual_Models/
│   │   ├── Class_Inventory.md
│   │   ├── Class_Model_Consistency_Check.md
│   │   └── Integration_Notes.md
│   ├── Project_Scheduling/
│   │   ├── Gantt_Chart/
│   │   │   └── Gantt_Chart.png
│   │   ├── Network_Schedule/
│   │   │   └── Network_Schedule.png
│   │   ├── Critical_Path.md
│   │   └── WBS.md
│   ├── Requirements/
│   │   ├── Use_Case_Diagram/
│   │   │   ├── .gitkeep
│   │   │   └── Driving Test Booking System.png
│   │   ├── Functional_Requirements.md
│   │   ├── Non_Functional_Requirements.md
│   │   ├── Scenarios.md
│   │   └── Use_Cases.md
│   ├── Software_Architecture/
│   │   ├── Component_Diagram/
│   │   ├── Architectural_Design_Goals.md
│   │   ├── Architectural_Style_Selection.md
│   │   ├── Class_Distribution.md
│   │   └── Component_Descriptions.md
│   ├── .gitkeep
│   ├── Feasibility_Study.md
│   ├── Process_Model.md
│   ├── Project_Description.md
│   ├── Project_Title.md
│   ├── Risk_Register.md
│   ├── Scope.md
│   └── Stakeholder.md
├── Source_Code/
├── Team/
└── README.md
````

## Team (Group 8)

| Name | Major |
|------|-------|
| Areej Syed | Computer Science |
| Farah Tawalbeh | Computer Engineering |
| Aira Khawwar | Computer Science |
| Zainab Kashif | Computer Science |



