# Functional Requirements

## Areej Contributions

- **FR-01:** The system shall allow applicants to register using their full name, a verified email address, and a valid password.
- **FR-02:** The system will display real-time available test slots when applicants search for a booking location and date.
- **FR-03:** The system shall prevent two bookings from being made for the same test slot by implementing a transaction block during booking processes.
- **FR-04:** The system shall allow driving examiners to submit a pass or fail grade, alongside optional notes, for any assigned tests to them and mark them as completed.
- **FR-05:** The system shall send automated notifications to applicants when a booking is made, cancelled, or rescheduled, and when test results become available.

## Aira Contributions

- **FR-06:** The system will authenticate users with their email and passwords and redirect each user to their dashboard for their role (applicant, examiner or administrator).
- **FR-07:** The system will create a booking with the status "Confirmed" when an applicant chooses their slot from the available slots. If the applicant already has a booking at the same date and time, the request is rejected.
- **FR-08:** When the chosen slot is booked by another applicant before an applicant’s current booking was completed, the system shall display an error message and prompt the applicant to select another time.
- **FR-09:** The system shall allow applicants to reschedule an upcoming booking from "My Bookings" by selecting a new available slot, and shall release the original slot back to the available pool only once the new booking is confirmed.
- **FR-10:** The system shall allow administrators to assign an available examiner to a confirmed booking that has no examiner, shall reject the assignment if that examiner already has a test at the same date and time, and shall notify the assigned examiner.

## Zainab Contributions

- **FR-11:** The system shall allow applicants to view their complete test history, including past bookings, dates, locations, and pass/fail results.
- **FR-12:** The system shall allow administrators to view a list of all upcoming bookings filtered by date, location, or examiner assignment status.
- **FR-13:** The system shall allow applicants to cancel an upcoming booking, releasing the slot back into the available pool and sending a cancellation confirmation.
- **FR-14:** The system shall allow examiners to view a list of their assigned tests for the day, including applicant name, time, and location.
- **FR-15:** The system shall update an applicant's overall record status (e.g., "Licensed" or "Retest Required") automatically once an examiner submits a pass or fail result.

## Farah Contributions

- **FR-16:** The system shall prevent an applicant from booking a driving test less than 30 minutes before the scheduled start time and shall inform the applicant that the booking cutoff has passed.
- **FR-17:** The system shall generate a unique booking reference number for every successfully confirmed driving test booking.
- **FR-18:** The system shall allow an applicant to view the date, time, location, and status of their upcoming booking from "My Bookings."
- **FR-19:** The system shall record the date and time at which an examiner submits a test result and store it with the applicant's test record.
- **FR-20:** The system shall prevent an examiner from submitting a pass/fail result before the scheduled test time has occurred.


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


# Use Cases

## Areej Contributions

- **UC-01 — Register Applicant Account:** A new applicant creates an account by providing their name, email, and password, which the system verifies before allowing login.
- **UC-02 — Search Available Test Slots:** An applicant searches by location and date and views the real-time list of open test slots.
- **UC-03 — Book Test Slot:** An applicant selects an available slot. The system reserves it, sets the booking status to "Confirmed," and sends a confirmation.
- **UC-04 — Reschedule Booking:** An applicant changes an upcoming booking to a new available slot from "My Bookings." The original slot is released once the new booking is confirmed.
- **UC-05 — Assign Examiner to Booking:** An administrator assigns an available examiner to a confirmed booking that has no examiner. The system updates the booking record and notifies the examiner.

## Zainab Contributions

- **UC-06 — Log In:** A registered user enters their email and password to authenticate and is redirected to the dashboard for their role.
- **UC-07 — Submit Test Result:** An examiner records a pass or fail outcome, along with optional notes, for a completed test and marks the booking as finished.
- **UC-08 — Receive Notification:** The system sends an automated alert to a user when a relevant event occurs, such as a booking change, examiner assignment, or result becoming available.
- **UC-09 — View Booking Details:** An administrator views the details of a specific booking, including applicant, examiner, slot time, and status, from the admin dashboard.
- **UC-10 — Prevent Duplicate Booking:** When two applicants attempt to book the same slot simultaneously, the system rejects the second request and prompts that applicant to choose another slot.

## Aira Contributions

- **UC-11 — Prevent Last-Minute Booking:** An applicant attempts to book a test less than 30 minutes before its start time. The system rejects the request and informs the applicant that the booking cutoff has passed.
- **UC-12 — View Upcoming Booking:** An applicant accesses "My Bookings" to view the date, time, location, and status of their upcoming driving test.
- **UC-13 — Cancel Booking:** An applicant cancels an upcoming driving test. The system cancels the booking, releases the slot, and confirms the cancellation.
- **UC-14 — View Test History:** An applicant views their previous driving tests, including the dates, locations, and pass/fail results.
- **UC-15 — View Assigned Tests:** An examiner views the driving tests assigned to them, including the applicant, scheduled time, and test location.

## Farah Contributions

- **UC-16 — Create Booking Reference:** The system generates a unique booking reference number when an applicant successfully confirms a driving test booking.
- **UC-17 — Update Applicant Record Status:** The system automatically updates an applicant's overall record status after an examiner submits a pass or fail result.
- **UC-18 — Assign Examiner:** An administrator selects an available examiner for a confirmed booking, and the system verifies that the examiner has no conflicting test.
- **UC-19 — Record Test Result Timestamp:** The system records the date and time when an examiner submits a test result and stores it with the applicant's test record.
- **UC-20 — Prevent Early Result Submission:** An examiner attempts to submit a result before the scheduled test time. The system rejects the submission and informs the examiner that the test has not yet occurred.


# Scenarios

## Areej Contributions

### S-01 — Applicant Registration
**Actor:** Applicant

**Scenario:**  
The applicant opens the registration page, enters their full name, verified email address, and valid password, and submits the registration form. The system validates the information, creates the applicant account, and allows the applicant to log in.

### S-02 — Search Available Test Slots
**Actor:** Applicant

**Scenario:**  
The applicant selects a preferred location and date. The system searches the available test slots and displays the real-time list of open slots for the selected criteria.

### S-03 — Book a Test Slot
**Actor:** Applicant

**Scenario:**  
The applicant selects an available test slot. The system checks that the slot is still available, creates the booking, sets its status to "Confirmed," generates a booking reference, and sends a confirmation notification.

### S-04 — Examiner Submits Test Result
**Actor:** Examiner

**Scenario:**  
The examiner opens an assigned completed test and submits a pass or fail result with optional notes. The system records the result, marks the test as completed, and updates the applicant's record.

### S-05 — Booking Notification
**Actor:** Applicant

**Scenario:**  
An applicant books, cancels, or reschedules a test, or their result becomes available. The system detects the event and sends the applicant an appropriate notification.


## Zainab Contributions

### S-06 — User Login
**Actor:** Applicant, Examiner, Administrator

**Scenario:**  
A registered user enters their email and password. The system authenticates the credentials and redirects the user to the dashboard associated with their role.

### S-07 — View Test History
**Actor:** Applicant

**Scenario:**  
The applicant opens their test history. The system retrieves and displays their previous bookings, dates, locations, and pass/fail results.

### S-08 — View Upcoming Bookings
**Actor:** Administrator

**Scenario:**  
The administrator opens the upcoming bookings section and filters the bookings by date, location, or examiner assignment status. The system displays the matching bookings.

### S-09 — Cancel Booking
**Actor:** Applicant

**Scenario:**  
The applicant selects an upcoming booking and chooses to cancel it. The system cancels the booking, releases the test slot, and sends a cancellation confirmation.

### S-10 — View Assigned Tests
**Actor:** Examiner

**Scenario:**  
The examiner opens their assigned tests for the day. The system displays each assigned applicant's name, scheduled time, and test location.


## Aira Contributions

### S-11 — Reschedule Booking
**Actor:** Applicant

**Scenario:**  
The applicant selects an upcoming booking from "My Bookings" and chooses to reschedule it. The system displays available slots, confirms the new slot, releases the original slot, and sends a rescheduling notification.

### S-12 — Assign Examiner to Booking
**Actor:** Administrator

**Scenario:**  
The administrator selects a confirmed booking without an examiner and chooses an available examiner. The system checks for scheduling conflicts, assigns the examiner if available, and sends a notification.

### S-13 — Prevent Duplicate Booking
**Actor:** Applicant, System

**Scenario:**  
Two applicants attempt to book the same test slot at nearly the same time. The system processes the requests and confirms the slot for only one applicant. The other applicant receives an error message and is prompted to select another slot.

### S-14 — Prevent Last-Minute Booking
**Actor:** Applicant

**Scenario:**  
The applicant attempts to book a driving test less than 30 minutes before its scheduled start time. The system rejects the booking and informs the applicant that the booking cutoff has passed.

### S-15 — Receive Notification
**Actor:** Applicant, Examiner

**Scenario:**  
A relevant system event occurs, such as a booking confirmation, cancellation, rescheduling, examiner assignment, or result availability. The system generates and sends the appropriate notification to the affected user.


## Farah Contributions

### S-16 — View Upcoming Booking
**Actor:** Applicant

**Scenario:**  
The applicant opens "My Bookings." The system displays the date, time, location, booking reference number, and current status of their upcoming driving test.

### S-17 — Generate Booking Reference
**Actor:** System

**Scenario:**  
An applicant successfully confirms a driving test booking. The system generates a unique booking reference number and stores it with the booking record.

### S-18 — Update Applicant Record
**Actor:** Examiner, System

**Scenario:**  
The examiner submits a pass or fail result for a completed driving test. The system records the result and automatically updates the applicant's overall record status, such as "Licensed" or "Retest Required."

### S-19 — Record Result Submission Time
**Actor:** Examiner, System

**Scenario:**  
The examiner submits a test result. The system records the exact date and time of submission and stores the timestamp with the applicant's test record.

### S-20 — Prevent Early Result Submission
**Actor:** Examiner

**Scenario:**  
The examiner attempts to submit a pass/fail result before the scheduled test time. The system checks the test time, rejects the submission, and informs the examiner that the result cannot be submitted before the test occurs.