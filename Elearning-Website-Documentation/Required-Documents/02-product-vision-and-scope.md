# E-Learning Website - Product Vision and Scope

## 1. Purpose

This document defines the product vision and MVP scope.

## 2. Product Vision

Create an Arabic-first e-learning website for Egyptian secondary school students where students can buy teacher courses using prepaid codes, watch lessons, solve simple quizzes, and track progress.

## 3. MVP Users

| User | Main Need |
| --- | --- |
| Student | Study online and track progress |
| Parent | Pay/redeem codes and view progress |
| Teacher | Publish and manage courses |
| Admin | Manage approvals, codes, users, and reports |

## 4. MVP Scope

The first release supports:

- Secondary 1, Secondary 2, and Secondary 3
- All core subjects
- Arabic interface
- Official Egyptian curriculum structure
- Private teachers
- Prepaid code payment
- Separate purchase for each teacher course
- No direct video download

## 5. Main Features

### Student

- Register and log in
- Browse courses
- Redeem prepaid code
- Enroll in a course
- Watch lessons
- Solve basic MCQ quizzes
- View progress

### Parent

- Register and log in
- Link to student
- Redeem prepaid code
- View student progress

### Teacher

- Manage profile
- Create courses
- Add lessons and quizzes
- Submit courses for approval
- View enrolled students and progress

### Admin

- Manage users
- Approve teachers and courses
- Manage curriculum data
- Generate prepaid codes
- View basic reports
- Manually adjust student balance

## 6. Out of Scope

- Mobile app
- Live classes
- Chat or forum
- Certificates
- English interface
- Subject bundles
- Direct online payment gateway
- Advanced video watermarking
- Parent-student link approval workflow

## 7. Main Business Rules

| ID | Rule |
| --- | --- |
| R-01 | Courses must follow year, subject, term, and chapter. |
| R-02 | Courses are hidden until admin approval. |
| R-03 | Payment is done using prepaid codes. |
| R-04 | Students buy teacher courses separately. |
| R-05 | Parents can view linked student progress. |
| R-06 | Videos must not be directly downloadable. |
| R-07 | Students can register without parent approval. |
| R-08 | Teachers are individual users in MVP. |
| R-09 | Each prepaid code can be redeemed for one student only. |
| R-10 | Redeemed code value is added to the student's balance. |
| R-11 | Prepaid codes are distributed manually in the MVP. |
| R-12 | Refunds are handled manually; admin resets student balance to 0 and money is returned outside the system. |
| R-13 | Lesson completion can be manual or automatic. |
| R-14 | MVP quizzes use MCQ questions only. |
| R-15 | Student balance can be used partially across multiple courses. |
| R-16 | Student balance cannot become negative. |
| R-17 | Admin can manually add or subtract student balance. |
| R-18 | Refund is allowed only if the student has not used/bought a course. |
| R-19 | No refund is allowed after the student buys a course and watches lessons. |
| R-20 | Prepaid codes do not expire. |
| R-21 | Admin can cancel an active prepaid code. |
| R-22 | Prepaid codes have serial numbers for manual distribution tracking. |
| R-23 | Parent links to student using student ID. |
| R-24 | Teacher approval requires name, phone, subject, bio, profile image, and documents. |
| R-25 | Admin can create or approve teacher accounts. |
| R-26 | Teacher sets course price. |
| R-27 | Admin can edit teacher course prices. |
| R-28 | Automatic lesson completion happens after watching 90% of the video. |
| R-29 | Quiz score is shown to student. |
| R-30 | Quiz retry is not allowed in MVP. |
| R-31 | Quiz result affects course progress. |
| R-32 | MVP reports include codes, enrollments, teacher sales, and student progress. |

## 8. Success for This Training Project

The documentation is successful if a software team can understand the MVP scope, users, features, and business rules.
