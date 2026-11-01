# Integration Notes

**Project:** Driving Test Booking and Results System (COE 420 Sec 02, Group 8)

This document records the significant changes made when the individual class models were consolidated into one team UML Class Diagram (`Class_Diagram/`).

## 1. Merged Duplicate Classes

| Class | Source of Duplication | Resolution |
|---|---|---|
| User | Full version in the Users and Security model; reduced versions (userId and name only) in Examiner Scheduling, Admin Oversight, Results and Notifications. | Full version retained because it contains authentication, lockout and password reset attributes. Reduced versions deleted. |
| Examiner | Individual models of Zainab, Areej and Aira. | Merged into one class with all attributes (examinerNumber, licenseCategories) and methods (availability, schedule, submitResult). |
| Administrator | Users and Security model and Admin Oversight model. | Merged. reassignExaminer was taken from the Admin Oversight model. |
| Applicant | Users and Security model and Results model. | Merged. viewMyResult and requestCertificate are listed once. |
| Booking | Examiner Scheduling, Admin Oversight, Results and Booking models. | Booking model version used as the base because it is the most complete. |
| TestSlot | Examiner Scheduling (name only) and Booking model. | Booking model version used. |
| ExaminerAssignment | Examiner Scheduling and Admin Oversight models. | Merged into a single definition. |
| ScheduleManager | Examiner Scheduling and Admin Oversight models. | Merged. assignExaminer and reassignExaminer added to the Examiner Scheduling method list. |
| NotificationType, BookingStatus, Outcome | Drawn in more than one individual diagram. | Each enumeration is now defined once. |

## 2. Removed Elements

- **Foreign key attributes.** Several classes held both an identifier attribute and an association to the same class, representing the same relationship twice. The identifier attributes were removed and the named association carries the link: Availability.examinerId, ExaminerAssignment.bookingId, ExaminerAssignment.examinerId, ExaminerAssignment.assignedByAdminId, TestResult.bookingId, TestResult.examinerId, Certificate.resultId, Notification.recipientId, Session.userId, PasswordResetToken.userId, AuditLog.performedBy and Booking.testSlot. Foreign keys remain necessary in the database schema, but they are an implementation detail and not part of the class model.
- **Reduced class copies.** The reduced copies of User, Examiner, Booking and TestSlot (Section 1) were deleted.
- **Methods omitted from the final diagram.** To keep the consolidated diagram readable, only the important methods are shown. Omitted: validateRegistration, the private login helpers (incrementFailedLogins, lockAccount, resetFailedLogins), viewMyBookings, viewMyAvailability, removeAvailability, getUnassignedBookings, hasConflict, and the notifyAssignmentRevoked, notifyBookingCancelled and notifyBookingRescheduled methods of NotificationService. Session.getUser, AuditLog.getByUser and getByRecord, and Availability helper methods in the individual diagrams are also omitted. The complete method lists are retained in the individual component diagrams.

## 3. Modified Elements

- **Applicant.updateRecordStatus.** Private in the Users and Security model, but it must be invoked after a result is recorded, so it was made public.
- **User login helpers.** incrementFailedLogins, lockAccount and resetFailedLogins were public but are only used inside login(), so they were made private.
- **RecordStatus value.** RETEST REQUIRED renamed RETEST_REQUIRED because an enumeration literal cannot contain a space.
- **Notification description.** The inventory said Notification covers only examiner assignment and revocation. It was extended to all six notification types.
- **Responsibilities of user classes.** Methods of Applicant, Examiner and Administrator overlapped with BookingManager, ScheduleManager and ResultManager. The user class methods were kept as entry points, and notes state that the business rules live in the manager classes.
- **Association direction.** The ExaminerAssignment and Booking association, named "is covered by", read backwards in one diagram. The name was kept and oriented from Booking to ExaminerAssignment.
- **Booking naming (Farah's model).** Attributes renamed for consistency: bookingID to bookingId, referenceNumber to bookingRef, bookingDate to createdAt, and status changed from String to the BookingStatus enumeration. cancellationDate was kept.
- **Booking methods.** confirmBooking, cancelBooking and getBookingDetails were shortened to confirm, cancel and getDetails. updateSlot became reschedule(newSlot). isActive and markCompleted were kept.
- **TestSlot naming (Farah's model).** testDate renamed date, and endTime added. isBooked, isAvailable(), reserveSlot() and releaseSlot() were kept, with the last two renamed reserve() and release().
- **BookingManager.** validateBookingCutoff renamed validateCutoff. checkBookingConflict, generateReferenceNumber, getUpcomingBooking and getBookingHistory were restored after an earlier draft of the consolidated diagram omitted them. The dependency "serves" from BookingManager to Applicant was restored.

## 4. Added Elements

- **BookingStatus enumeration** (CONFIRMED, CANCELLED, RESCHEDULED, COMPLETED), used by Booking but previously drawn in only one individual diagram.
- **ActionType values** BOOKING_RESCHEDULED, AVAILABILITY_REMOVED and EXAMINER_REASSIGNED, because the manager classes log these actions and NFR17 requires an audit record for every such action.
- **Booking.testType**, because requestBooking and createBooking both accept a test type.
- **Reserve and release behavior on TestSlot**, to reflect that a slot can be reserved once and released after cancellation or rescheduling.
- **UML notes** for the main constraints: account lockout, one active booking per slot, one ACTIVE assignment per booking, certificates only for PASS results, and the append-only audit log.

## 5. Design Decisions

- **Booking to TestSlot (0..* to 1).** A slot can be reused after a booking is cancelled, so many bookings may reference one slot over time, but only one non-cancelled booking may hold it at any moment (stated in a note).
- **Booking to ExaminerAssignment (1 to 0..*).** Revoked assignments are kept as history, so a booking may have several assignments, of which at most one is ACTIVE.
- **Inheritance.** Used only for User, with Applicant, Examiner and Administrator as subclasses, because this is the only genuine generalization in the system.
