# E-Learning Website - Functional Requirements / SRS

## 1. Purpose

This document describes the main system functions needed for the MVP.

## 2. System Modules

The MVP includes these modules:

1. User Account Management
2. Course Catalog
3. Course Management
4. Prepaid Code Management
5. Enrollment and Access
6. Learning and Progress
7. Parent View
8. Admin Management
9. Reports

## 3. Functional Requirements

### 3.1 User Account Management

| ID | Requirement |
| --- | --- |
| FR-01 | Users can log in and log out. |
| FR-02 | Students can create accounts. |
| FR-03 | Parents can create accounts. |
| FR-04 | Teachers and education centers can have accounts approved by admin. |
| FR-05 | Users can update basic profile information. |

### 3.2 Course Catalog

| ID | Requirement |
| --- | --- |
| FR-06 | Students can browse published courses. |
| FR-07 | Students can filter courses by secondary year, subject, term, chapter, and teacher. |
| FR-08 | Students can view course details before enrollment. |
| FR-09 | Course details show teacher, price, description, lessons, and subject information. |

### 3.3 Course Management

| ID | Requirement |
| --- | --- |
| FR-10 | Teachers can create draft courses. |
| FR-11 | Teachers can add lessons to courses. |
| FR-12 | Teachers can add video content to lessons. |
| FR-13 | Teachers can add simple quizzes. |
| FR-14 | Teachers can submit courses for admin approval. |
| FR-15 | Admin can approve or reject courses. |

### 3.4 Prepaid Code Management

| ID | Requirement |
| --- | --- |
| FR-16 | Admin can generate prepaid codes with fixed values. |
| FR-17 | Admin can set code status: active, used, expired, or cancelled. |
| FR-18 | Student or parent can redeem a valid prepaid code. |
| FR-19 | The system must reject invalid, used, expired, or cancelled codes. |
| FR-20 | The system must store code redemption history. |

### 3.5 Enrollment and Access

| ID | Requirement |
| --- | --- |
| FR-21 | Students can enroll in a paid course after successful payment/code redemption. |
| FR-22 | Students can access only courses they are enrolled in. |
| FR-23 | Students buy teacher courses separately. |
| FR-24 | The system must prevent access to unpublished courses. |

### 3.6 Learning and Progress

| ID | Requirement |
| --- | --- |
| FR-25 | Students can watch enrolled video lessons. |
| FR-26 | Videos should not be directly downloadable. |
| FR-27 | Students can mark or automatically record lesson completion. |
| FR-28 | Students can solve basic quizzes. |
| FR-29 | The system tracks student course progress. |

### 3.7 Parent View

| ID | Requirement |
| --- | --- |
| FR-30 | Parents can link to student accounts. |
| FR-31 | Parents can view linked student enrollments. |
| FR-32 | Parents can view linked student progress. |
| FR-33 | Parents can redeem prepaid codes for linked students if allowed by final payment design. |

### 3.8 Admin Management

| ID | Requirement |
| --- | --- |
| FR-34 | Admin can manage users. |
| FR-35 | Admin can manage teachers and education centers. |
| FR-36 | Admin can manage secondary years, subjects, terms, and chapters. |
| FR-37 | Admin can manage course approval status. |
| FR-38 | Admin can manage prepaid codes. |

### 3.9 Reports

| ID | Requirement |
| --- | --- |
| FR-39 | Admin can view course enrollment reports. |
| FR-40 | Admin can view prepaid code reports. |
| FR-41 | Teachers can view reports for their own courses. |
| FR-42 | Education centers can view reports for their own teachers/courses. |

## 4. Basic Non-Functional Requirements

| ID | Requirement |
| --- | --- |
| NFR-01 | The website must support Arabic layout and content. |
| NFR-02 | The website must work on mobile and desktop browsers. |
| NFR-03 | User data must be protected by login and role permissions. |
| NFR-04 | Video playback should be stable for students. |
| NFR-05 | The system should record important admin actions. |

## 5. Open Questions

1. Does a redeemed code add wallet balance or unlock a course directly?
2. Should lesson completion be manual, automatic, or both?
3. What quiz question types are needed in MVP?
4. How should parent-student linking be approved?

## 6. Next Document

The next document should be User Stories and Acceptance Criteria.

