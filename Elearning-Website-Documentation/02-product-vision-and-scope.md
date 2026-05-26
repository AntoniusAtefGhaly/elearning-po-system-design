# E-Learning Website - Product Vision and Scope

## 1. Purpose

This document defines the product vision and scope for the e-learning website. It explains what the product is, who it serves, what the MVP includes, what is out of scope, and the main business rules that guide the first release.

This project is a Product Owner training project. The document is written as a practical handoff artifact for a software team, but the business assumptions are not based on real market validation.

## 2. Product Vision

Create an Arabic-first e-learning marketplace for Egyptian secondary school students where students can find trusted teachers, buy teacher courses using prepaid access codes, study lessons online, solve basic quizzes, and track their progress.

The platform also helps teachers and education centers publish and sell structured courses aligned with the official Egyptian curriculum.

## 3. Product Scope Summary

The first release focuses on Secondary 1, Secondary 2, and Secondary 3 students in Egypt. The platform supports all core school subjects and organizes courses by secondary year, subject, term, chapter, and teacher.

The MVP supports students, parents, teachers, education centers, and admins.

## 4. Target Users

| User Type | Description |
| --- | --- |
| Student | Uses the platform to browse courses, redeem prepaid codes, enroll in teacher courses, watch lessons, solve quizzes, and track progress |
| Parent | Uses the platform to pay or redeem codes and view the student's progress |
| Teacher | Creates and manages courses, uploads lessons, tracks enrollments, and views student progress |
| Education Center | Publishes or manages courses through teachers under the center |
| Admin | Manages users, teachers, education centers, courses, prepaid codes, approvals, reports, and platform settings |

## 5. Problem Statement

Egyptian secondary school students often depend on private lessons and teacher reputation to prepare for exams. Offline private courses may create issues such as travel time, schedule conflicts, limited teacher reach, and difficulty tracking progress.

Teachers and education centers also need a simple way to publish paid courses online, manage student access, and organize content according to the curriculum.

## 6. Product Objectives

- Allow students to access trusted secondary school courses online.
- Allow teachers and education centers to publish paid courses.
- Organize courses according to the Egyptian curriculum by year, subject, term, and chapter.
- Support prepaid code payment instead of direct online payment in the MVP.
- Allow parents to support payment and monitor student progress.
- Prevent direct video download in the MVP.
- Provide admins with control over courses, users, teachers, codes, and reports.

## 7. MVP Scope

The MVP includes the minimum features needed to operate the first version of the platform.

### Student Features

- Register and log in.
- View available courses.
- Filter courses by secondary year, subject, term, chapter, and teacher.
- View course details.
- Redeem prepaid access code.
- Enroll in paid teacher courses.
- Watch enrolled course lessons.
- Solve basic quizzes.
- Track lesson and course progress.

### Parent Features

- Register and log in.
- Link to one or more student accounts.
- Redeem prepaid access codes or support payment.
- View student course progress.

### Teacher Features

- Register or be created by admin.
- Manage teacher profile.
- Create and manage courses.
- Organize course content by term and chapter.
- Upload or add video lessons.
- Add basic quizzes.
- View enrolled students.
- View student progress.

### Education Center Features

- Register or be created by admin.
- Manage center profile.
- Manage teachers linked to the center.
- Publish or manage courses through center teachers.

### Admin Features

- Manage students, parents, teachers, and education centers.
- Approve or reject teacher accounts.
- Approve or reject courses before publishing.
- Manage school years, subjects, terms, and chapters.
- Generate prepaid access codes with fixed values, such as 50 EGP and 100 EGP.
- Track generated, redeemed, cancelled, and expired codes.
- Manage course access.
- View enrollment and revenue reports.
- Manage platform settings.

## 8. Out of Scope for MVP

The following features are not included in the first release:

- Mobile application.
- Live classes.
- Chat or community forum.
- AI recommendations.
- Advanced gamification.
- Certificates.
- English interface.
- Subject bundles.
- Direct online card or wallet payment gateway.
- Complex teacher payout automation.
- Advanced exam engine.
- Homework correction workflow.
- Video watermarking, unless added later.

## 9. Main Business Rules

| Rule ID | Business Rule |
| --- | --- |
| BR-001 | The platform launches in Arabic first. |
| BR-002 | The first release supports Secondary 1, Secondary 2, and Secondary 3. |
| BR-003 | Courses must be linked to secondary year, subject, term, chapter, and teacher. |
| BR-004 | Students buy teacher courses separately. |
| BR-005 | Subject bundles are not included in the MVP. |
| BR-006 | Payment in MVP is handled through prepaid access codes. |
| BR-007 | Admin can generate prepaid codes with fixed values, such as 50 EGP and 100 EGP. |
| BR-008 | A prepaid code cannot be redeemed more than allowed by its configuration. |
| BR-009 | Parents can view student progress in MVP. |
| BR-010 | Videos should not be directly downloadable by students. |
| BR-011 | Courses require admin approval before publishing. |
| BR-012 | Teachers create the initial course content. |

## 10. Assumptions

- Students and parents accept prepaid access codes as the MVP payment model.
- Teachers are responsible for creating and maintaining their own course content.
- Students mostly access the platform through mobile browsers.
- Arabic is enough for the first release.
- No-download video protection is acceptable for MVP, even if stronger anti-piracy tools are added later.

## 11. Dependencies

| Dependency | Why It Matters |
| --- | --- |
| Teacher content | The platform needs real courses before students can use it |
| Video hosting | Lessons require stable video playback and no-download controls |
| Prepaid code process | Payment and access depend on code generation and redemption |
| Curriculum structure | Courses must match secondary year, subject, term, and chapter |
| Admin operations | Courses, teachers, and codes need approval and monitoring |

## 12. Success Criteria for MVP

Because this is a training project, success is measured by documentation completeness and clarity rather than real market results.

The MVP documentation is successful if a software team can understand:

- Who the users are.
- What each user can do.
- What features are included in MVP.
- What features are excluded from MVP.
- What the main business rules are.
- What the major diagrams and requirements should cover next.

## 13. Next Document

The next document should define stakeholders and user roles in more detail. It will explain each role, responsibilities, permissions, and how users relate to each other.

