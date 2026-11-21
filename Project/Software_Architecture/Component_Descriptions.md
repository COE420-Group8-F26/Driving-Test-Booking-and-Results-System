# Component Descriptions

**Project:** Driving Test Booking and Results System  
**Course:** COE420L — Software Engineering, Lab 8  
**Exercise:** 3 — Identify Components and Distribute Project Classes

The system uses the selected closed three-layer architectural style: a presentation layer, an application (middleware) layer, and a data layer. The six components and their responsibilities below follow Exercise 3 of the Lab 8 report.

## CO1 — Web User Interface

**Layer:** Presentation

Provides the web pages and dashboards for applicants, examiners, and administrators. Collects user input, sends every request to the application server, and displays results and error messages. It never accesses the data layer directly (closed architecture, NFR-11).

## CO2 — Account and Access Control

**Layer:** Application

Handles registration, profile updates, password reset, login, and logout. Authenticates users, implements a 15-minute lockout after five failed logins (NFR-16), checks role permissions before calling any other component, and validates sessions (DG-01, NFR-11). After a result, updates the applicant's record status (FR-15).

## CO3 — Booking and Scheduling

**Layer:** Application

Searches available slots; creates, reschedules, and cancels bookings; enforces the 30-minute cutoff (FR-16) and booking conflict rules (FR-07); and automatically reserves slots to prevent double booking (FR-03, NFR-13, DG-02). Records examiner availability and assigns examiners while preventing schedule clashes (FR-10, FR-24). Provides booking lists and filters for administrators.

## CO4 — Results and Certification

**Layer:** Application

Checks that the examiner is assigned and the test time has passed (FR-20), records one result per booking (FR-07, FR-19), marks the booking completed, provides results and test history (FR-11), and issues certificates only for PASS results (FR-26).

## CO5 — Notification and Audit

**Layer:** Application

Creates and sends notifications for booking, rescheduling, cancellation, examiner assignment, and result events (FR-05, NFR-15). Writes append-only audit entries for audited actions (NFR-17).

## CO6 — Data Management

**Layer:** Data

Stores the shared domain records used by more than one application component: bookings, test slots, availability, examiner assignments, results, and certificates. Enforces consistency rules to prevent orphan records (NFR-19) and ensure only one active booking per slot or active assignment per booking.
