# Use Cases

## Aira Contributions

- **UC-01 — Log In:** A registered user enters their email and password to authenticate and is redirected to the dashboard for their role.
- **UC-02 — Search Available Test Slots:** An applicant searches by location and date and views the real-time list of open test slots.
- **UC-03 — Book Test Slot:** An applicant selects an available slot. The system verifies that the slot remains available and that the test starts at least 30 minutes later. If the booking is valid, the system reserves the slot, sets its status to "Confirmed," generates a booking reference number, and sends confirmation. Otherwise, the system rejects the request and informs the applicant of the reason.
- **UC-04 — Reschedule Booking:** An applicant changes an upcoming booking to a new available slot from "My Bookings." The original slot is released once the new booking is confirmed.
- **UC-05 — Assign Examiner to Booking:** An administrator assigns an available examiner to a confirmed booking that has no examiner. The system updates the booking record and notifies the examiner.


## Zainab Contributions

- **UC-06 — Register Applicant Account:** A new user creates an account by providing their name, email, and password, which the system verifies before allowing login.
- **UC-07 — Submit Test Result:** An examiner records a pass or fail outcome, along with optional notes, for a completed test and marks the booking as finished.
- **UC-08 — Receive Notification:** The system sends an automated alert to a user when a relevant event occurs, such as a booking change, examiner assignment, or result becoming available.
- **UC-09 — View Booking Details:** An administrator views the details of a specific booking, including applicant, examiner, slot time, and status, from the admin dashboard.
- **UC-10 — Download Test Result Certificate:** An applicant who has passed their driving test downloads a certificate or confirmation document from their account for their records.


## Farah Contributions

- **UC-11 — View Upcoming Booking:** An applicant accesses "My Bookings" to view the date, time, location, and status of their upcoming driving test.
- **UC-12 — Cancel Booking:** An applicant cancels an upcoming driving test. The system cancels the booking, releases the slot, and confirms the cancellation.
- **UC-13 — View Test History:** An applicant views their previous driving tests, including the dates, locations, and pass/fail results.
- **UC-14 — View Assigned Tests:** An examiner views the driving tests assigned to them, including the applicant, scheduled time, and test location.
- **UC-20 — View Examiner Availability:** An administrator views the examiners available for a selected test date and time before assigning an examiner to a booking.


## Areej Contributions

- **UC-15 — Reset Forgotten Password:** A user who does not remember their password requests a reset link via their registered email, sets a new password, and regains account access.
- **UC-16 — Update Profile Information:** A logged-in applicant edits personal details, such as their address or phone number. The system then updates and saves the information.
- **UC-17 — Set Examiner Availability:** An examiner logs in and selects the day/time slots that match their availability to conduct tests; the system uses this information when administrators assign examiners to bookings.
- **UC-18 — Filter Booking List:** An administrator filters the complete list of bookings by location, examiner-assignment status, or date when managing system-wide scheduling.
- **UC-19 — Log Out:** A logged-in user session ends, and the system invalidates access until they are logged in again.


## Team Consolidated Use Cases

- **UC-01 — Log In:** A registered user enters their email and password to authenticate and is redirected to the dashboard for their role.
- **UC-02 — Search Available Test Slots:** An authenticated applicant searches by location and date and views the real-time list of open test slots.
- **UC-03 — Book Test Slot:** An authenticated applicant selects an available slot. The system verifies that the slot remains available and that the test starts at least 30 minutes later. If the booking is valid, the system reserves the slot, sets its status to "Confirmed," generates a booking reference number, and sends confirmation. Otherwise, the system rejects the request and informs the applicant of the reason.
- **UC-04 — Reschedule Booking:** An authenticated applicant changes an upcoming booking to a new available slot from "My Bookings." The original slot is released once the new booking is confirmed.
- **UC-05 — Assign Examiner to Booking:** An authenticated administrator assigns an available examiner to a confirmed booking that has no examiner. The system updates the booking record and notifies the examiner.
- **UC-06 — Register Applicant Account:** A new user creates an account by providing their name, email, and password, which the system verifies before allowing login.
- **UC-07 — Submit Test Result:** An authenticated examiner records a pass or fail outcome, along with optional notes, for a completed test and marks the booking as finished.
- **UC-08 — Send Notification:** The system sends an automated alert to a user when a relevant event occurs, such as a booking change, examiner assignment, or result becoming available.
- **UC-09 — View Booking Details:** An authenticated administrator views the details of a specific booking, including applicant, examiner, slot time, and status, from the admin dashboard.
- **UC-10 — Download Test Result Certificate:** An authenticated applicant who has passed their driving test downloads a certificate or confirmation document from their account for their records.
- **UC-11 — View Upcoming Booking:** An authenticated applicant accesses "My Bookings" to view the date, time, location, and status of their upcoming driving test.
- **UC-12 — Cancel Booking:** An authenticated applicant cancels an upcoming driving test. The system cancels the booking, releases the slot, and confirms the cancellation.
- **UC-13 — View Test History:** An authenticated applicant views their previous driving tests, including the dates, locations, and pass/fail results.
- **UC-14 — View Assigned Tests:** An authenticated examiner views the driving tests assigned to them, including the applicant, scheduled time, and test location.
- **UC-15 — Reset Forgotten Password:** A user who does not remember their password requests a reset link via their registered email, sets a new password, and regains account access.
- **UC-16 — Update Profile Information:** An authenticated applicant edits personal details, such as their address or phone number. The system then updates and saves the information.
- **UC-17 — Set Examiner Availability:** An authenticated examiner logs in and selects the day/time slots that match their availability to conduct tests; the system uses this information when administrators assign examiners to bookings.
- **UC-18 — Filter Booking List:** An authenticated administrator filters the complete list of bookings by location, examiner-assignment status, or date when managing system-wide scheduling.
- **UC-19 — Log Out:** A authenticated user session ends, and the system invalidates access until they are logged in again.
- **UC-20 — View Examiner Availability:** An authenticated administrator views the examiners available for a selected test date and time before assigning an examiner to a booking.

## Use Case Relationship Table

| **Relationship ID** | **Base Use Case** | **Related Use Case** | **Relationship** | **Justification** |
|---------------------|-------------------|----------------------|------------------|-------------------|
| **R-01** | Reschedule Booking | Book Test Slot | <<include>> | Every reschedule requires the applicant to select and confirm a new slot, which is the same behavior as booking (S-02). |
| **R-02** | Book Test Slot | Search Available Test Slots | <<include>> | An applicant must view the available slots before selecting one (S-01). |
| **R-03** | Submit Test Result | Receive Notification | <<include>> | Every time an examiner submits a result, the system always sends a notification to the applicant that their result is available (S-03), making this a required step, not optional. |
| **R-04** | Log In | Reset Forgotten Password | <<extend>> | When a user cannot remember their password while attempting to log in, they may optionally initiate the password-reset process. |
| **R-05** | Cancel Booking | Send Notification | <<include>> | Every successful cancellation sends the applicant a cancellation confirmation, making the notification a required part of the cancellation process. |
| **R-06** | Assign Examiner to Booking | View Examiner Availability | <<include>> | Before assigning an examiner, the administrator must view which examiners are available for the selected test date and time. |
| **R-07** | Book Test Slot | Send Notification | <<include>> | Every confirmed booking sends a confirmation |
| **R-08** | Assign Examiner to Booking | Send Notification Availability | <<include>> | Every assignment notifies the examiner. |
