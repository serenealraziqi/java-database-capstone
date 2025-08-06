# User Stories

## Admin User Stories

**Title:**  
_As an Admin, I want to create, edit, and deactivate user accounts, so that I can manage system access securely._  
**Acceptance Criteria:**  
1. Admin can add new users with appropriate roles.  
2. Admin can modify user details, including roles and status.  
3. Admin can deactivate users to restrict system access.  
**Priority:** High  
**Story Points:** 5  
**Notes:**  
- Ensure that user actions are logged for audit purposes.  

**Title:**  
_As an Admin, I want to assign roles to users (Doctor, Patient), so that permissions and access are properly managed._  
**Acceptance Criteria:**  
1. Admin can assign one or multiple roles during user creation.  
2. Role changes can be modified later by Admin.  
3. System enforces role-based access control based on assigned roles.  
**Priority:** High  
**Story Points:** 3  
**Notes:**  
- Ensure role changes trigger permission refresh across modules.

## Doctor User Stories

**Title:**  
_As a Doctor, I want to view my upcoming appointments, so that I can prepare for patient consultations._  
**Acceptance Criteria:**  
1. Doctor sees list of upcoming appointments sorted by date and time.  
2. Appointment details include patient info and reason for visit.  
3. Doctor can filter or search appointments by date.  
**Priority:** High  
**Story Points:** 5  
**Notes:**  
- Notifications for new or changed appointments may be included later.

**Title:**  
_As a Doctor, I want to manage my availability calendar, so that patients can book only during my free times._  
**Acceptance Criteria:**  
1. Doctor can mark time slots as available or unavailable.  
2. Calendar changes immediately affect booking availability.  
3. Doctor can view booked vs free slots.  
**Priority:** Medium  
**Story Points:** 8  
**Notes:**  
- Integrate with patient booking system for real-time updates.

## Patient User Stories

**Title:**  
_As a Patient, I want to register and create a personal profile, so that I can access healthcare services._  
**Acceptance Criteria:**  
1. Patient can register with valid email and password.  
2. Profile includes personal and health information.  
3. Patient receives confirmation email after registration.  
**Priority:** High  
**Story Points:** 3  
**Notes:**  
- Consider email verification for security.

**Title:**  
_As a Patient, I want to search for and find doctors by specialty or name, so that I can select an appropriate healthcare provider._  
**Acceptance Criteria:**  
1. Patient can enter search terms for specialty or doctor name.  
2. Matching doctors are displayed with profiles and availability.  
3. Search results are paginated or filtered by relevance.  
**Priority:** High  
**Story Points:** 5  
**Notes:**  
- Include filters for location, ratings, or availability if possible.

**Title:**  
_As a Patient, I want to book, reschedule, and cancel appointments, so that I can manage my healthcare schedule conveniently._  
**Acceptance Criteria:**  
1. Patient can view doctor availability calendar for booking.  
2. Patient can reschedule or cancel existing appointments easily.  
3. Appointment status updates are reflected immediately.  
**Priority:** High  
**Story Points:** 8  
**Notes:**  
- Send notifications for appointment confirmations or changes.

