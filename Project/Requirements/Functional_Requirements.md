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