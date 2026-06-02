# E-Learning Website - Business Requirements

## 1. Purpose

This document lists the main business requirements for the e-learning website MVP.

It explains what the business needs the system to support, without going into detailed technical design.

## 2. Product Scope

The MVP is an Arabic-first e-learning website for Egyptian secondary school students, parents, teachers, and admins.

The platform supports Secondary 1, Secondary 2, and Secondary 3.

## 3. Business Requirements

| ID | Requirement |
| --- | --- |
| BR-01 | The system must allow students to register and access their learning account. |
| BR-02 | The system must allow parents to register and link to student accounts. |
| BR-03 | The system must allow teachers to create and manage course content. |
| BR-05 | The system must organize courses by secondary year, subject, term, chapter, and teacher. |
| BR-06 | The system must allow students to browse and view course details. |
| BR-07 | The system must support paid access using prepaid codes. |
| BR-08 | Admin must be able to generate prepaid codes with fixed values, such as 50 EGP and 100 EGP. |
| BR-09 | Students must buy teacher courses separately. |
| BR-10 | The system must allow enrolled students to watch course lessons. |
| BR-11 | Videos must not be directly downloadable by students. |
| BR-12 | The system must track student progress. |
| BR-13 | Parents must be able to view payment information and student progress. |
| BR-14 | Teachers must be able to view enrolled students and course progress. |
| BR-15 | Admin must approve teachers and courses before they are published. |
| BR-16 | Admin must be able to view basic reports for users, courses, enrollments, and prepaid codes. |
| BR-17 | Admin must be able to manually adjust student balance. |

## 4. Business Rules

| ID | Rule |
| --- | --- |
| R-01 | The MVP language is Arabic only. |
| R-02 | English is planned for a later phase. |
| R-03 | Subject bundles are not included in MVP. |
| R-04 | Direct card or wallet payment is not included in MVP. |
| R-05 | Each course belongs to one main teacher. |
| R-06 | A course cannot be visible to students before admin approval. |
| R-07 | A prepaid code must have a value and status. |
| R-08 | A used or cancelled code cannot be reused. |
| R-09 | A parent can be linked to one or more students. |
| R-10 | A student can enroll in many courses. |
| R-11 | Students can register without parent approval. |
| R-12 | Teachers are individual users in MVP. |
| R-13 | Each prepaid code can be redeemed for one student only. |
| R-14 | Redeemed code value is added to the student's balance. |
| R-15 | Prepaid codes are distributed manually in the MVP. |
| R-16 | For refunds, admin resets student balance to 0 and the money is returned manually outside the system. |
| R-17 | Lesson completion can be manual or automatic. |
| R-18 | MVP quizzes use MCQ questions only. |
| R-19 | Student balance can be used partially across multiple courses. |
| R-20 | Student balance cannot become negative. |
| R-21 | Admin can manually add or subtract student balance. |
| R-22 | Refund is allowed only if the student has not used/bought a course. |
| R-23 | No refund is allowed after the student buys a course and watches lessons. |
| R-24 | Prepaid codes do not expire. |
| R-25 | Admin can cancel an active prepaid code. |
| R-26 | Prepaid codes have serial numbers for manual distribution tracking. |
| R-27 | Parent links to student using student ID. |
| R-28 | Teacher approval requires name, phone, subject, bio, profile image, and documents. |
| R-29 | Admin can create or approve teacher accounts. |
| R-30 | Teacher sets course price. |
| R-31 | Admin can edit teacher course prices. |
| R-32 | Automatic lesson completion happens after watching 90% of the video. |
| R-33 | Quiz score is shown to student. |
| R-34 | Quiz retry is not allowed in MVP. |
| R-35 | Quiz result affects course progress. |
| R-36 | MVP reports include codes, enrollments, teacher sales, and student progress. |

## 5. Out of Scope

The MVP does not include:

- Mobile app
- Live classes
- Chat or forums
- AI recommendations
- Certificates
- English interface
- Subject bundles
- Direct online payment gateway
- Advanced video protection such as watermarking
- Parent-student link approval workflow

## 6. Open Questions

No open business requirement questions for now.

## 7. Next Document

The next document should be the Functional Requirements / SRS. It will explain what each system module must do in more detail.
