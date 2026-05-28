# E-Learning Website - Test Scenarios

## 1. Purpose

This document lists simple MVP test scenarios to confirm that the main product flows work.

## 2. Student Scenarios

| ID | Scenario | Expected Result |
| --- | --- | --- |
| TS-01 | Student registers with valid data | Student account is created |
| TS-02 | Student logs in with valid credentials | Student enters the platform |
| TS-03 | Student browses courses | Published courses are displayed |
| TS-04 | Student filters courses | Courses are filtered by year, subject, term, chapter, or teacher |
| TS-05 | Student redeems valid prepaid code | Code value is added to student balance |
| TS-06 | Student redeems used or cancelled code | System rejects the code |
| TS-07 | Student buys course with enough balance | Course is added to student enrollments |
| TS-08 | Student buys course without enough balance | System prevents purchase |
| TS-09 | Student watches enrolled lesson | Video plays successfully |
| TS-10 | Student tries to watch unenrolled lesson | Access is denied |
| TS-11 | Student completes lesson manually | Progress is updated |
| TS-12 | Student watches 90% of video | Lesson is completed automatically |
| TS-13 | Student solves MCQ quiz | Score is displayed |
| TS-14 | Student tries to retry quiz | Retry is not allowed |

## 3. Parent Scenarios

| ID | Scenario | Expected Result |
| --- | --- | --- |
| TS-15 | Parent registers and logs in | Parent account is created and accessible |
| TS-16 | Parent links student using student ID | Student appears in parent account |
| TS-17 | Parent redeems code for linked student | Value is added to that student's balance |
| TS-18 | Parent views student progress | Linked student's progress is displayed |
| TS-19 | Parent tries to view unlinked student | Access is denied |

## 4. Teacher Scenarios

| ID | Scenario | Expected Result |
| --- | --- | --- |
| TS-20 | Teacher submits approval data | Teacher account becomes pending approval |
| TS-21 | Approved teacher creates course | Course is saved as draft |
| TS-22 | Teacher adds lessons | Lessons are added to the course |
| TS-23 | Teacher adds MCQ quiz | Quiz is added to the course |
| TS-24 | Teacher submits course for approval | Course status becomes pending approval |
| TS-25 | Teacher views own course progress | Own students' progress is displayed |
| TS-26 | Teacher tries to view another teacher's course data | Access is denied |

## 5. Education Center Scenarios

| ID | Scenario | Expected Result |
| --- | --- | --- |
| TS-27 | Education center creates teacher account | Teacher is created under the center |
| TS-28 | Education center views center courses | Center courses are displayed |
| TS-29 | Education center views center reports | Center-related reports are displayed |

## 6. Admin Scenarios

| ID | Scenario | Expected Result |
| --- | --- | --- |
| TS-30 | Admin approves teacher | Teacher can create/submit courses |
| TS-31 | Admin rejects teacher | Teacher cannot publish courses |
| TS-32 | Admin approves course | Course appears in catalog |
| TS-33 | Admin rejects course | Course stays hidden from students |
| TS-34 | Admin generates prepaid code | Code is created with value and serial number |
| TS-35 | Admin cancels active code | Code cannot be redeemed |
| TS-36 | Admin manually adjusts balance | Student balance is updated |
| TS-37 | Admin resets balance for refund | Student balance becomes 0 |
| TS-38 | Admin views code report | Code report is displayed |
| TS-39 | Admin views enrollment report | Enrollment report is displayed |
| TS-40 | Admin views teacher sales report | Teacher sales report is displayed |
| TS-41 | Admin views student progress report | Student progress report is displayed |

## 7. Non-Functional Scenarios

| ID | Scenario | Expected Result |
| --- | --- | --- |
| TS-42 | User opens website on mobile browser | Website is usable on mobile |
| TS-43 | User opens website in Arabic | Arabic layout and content display correctly |
| TS-44 | User tries to access page without permission | System blocks access |
| TS-45 | Student tries to directly download video | Direct download is not available |

