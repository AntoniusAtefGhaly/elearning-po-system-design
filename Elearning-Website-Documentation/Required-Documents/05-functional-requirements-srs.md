# E-Learning Website - Functional Requirements / SRS

## 1. Purpose

This document describes the main system functions needed for the MVP.

## 2. System Modules

The system is divided into these business modules:

Detailed module documents 08 to 12 are planned for Phase 2. MVP still includes prepaid code and student balance rules under Payment & Subscription Management.

- Payment & Subscription Management
- Notification Management
- Parent Portal
- Reporting & Analytics
- Administration

### 2.1 Identity & Access Management

Description: Handles authentication, user accounts, roles, and authorization.

Responsibilities:

- User registration
- Login/logout
- Role management: Student, Teacher, Admin, Parent
- Access control using RBAC

### 2.2 Teacher Management

Description: Manages teacher profiles and their lifecycle within the platform.

Responsibilities:

- Teacher onboarding
- Profile management
- Verification
- Linking teachers to courses

### 2.3 Student Management

Description: Manages student accounts and learning activity.

Responsibilities:

- Student registration
- Profile management
- Activity tracking
- Course associations

### 2.4 Content & Course Management

Description: Responsible for creating, managing, structuring, and publishing educational courses and their learning materials.

Responsibilities:

- Create and edit courses
- Publish courses
- Categorize courses
- Create subjects, modules, and lessons
- Upload videos and documents
- Organize course materials

Key entities:

- Course
- Category
- Tag
- Subject
- Module
- Lesson
- Video
- Document
- Media File

### 2.5 Enrollment Management

Description: Handles student enrollment in courses.

Responsibilities:

- Enroll students in courses
- Cancel enrollment
- Track enrollment status

Key entities:

- Enrollment

### 2.6 Assessment Management

Description: Manages exams, quizzes, and evaluations.

Responsibilities:

- Create exams
- Create questions
- Publish assessments
- Define grading rules

Key entities:

- Exam
- Question
- Answer

### 2.7 Grading Management

Description: Handles evaluation and grading of student submissions.

Responsibilities:

- Grade exams
- Calculate scores
- Generate results

Key entities:

- Grade
- Result

### 2.8 Payment & Subscription Management

Description: Handles prepaid codes and student balance in MVP. Payment gateway, subscriptions, and invoices are future scope.

Responsibilities:

- Generate prepaid codes
- Delete prepaid codes
- Manage student balance

Key entities:

- Prepaid Code
- Payment

### 2.9 Notification Management

Description: Future scope. Handles all system notifications.

Responsibilities:

- Email notifications
- In-app notifications
- Alerts and reminders

### 2.10 Parent Portal

Description: Provides parents with visibility into student progress.

Responsibilities:

- Track student performance
- View results
- Monitor activity

### 2.11 Reporting & Analytics

Description: Provides business intelligence and system analytics.

Responsibilities:

- Student performance reports
- Teacher performance reports
- Platform KPIs

### 2.12 Administration

Description: System-wide administration and configuration.

Responsibilities:

- User management
- System monitoring
- Platform configuration

## 3. Functional Requirements

### 3.1 Identity & Access Management

| ID | Requirement |
| --- | --- |
| FR-01 | Users can log in and log out. |
| FR-02 | Students can create accounts. |
| FR-03 | Parents can create accounts. |
| FR-04 | Teachers can have accounts approved by admin. |
| FR-05 | Users can update basic profile information. |
| FR-05A | Students can register without parent approval. |
| FR-05B | Teacher approval data includes name, phone, subject, bio, profile image, and documents. |

### 3.2 Course Catalog

| ID | Requirement |
| --- | --- |
| FR-06 | Students can browse published courses. |
| FR-07 | Students can filter courses by secondary year, subject, term, chapter, and teacher. |
| FR-08 | Students can view course details before enrollment. |
| FR-09 | Course details show teacher, price, description, lessons, and subject information. |

### 3.3 Content & Course Management

| ID | Requirement |
| --- | --- |
| FR-10 | Teachers can create draft courses. |
| FR-11 | Teachers can add lessons to courses. |
| FR-12 | Teachers can add video content to lessons. |
| FR-13 | Teachers can add assessments/quizzes. |
| FR-14 | Teachers can submit courses for admin approval. |
| FR-15 | Admin can approve or reject courses. |
| FR-15A | Teacher can set course price. |
| FR-15B | Admin can edit teacher course prices. |

### 3.4 Payment & Subscription Management

| ID | Requirement |
| --- | --- |
| FR-16 | Admin can generate prepaid codes with fixed values. |
| FR-17 | Admin can set code status: active, used, or cancelled. |
| FR-18 | Student or parent can redeem a valid prepaid code. |
| FR-19 | The system must reject invalid, used, or cancelled codes. |
| FR-20 | The system must store code redemption history. |
| FR-20A | Each prepaid code can be redeemed for one student only. |
| FR-20B | Redeemed code value is added to the student's balance. |
| FR-20C | Admin can track manually distributed codes. |
| FR-20D | Admin can reset a student's balance to 0 for manual refund handling. |
| FR-20E | Student balance can be used partially across multiple courses. |
| FR-20F | Student balance cannot become negative. |
| FR-20G | Admin can manually add or subtract student balance. |
| FR-20H | Prepaid codes do not expire. |
| FR-20I | Admin can cancel an active prepaid code. |
| FR-20J | Prepaid codes have serial numbers for manual distribution tracking. |

### 3.5 Enrollment Management

| ID | Requirement |
| --- | --- |
| FR-21 | Students can enroll in a paid course after successful payment/code redemption. |
| FR-22 | Students can access only courses they are enrolled in. |
| FR-23 | Students buy teacher courses separately. |
| FR-24 | The system must prevent access to unpublished courses. |

### 3.6 Assessment and Grading Management

| ID | Requirement |
| --- | --- |
| FR-25 | Students can watch enrolled video lessons. |
| FR-26 | Videos should not be directly downloadable. |
| FR-27 | Students can mark lesson completion manually, and the system can record completion automatically. |
| FR-28 | Students can solve assessments according to the Assessment Management module scope. |
| FR-29 | The system tracks student course progress. |
| FR-29A | Automatic lesson completion happens after watching 90% of the video. |
| FR-29B | Quiz score is shown to the student. |
| FR-29C | Student can retry a quiz in MVP. |
| FR-29D | Quiz result affects course progress. |

### 3.7 Parent Portal

| ID | Requirement |
| --- | --- |
| FR-30 | Parents can link to student accounts. |
| FR-31 | Parents can view linked student enrollments. |
| FR-32 | Parents can view linked student progress. |
| FR-33 | Parents can redeem prepaid codes for one linked student at a time. |
| FR-33A | Parent links to student using student ID. |

### 3.8 Administration

| ID | Requirement |
| --- | --- |
| FR-34 | Admin can manage users. |
| FR-35 | Admin can manage teachers. |
| FR-36 | Admin can manage secondary years, subjects, terms, and chapters. |
| FR-37 | Admin can manage course approval status. |
| FR-38 | Admin can manage prepaid codes. |

### 3.9 Reporting & Analytics

| ID | Requirement |
| --- | --- |
| FR-39 | Admin can view course enrollment reports. |
| FR-40 | Admin can view prepaid code reports. |
| FR-41 | Teachers can view reports for their own courses. |
| FR-43 | Admin can view teacher sales reports. |
| FR-44 | Admin can view student progress reports. |

## 4. Basic Non-Functional Requirements

| ID | Requirement |
| --- | --- |
| NFR-01 | The website must support Arabic layout and content. |
| NFR-02 | The website must work on mobile and desktop browsers. |
| NFR-03 | User data must be protected by login and role permissions. |
| NFR-04 | Video playback should be stable for students. |
| NFR-05 | The system should record important admin actions. |

## 5. Open Questions

No open functional requirement questions for now.

## 6. Next Document

The next document should be User Stories and Acceptance Criteria.
