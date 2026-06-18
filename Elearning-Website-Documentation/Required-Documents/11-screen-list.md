# E-Learning Website - Screen List

## 1. Purpose

This document lists the main MVP screens and maps them to the module-ordered user stories in document 06.

It helps UI/UX and frontend teams understand what pages should exist.

## 2. Public and Identity Screens

| Screen | User | Related Stories | Purpose | Main Actions |
| --- | --- | --- | --- | --- |
| Home Page | Guest | US-CM-06 | Introduce platform and show course entry points | View courses, register, log in |
| Login | All users | US-IM-01, US-IM-02 | Access account | Enter credentials |
| Student Register | Student | US-IM-01 | Create student account | Submit registration form |
| Parent Register | Parent | US-IM-02 | Create parent account | Submit registration form |
| Course Catalog | Guest/Student/Parent | US-CM-06 | Browse available courses | Search, filter, open course |
| Course Details | Guest/Student/Parent | US-CM-06, US-EM-01 | View course information | View price, teacher, lessons, enroll |

## 3. Student Management Screens

| Screen | Related Stories | Purpose | Main Actions |
| --- | --- | --- | --- |
| Student Dashboard | US-SM-02, US-SM-03 | Show student learning summary | View enrolled courses, balance, progress |
| Student Profile | US-SM-01 | Manage student profile | Update allowed profile data |
| My Courses | US-SM-02, US-EM-01 | Show enrolled courses | Open course |
| Progress Page | US-SM-03 | View learning progress | View completed lessons and assessment progress |

## 4. Payment and Enrollment Screens

| Screen | Related Stories | Purpose | Main Actions |
| --- | --- | --- | --- |
| Redeem Code | Module 08 story to add | Add value to student balance | Enter prepaid code |
| Course Purchase | US-EM-01, US-EM-02 | Buy course using balance | Confirm purchase |
| Lesson Player | US-CM-07, US-EM-03 | Watch course lessons | Play video, mark lesson complete |

## 5. Assessment and Grading Screens

| Screen | Related Stories | Purpose | Main Actions |
| --- | --- | --- | --- |
| Assessment Page | US-AM-05, US-CM-08 | Solve assessment/quiz | Select answers, submit, view score |
| Student Results | US-GM-06 | View published results | View score, percentage, pass/fail status |

## 6. Parent Screens

| Screen | Related Stories | Purpose | Main Actions |
| --- | --- | --- | --- |
| Parent Dashboard | US-SM-04 | Show linked students | View students and progress |
| Link Student | US-SM-04 | Connect parent to student | Enter student ID |
| Parent Redeem Code | Module 08 story to add | Add value to linked student balance | Select student, enter code |
| Student Progress View | US-SM-04 | Monitor student learning | View courses, lessons, progress |
| Student Grades View | US-AM-07, US-GM-07 | Monitor academic performance | View assessment results and grades |

## 7. Teacher Screens

| Screen | Related Stories | Purpose | Main Actions |
| --- | --- | --- | --- |
| Teacher Dashboard | US-TM-01, US-EM-04 | Show teacher summary | View courses, enrollments, results |
| Teacher Profile | US-TM-01, US-TM-02 | Manage teacher information | Edit name, phone, subject, bio, image, documents |
| Course List | US-CM-01 | Manage teacher courses | View, create, edit courses |
| Course Editor | US-CM-01, US-CM-02, US-CM-03 | Create or edit course | Set course data, structure, lessons, materials |
| Course Review Submission | US-CM-04 | Submit course for approval | Submit complete course |
| Course Students | US-EM-04 | View enrolled students | View student progress |
| Assessment Management | US-AM-01, US-AM-02, US-AM-03, US-AM-04 | Manage assessments/quizzes | Create, add questions, publish |
| Submission Review | US-AM-06, US-GM-02 | Review and grade submissions | Add grades and feedback |
| Result Publishing | US-GM-03, US-GM-04, US-GM-05 | Manage results | Review, publish, modify with reason |

## 8. Admin Screens

| Screen | Related Stories | Purpose | Main Actions |
| --- | --- | --- | --- |
| Admin Dashboard | US-IM-04 | Show platform summary | View users, courses, codes, reports |
| User Management | US-IM-04, US-SM-05 | Manage users | View, update, deactivate users |
| Teacher Approval | US-IM-03, US-TM-03, US-TM-04, US-TM-05 | Approve teachers | Review teacher data, approve/reject/suspend |
| Course Approval | US-CM-05 | Approve courses | Review course, approve/reject |
| Curriculum Management | US-CM-01, US-CM-02 | Manage curriculum data | Add/edit years, subjects, terms, chapters |
| Prepaid Code Management | Module 08 story to add | Manage prepaid codes | Generate, cancel, track codes |
| Student Balance Management | Module 08 story to add, US-EM-07 | Manage balances | Add/subtract balance, reset for refund |
| Grading Audit | US-GM-08 | Monitor grading actions | View grading audit log |
| Reports | Module 11 story to add | View platform reports | View codes, enrollments, teacher sales, student progress |
| Settings | Future story | Manage basic platform settings | Update simple system settings |

## 9. Future Screens

| Screen | Related Stories | Reason |
| --- | --- | --- |
| Attendance Management | US-SM-06 | Future scope |
| Notifications Center | US-SM-07, US-AM-08, US-GM-09 | Future scope |
| Course Archive/Delete/Restore | US-CM-09 | Future scope |
| Free Course Enrollment | US-CM-10 | Future scope |
| Advanced Refund Requests | US-EM-08 | Future scope |

## 10. Notes

- These are MVP screens plus clearly marked future screens.
- Detailed wireframes can be created later from this list.
- Mobile app screens are not included in MVP.
