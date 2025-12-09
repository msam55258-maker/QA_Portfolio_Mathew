🐞 BUG 1 – Login button enabled on blank fields

Bug ID: BUG_HMS_01
Module: Login
Bug Summary: Login button remains enabled when username and password are blank
Environment: QA Server, Chrome latest, Windows 10
Preconditions: User is on the Login page

Steps to Reproduce:
	1.	Open the HMS login page.
	2.	Keep the Username field empty.
	3.	Keep the Password field empty.
	4.	Observe the Login button state.

Expected Result:
Login button should be disabled or system should show “Username and Password are required” and not send request.

Actual Result:
Login button is enabled and allows login attempt with empty fields.

Severity: Medium
Priority: High
Status: Open
Reported By: Mathew
Reported Date: dd-mm-yyyy
Comments: Could lead to unnecessary backend calls and security/logging issues.

⸻

🐞 BUG 2 – Invalid mobile accepted in registration

Bug ID: BUG_HMS_02
Module: Patient Registration
Bug Summary: Mobile number field accepts alphabets and saves record
Environment: QA Server, Chrome latest

Preconditions: User is logged in and on Patient Registration page.

Steps to Reproduce:
	1.	Enter valid Name, Age, Gender.
	2.	In Mobile Number field, enter 98AB543210.
	3.	Fill other mandatory fields.
	4.	Click Save.

Expected Result:
System should restrict non-numeric data and show validation: “Enter valid mobile number”.

Actual Result:
Patient record is created successfully with invalid mobile number.

Severity: High
Priority: High
Status: Open
Reported By: Mathew
Reported Date: dd-mm-yyyy
Comments: Impacts contactability of patients; data quality issue.

⸻

🐞 BUG 3 – Double booking allowed for same doctor and time

Bug ID: BUG_HMS_03
Module: Appointment Booking
Bug Summary: System allows double booking for same doctor and time slot
Environment: QA Server, Chrome

Preconditions:
	•	Doctor “Dr. John” has an appointment already booked from 10:00–10:30 AM for today.
	•	User is on Appointment Booking page.

Steps to Reproduce:
	1.	Select doctor Dr. John.
	2.	Select the same date and time slot 10:00–10:30 AM.
	3.	Select any patient.
	4.	Click Book Appointment.

Expected Result:
System should block booking and show message like “This time slot is already booked”.

Actual Result:
Second appointment is created successfully for the same doctor and time.

Severity: Critical
Priority: High
Status: Open
Reported By: Mathew
Reported Date: dd-mm-yyyy
Comments: Serious scheduling issue; can cause real-world conflicts in hospital.

⸻

🐞 BUG 4 – Past date appointment allowed

Bug ID: BUG_HMS_04
Module: Appointment Booking
Bug Summary: Application allows booking appointments in the past
Environment: QA Server, Chrome

Preconditions: User is logged in and on Appointment Booking page.

Steps to Reproduce:
	1.	Select any patient and doctor.
	2.	From date picker, choose a date before today.
	3.	Select any time slot.
	4.	Click Book Appointment.

Expected Result:
System should not allow past dates and show “Cannot book appointment for a past date”.

Actual Result:
Appointment is saved successfully with past date.

Severity: Major
Priority: Medium
Status: Open
Reported By: Mathew
Reported Date: dd-mm-yyyy
Comments: Business rule violation; may break reporting and analytics.

⸻

🐞 BUG 5 – Incorrect discount calculation in billing

Bug ID: BUG_HMS_05
Module: Billing
Bug Summary: 10% discount applied incorrectly on total bill amount
Environment: QA Server, Chrome

Preconditions:
	•	Patient bill exists with total amount = ₹10,000.
	•	Discount feature enabled.

Steps to Reproduce:
	1.	Open Billing screen for the patient.
	2.	Enter discount as 10%.
	3.	Click Apply Discount.

Expected Result:
Final amount should be ₹9,000 (10% of ₹10,000 = ₹1,000).

Actual Result:
Final amount shows ₹9,500 (discount applied as 5% instead of 10%).

Severity: Major
Priority: High
Status: Open
Reported By: Mathew
Reported Date: dd-mm-yyyy
Comments: Direct financial impact; needs urgent fix.

⸻

🐞 BUG 6 – Payment success shown even when payment fails

Bug ID: BUG_HMS_06
Module: Billing / Payment
Bug Summary: System displays “Payment successful” even when payment gateway returns failure
Environment: QA Server, Chrome, Test Payment Gateway

Preconditions: Payment gateway configured to simulate failure response.

Steps to Reproduce:
	1.	Open a bill ready for payment.
	2.	Choose Card payment option.
	3.	Enter test card details that simulate failed transaction.
	4.	Click Pay.

Expected Result:
System should show “Payment failed, please try again” and bill status should stay Unpaid.

Actual Result:
System shows “Payment successful” and updates bill status to Paid.

Severity: Critical
Priority: High
Status: Open
Reported By: Mathew
Reported Date: dd-mm-yyyy
Comments: Critical financial and audit issue.

⸻

🐞 BUG 7 – Dashboard appointment count mismatch

Bug ID: BUG_HMS_07
Module: Dashboard
Bug Summary: Today’s appointment count on dashboard not matching appointment list
Environment: QA Server, Chrome

Preconditions:
	•	7 appointments exist for today in Appointment List.

Steps to Reproduce:
	1.	Log in as Admin.
	2.	Go to Dashboard.
	3.	Note “Today’s Appointments” count.
	4.	Go to Appointment List and filter by today’s date.

Expected Result:
Dashboard count should match filtered appointment list (7).

Actual Result:
Dashboard shows 5 appointments, while list shows 7.

Severity: Medium
Priority: Low
Status: Open
Reported By: Mathew
Reported Date: dd-mm-yyyy
Comments: Reporting inconsistency; impacts analytics and management view.

⸻

🐞 BUG 8 – Unauthorized access to admin screen

Bug ID: BUG_HMS_08
Module: User Management / Access Control
Bug Summary: Receptionist role can access Admin-only “User Management” screen via URL
Environment: QA Server, Chrome

Preconditions:
	•	User with role Receptionist is logged in.

Steps to Reproduce:
	1.	Log in as Receptionist.
	2.	Directly enter the URL of Admin’s User Management page (e.g., /admin/users).

Expected Result:
Access should be denied with “Unauthorized access” or redirect to home.

Actual Result:
Receptionist can view and edit user accounts.

Severity: Critical
Priority: High
Status: Open
Reported By: Mathew
Reported Date: dd-mm-yyyy
Comments: Major security & permission flaw.

⸻

🐞 BUG 9 – Slow response time on login

Bug ID: BUG_HMS_09
Module: Login / Performance
Bug Summary: Login response takes more than 10 seconds under normal load
Environment: QA Server, Chrome, normal network

Preconditions: Application up and running.

Steps to Reproduce:
	1.	Open Login page.
	2.	Enter valid credentials.
	3.	Click Login.
	4.	Measure time until Dashboard appears.

Expected Result:
Dashboard should load within 3 seconds.

Actual Result:
Dashboard takes 12–15 seconds to load.

Severity: Medium
Priority: Medium
Status: Open
Reported By: Mathew
Reported Date: dd-mm-yyyy
Comments: Performance issue; may affect user satisfaction.

⸻

🐞 BUG 10 – Error message not cleared after successful action

Bug ID: BUG_HMS_10
Module: Patient Registration
Bug Summary: Previous validation error message remains visible after successful form submission
Environment: QA Server, Chrome

Preconditions: User on Patient Registration page.

Steps to Reproduce:
	1.	Try to save form with blank Name → see “Name is required” message.
	2.	Now enter valid Name and all fields.
	3.	Click Save again.

Expected Result:
Patient should be saved and previous error message should disappear.

Actual Result:
Patient is saved, but “Name is required” error message still shown on screen.

Severity: Low
Priority: Low
Status: Open
Reported By: Mathew
Reported Date: dd-mm-yyyy
Comments: UI issue; may confuse users.
