# E-Learning Website - Business Requirements

## 1. Purpose

This document lists the main business requirements for the e-learning website MVP.

It explains what the business needs the system to support, without going into detailed technical design.

## 2. Product Scope

The MVP is an Arabic-first e-learning website for Egyptian secondary school students, parents, teachers, education centers, and admins.

The platform supports Secondary 1, Secondary 2, and Secondary 3.

## 3. Business Requirements

| ID | Requirement |
| --- | --- |
| BR-01 | The system must allow students to register and access their learning account. |
| BR-02 | The system must allow parents to register and link to student accounts. |
| BR-03 | The system must allow teachers to create and manage course content. |
| BR-04 | The system must allow education centers to manage their teachers and courses. |
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
| R-08 | A used, expired, or cancelled code cannot be reused. |
| R-09 | A parent can be linked to one or more students. |
| R-10 | A student can enroll in many courses. |

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

## 6. Open Questions

1. Does a prepaid code add wallet balance or unlock a specific course?
2. Can a student redeem codes, or only parents?
3. Can one teacher belong to more than one education center?
4. What happens if a student requests a refund?

## 7. Next Document

The next document should be the Functional Requirements / SRS. It will explain what each system module must do in more detail.

