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
- **UC-10 — Download Test Result Certificate** An applicant who has passed their driving test downloads a certificate or confirmation document from their account for their records. 



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