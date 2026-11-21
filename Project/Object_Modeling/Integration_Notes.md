# Integration Notes

## 1. Merged Duplicate Classes

Several classes appeared in more than one individual model. Each was merged into a single definition, as summarised below.

| Class | Source of Duplication | Resolution |
|---|---|---|
| User | Full version in the Users and Security model; reduced versions (userId and name only) in the Examiner Scheduling, Admin Oversight, Results and Notifications models. | The full version was retained because it contains the authentication, lockout and password reset attributes. The reduced versions were deleted. |
| Examiner | Individual models of Zainab, Areej and Aira. | Merged into one class containing all attributes (examinerNumber, licenseCategories) and the methods submitAvailability, viewMySchedule and submitResult. |
| Administrator | Users and Security model and Admin Oversight model. | Merged. The method reassignExaminer was taken from the Admin Oversight model. filterBookings was moved to BookingManager (Section 3). |
| Applicant | Users and Security model and Results model. | Merged. viewMyResult and requestCertificate are listed once. |
| Booking | Examiner Scheduling, Admin Oversight, Results and Booking models. | The Booking model version was used as the base because it is the most complete. Its names were standardised (Section 3). |
| TestSlot | Examiner Scheduling model (reduced) and Booking model. | The Booking model version was used, with endTime taken from the Examiner Scheduling version. |
| ExaminerAssignment | Examiner Scheduling and Admin Oversight models. | Merged into a single definition. |
| ScheduleManager | Examiner Scheduling and Admin Oversight models. | Merged. assignExaminer and reassignExaminer were added to the Examiner Scheduling method list. |
| AuditLog | Full version in the Users and Security model; name-only copy in the Admin Oversight model. | The full version was retained. |
| NotificationType, BookingStatus, Outcome | Drawn in more than one individual diagram. | Each enumeration is now defined once. |

## 2. Removed Elements

- **Foreign key attributes.** Several classes contained both an identifier attribute and an association to the same class, which represented the same relationship twice. The identifier attributes were removed and the named association now carries the link: Availability.examinerId, ExaminerAssignment.bookingId, ExaminerAssignment.examinerId, ExaminerAssignment.assignedByAdminId, TestResult.bookingId, TestResult.examinerId, Certificate.resultId, Notification.recipientId, Session.userId, PasswordResetToken.userId, AuditLog.performedBy and Booking.testSlot. Foreign keys remain necessary in the database schema, but they are an implementation detail and are not part of the class model.
- **Reduced class copies.** The reduced copies of User, Examiner, Applicant, Booking and TestSlot, the name-only AuditLog in the Admin Oversight model, and the name-only ResultManager and ScheduleManager in the Notifications model were deleted.
- **Methods replaced by manager operations.** Administrator.viewExaminerAvailability was replaced by ScheduleManager.getAvailableExaminers (UC-20). Examiner.removeAvailability was replaced by ScheduleManager.removeAvailability, which already existed in the Examiner Scheduling model. Applicant.viewAvailableSlots was replaced by BookingManager.searchAvailableSlots. ResultManager.downloadCertificate was replaced by Certificate.getDocument.
- **Methods omitted from the final diagram.** To keep the final diagram readable on a single page, helper and query methods that no sequence diagram uses were omitted: User.validateRegistration, PasswordResetToken.isExpired (covered by isValid), AuditLog.getByUser and getByRecord, Applicant.viewMyBookings, Examiner.viewMyAvailability, Availability.isValid, ScheduleManager.getAvailability, hasConflict and getUnassignedBookings, TestResult.getSummary and Certificate.isValid. They remain in the individual diagrams.

## 3. Modified Elements

- **Applicant.updateRecordStatus.** This method had package visibility (~) in the Users and Security model, but ResultManager must invoke it after a result is recorded. Its visibility was changed to public.
- **User login helpers.** incrementFailedLogins, lockAccount and resetFailedLogins remain private, because only login() uses them. They are shown in the final diagram because the UC-01 sequence diagram calls them.
- **RecordStatus value.** RETEST REQUIRED was renamed RETEST_REQUIRED, because an enumeration literal cannot contain a space.
- **BookingManager names.** These were aligned with the other models: validateBookingCutoff was renamed validateCutoff; checkBookingConflict(applicantID: int, slot) became checkBookingConflict(applicant: Applicant, slot); and rescheduleBooking now returns Booking instead of boolean, to match Applicant.rescheduleBooking.
- **Booking names.** bookingID was renamed bookingId, referenceNumber bookingRef, and bookingDate createdAt. status changed from String to BookingStatus. The methods confirmBooking, cancelBooking, updateSlot and getBookingDetails were renamed confirm, cancel, reschedule and getDetails.
- **TestSlot names.** slotID was renamed slotId and testDate date. reserveSlot and releaseSlot were renamed reserve and release.
- **filterBookings.** Moved from Administrator to BookingManager, so that all booking queries sit in one controller. Its parameters changed from (date, status, applicant, examiner) to (date, location, assignmentStatus), to match FR21 (filter by date, location or examiner-assignment status).
- **Notification description.** The class inventory stated that Notification covers only examiner assignment and revocation notices. The description was extended to all six notification types, since NotificationType and NotificationService already support booking and result notices.
- **Responsibilities of user classes.** The methods of Applicant, Examiner and Administrator overlapped with those of BookingManager, ScheduleManager and ResultManager. The user class methods were retained as entry points; the business rules are implemented in the manager classes.
- **Association direction.** The association between ExaminerAssignment and Booking was named "is covered by" but read backwards in one diagram. The name was retained and oriented from Booking to ExaminerAssignment.
- **Association name.** The Notification-to-User association "sent to" was renamed "receives" and oriented from User to Notification, to match the other User associations ("has", "requests", "performs").

## 4. Added Elements

- **BookingStatus enumeration** (CONFIRMED, CANCELLED, RESCHEDULED, COMPLETED). Booking used it, but it was only drawn in one individual diagram.
- **ActionType values.** BOOKING_RESCHEDULED, AVAILABILITY_REMOVED and EXAMINER_REASSIGNED were added, because the manager classes log these actions and NFR17 requires an audit record for every such action. NOTIFICATION_FAILED was added because a notification that still fails after 3 retries is written to the audit log (FR27).
- **Booking.testType.** Added because requestBooking and createBooking both accept a test type, so Booking needs an attribute to store it.
- **BookingManager.getBookingDetails(booking).** Added so that administrators can view a booking's applicant, examiner, date, time, location and status (UC-05).
- **ScheduleManager.getAvailableExaminers(slot).** Added to support View Examiner Availability (UC-20) when assigning an examiner.
- **NotificationService.alertNotificationFailure(notification).** Added for FR27: a notification that still fails after 3 retries is logged and the administrator is alerted.
- **Manager dependencies.** Dependencies were added from BookingManager, ScheduleManager and ResultManager to AuditLog; from ResultManager to Booking and Applicant; and from ScheduleManager to Booking and Examiner. These cover every interaction shown in the sequence diagrams.
- **UML notes.** Notes were added for the main constraints: account lockout, one active booking per slot, one ACTIVE assignment per booking, certificates only for PASS results, the append-only audit log, and the notification retry rule.

## 5. Design Decisions

- **Booking to TestSlot (0..* to 1).** A slot can be reused after a booking is cancelled, so many bookings may reference one slot over time, but only one non-cancelled booking may hold it at any moment. This is stated in a note.
- **Booking to ExaminerAssignment (1 to 0..*).** Revoked assignments are kept as history, so a booking may have several assignments, of which at most one is ACTIVE.
- **Inheritance.** Inheritance is used only for User, with Applicant, Examiner and Administrator as subclasses, because this is the only genuine generalization in the system.
