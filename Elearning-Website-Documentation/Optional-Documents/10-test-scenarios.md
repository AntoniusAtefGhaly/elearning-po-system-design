# E-Learning Website - Test Scenarios

## 1. Purpose

This document lists simple MVP test scenarios mapped to the module-ordered user stories in document 06.

## 2. Identity & Access Management

| ID | Story Reference | Scenario | Expected Result |
| --- | --- | --- | --- |
| TS-01 | US-IM-01 | Student registers with valid data | Student account is created |
| TS-02 | US-IM-01 | Student registers with duplicate phone/email | Registration is rejected |
| TS-03 | US-IM-02 | Parent registers and logs in | Parent account is created and accessible |
| TS-04 | US-IM-03 | Teacher submits account approval data | Teacher account becomes pending approval |
| TS-05 | US-IM-04 | Admin updates user status | User status is updated and action is auditable |

## 3. Teacher Management

| ID | Story Reference | Scenario | Expected Result |
| --- | --- | --- | --- |
| TS-06 | US-TM-01 | Teacher completes profile and uploads documents | Teacher profile is saved as pending approval |
| TS-07 | US-TM-03 | Admin approves teacher | Teacher can access teacher features |
| TS-08 | US-TM-04 | Admin rejects teacher with reason | Teacher is rejected and reason is saved |
| TS-09 | US-TM-05 | Admin suspends teacher | New course/enrollment actions are blocked |
| TS-10 | US-TM-06 | Teacher registers with duplicate National ID or phone | Registration is rejected |
| TS-11 | US-TM-07 | Teacher creates course for verified subject | Course draft can be created |

## 4. Student Management

| ID | Story Reference | Scenario | Expected Result |
| --- | --- | --- | --- |
| TS-12 | US-SM-01 | Student updates allowed profile fields | Profile is updated |
| TS-13 | US-SM-02 | Student opens enrolled courses dashboard | Enrolled courses are displayed |
| TS-14 | US-SM-03 | Student watches 90% of video | Progress updates automatically |
| TS-15 | US-SM-04 | Parent views linked student progress | Linked student's progress is displayed |
| TS-16 | US-SM-04 | Parent tries to view unlinked student | Access is denied |
| TS-17 | US-SM-05 | Admin deactivates student account | Student account status is updated |

## 5. Content & Course Management

| ID | Story Reference | Scenario | Expected Result |
| --- | --- | --- | --- |
| TS-18 | US-CM-01 | Teacher creates course draft | Course is saved as draft |
| TS-19 | US-CM-02 | Teacher organizes subjects, modules, and lessons | Course structure is saved correctly |
| TS-20 | US-CM-03 | Teacher uploads video or document | Material is linked to lesson |
| TS-21 | US-CM-04 | Teacher submits course for review | Course status becomes pending approval |
| TS-22 | US-CM-05 | Admin publishes approved course | Course appears in catalog |
| TS-23 | US-CM-06 | Student browses published courses | Published courses are displayed |
| TS-24 | US-CM-07 | Student opens enrolled course content | Content is accessible |
| TS-25 | US-CM-07 | Student opens unenrolled course content | Access is denied |
| TS-26 | US-CM-08 | Student solves lesson quiz | Score is displayed |
| TS-27 | US-CM-08 | Student retries quiz | A new attempt is recorded |

## 6. Payment Enablers

| ID | Story Reference | Scenario | Expected Result |
| --- | --- | --- | --- |
| TS-28 | Module 08 story to add | Admin generates prepaid code | Code is created with value and serial number |
| TS-29 | Module 08 story to add | Admin cancels active code | Code cannot be redeemed |
| TS-30 | Module 08 story to add | Student redeems valid prepaid code | Code value is added to student balance |
| TS-31 | Module 08 story to add | Student redeems used or cancelled code | System rejects the code |
| TS-32 | Module 08 story to add | Admin manually adjusts balance | Student balance is updated |

## 7. Enrollment Management

| ID | Story Reference | Scenario | Expected Result |
| --- | --- | --- | --- |
| TS-33 | US-EM-01 | Student buys course with enough balance | Enrollment becomes active |
| TS-34 | US-EM-01 | Student buys course without enough balance | Purchase is blocked |
| TS-35 | US-EM-02 | Student tries to enroll twice | Duplicate enrollment is blocked |
| TS-36 | US-EM-03 | Student watches enrolled lesson | Video plays successfully |
| TS-37 | US-EM-03 | Student tries to watch unenrolled lesson | Access is denied |
| TS-38 | US-EM-04 | Teacher views own enrolled students | Own students are displayed |
| TS-39 | US-EM-05 | Teacher is suspended after enrollments exist | Existing students keep access |
| TS-40 | US-EM-06 | Student completes course requirements | Enrollment becomes completed |
| TS-41 | US-EM-07 | Admin resets balance for manual refund | Student balance becomes 0 and action is logged |

## 8. Assessment Management

| ID | Story Reference | Scenario | Expected Result |
| --- | --- | --- | --- |
| TS-42 | US-AM-01 | Teacher creates exam | Exam is saved |
| TS-43 | US-AM-02 | Teacher creates quiz | Quiz is saved and linked |
| TS-44 | US-AM-03 | Teacher adds questions | Questions are linked to assessment |
| TS-45 | US-AM-04 | Teacher publishes assessment | Enrolled students can access it |
| TS-46 | US-AM-05 | Student submits assessment answers | Attempt is recorded |
| TS-47 | US-AM-06 | Teacher reviews submission | Grade or feedback can be added |
| TS-48 | US-AM-07 | Parent views linked student result | Result is displayed read-only |

## 9. Grading Management

| ID | Story Reference | Scenario | Expected Result |
| --- | --- | --- | --- |
| TS-49 | US-GM-01 | System grades objective questions | Score is calculated automatically |
| TS-50 | US-GM-02 | Teacher grades essay answer | Manual score is saved |
| TS-51 | US-GM-03 | System generates result after grading | Draft result is created |
| TS-52 | US-GM-04 | Teacher publishes result | Student can view result |
| TS-53 | US-GM-05 | Teacher modifies result with reason | Change is saved and logged |
| TS-54 | US-GM-06 | Student views own published result | Result is displayed |
| TS-55 | US-GM-07 | Parent views linked student grades | Grades are displayed read-only |
| TS-56 | US-GM-08 | Admin views grading audit | Audit information is displayed |

## 10. Non-Functional Scenarios

| ID | Scenario | Expected Result |
| --- | --- | --- |
| TS-57 | User opens website on mobile browser | Website is usable on mobile |
| TS-58 | User opens website in Arabic | Arabic layout and content display correctly |
| TS-59 | User tries to access page without permission | System blocks access |
| TS-60 | Student tries to directly download video | Direct download is not available |
