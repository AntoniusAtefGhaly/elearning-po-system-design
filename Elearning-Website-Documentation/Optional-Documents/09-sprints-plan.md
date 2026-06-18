# E-Learning Website - Sprints Plan

## 1. Purpose

This document organizes the module-ordered user stories and backlog into simple Agile sprints.

## 2. Sprint Goal

Build a working Arabic e-learning MVP where students can buy teacher courses using prepaid balance, watch lessons, solve assessments/quizzes, view grades, and track progress.

## 3. MVP Sprint Scope

The MVP includes:

- Identity and role-based access
- Teacher onboarding and approval
- Student profile, enrolled courses, and progress
- Course creation, course structure, lessons, and course approval
- Prepaid code and student balance enablers
- Paid course enrollment and access control
- Video lessons and no-download control
- Assessment and grading flow
- Parent progress and grade view
- Basic reports

## 4. Suggested Sprint Plan

| Sprint | Focus | Main Story References |
| --- | --- | --- |
| Sprint 1 | Identity & Access | US-IM-01, US-IM-02, US-IM-03, US-IM-04 |
| Sprint 2 | Teacher Management | US-TM-01, US-TM-02, US-TM-03, US-TM-04, US-TM-06, US-TM-07 |
| Sprint 3 | Student Management | US-SM-01, US-SM-02, US-SM-03, US-SM-04, US-SM-05 |
| Sprint 4 | Content & Course Management | US-CM-01, US-CM-02, US-CM-03, US-CM-04, US-CM-05, US-CM-06 |
| Sprint 5 | Payment Enablers & Enrollment | Module 08 prepaid stories to add, US-EM-01, US-EM-02, US-EM-03, US-EM-04 |
| Sprint 6 | Learning Progress | US-CM-07, US-CM-08, US-EM-05, US-EM-06, US-EM-07 |
| Sprint 7 | Assessment Management | US-AM-01, US-AM-02, US-AM-03, US-AM-04, US-AM-05, US-AM-06, US-AM-07 |
| Sprint 8 | Grading Management | US-GM-01, US-GM-02, US-GM-03, US-GM-04, US-GM-05, US-GM-06, US-GM-07, US-GM-08 |
| Sprint 9 | Reports, Testing, Release | Module 11 basic reports stories to add, bug fixing, final testing, MVP release preparation |

## 5. Main Dependencies

| Feature | Depends On |
| --- | --- |
| Teacher course creation | Teacher approval and verified subjects |
| Course publishing | Course draft, course structure, uploaded learning material, and admin approval |
| Course catalog | Published courses |
| Course purchase | Prepaid code redemption and student balance |
| Lesson viewing | Active enrollment |
| Progress tracking | Lesson viewing and assessment/quiz activity |
| Assessment submission | Active enrollment and published assessment |
| Result viewing | Grading completion and result publication |
| Parent progress/grade view | Parent account and linked student |
| Reports | Users, courses, codes, enrollments, progress, assessments, and grades |

## 6. MVP Exit Criteria

The MVP is ready when:

- Students, parents, teachers, and admins can register or log in according to role.
- Admin can approve, reject, and manage teacher status.
- Teachers can create courses for verified subjects.
- Teachers can build course structure and upload lesson materials.
- Admin can approve and publish courses.
- Students can browse published courses.
- Admin can generate prepaid codes and manage student balance.
- Student or parent can redeem a prepaid code for one student.
- Student can buy a course using balance.
- Duplicate enrollment is prevented.
- Student can access only enrolled course content.
- Video is not directly downloadable.
- Lesson progress works manually and automatically after 90% video watching.
- Student can solve assessments/quizzes and retry quizzes.
- Objective grading and result generation work.
- Teachers can publish results.
- Students and parents can view published results.
- Parents can view linked student progress.
- Admin and teachers can view basic reports.

## 7. Later Sprints / Releases

Later sprints or releases may include:

- Attendance tracking: US-SM-06
- Student/course notifications: US-SM-07
- Course archive/delete/restore lifecycle: US-CM-09
- Free course enrollment: US-CM-10
- Advanced refund workflow: US-EM-08
- Assessment notifications: US-AM-08
- Result notifications: US-GM-09
- Direct online payment gateway
- Subscriptions and invoices
- Mobile app
- Live classes
- Chat/community
- Certificates
- Subject bundles
- English interface
- Video watermarking
