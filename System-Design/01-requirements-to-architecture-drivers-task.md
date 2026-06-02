# Task 01 - From Requirements to Architecture Drivers

## Purpose

This task helps you practice the first step of software architecture:

> Convert product requirements into architecture thinking.

You will read the existing E-learning project requirements, classify them, identify the most important architecture drivers, and explain their impact on the system design.

## Source Documents

Use these existing documents as your source:

- `Elearning-Website-Documentation/Required-Documents/02-product-vision-and-scope.md`
- `Elearning-Website-Documentation/Required-Documents/03-stakeholders-and-user-roles.md`
- `Elearning-Website-Documentation/Required-Documents/04-business-requirements.md`
- `Elearning-Website-Documentation/Required-Documents/05-functional-requirements-srs.md`

## Product Summary

The product is an Arabic-first E-learning website for Egyptian secondary school students.

Students can browse teacher courses, redeem prepaid codes, buy courses using student balance, watch recorded lessons, solve MCQ quizzes, and track progress.

Teachers and education centers can publish courses based on the official Egyptian curriculum. Admins manage approvals, users, prepaid codes, balances, reports, and platform settings.

## Existing Functional Requirements

Use the list below as your starting point.

### User Account Management

- Users can log in and log out.
- Students can create accounts.
- Parents can create accounts.
- Teachers and education centers can have accounts approved by admin.
- Users can update basic profile information.
- Students can register without parent approval.
- Teacher approval data includes name, phone, subject, bio, profile image, and documents.
- Education centers can create teacher accounts.
- Admin can link existing teachers to education centers.

### Course Catalog

- Students can browse published courses.
- Students can filter courses by secondary year, subject, term, chapter, and teacher.
- Students can view course details before enrollment.
- Course details show teacher, price, description, lessons, and subject information.

### Course Management

- Teachers can create draft courses.
- Teachers can add lessons to courses.
- Teachers can add video content to lessons.
- Teachers can add MCQ quizzes.
- Teachers can submit courses for admin approval.
- Admin can approve or reject courses.
- Teacher can set course price.
- Admin can edit teacher course prices.

### Prepaid Code and Balance Management

- Admin can generate prepaid codes with fixed values.
- Admin can set code status: active, used, or cancelled.
- Student or parent can redeem a valid prepaid code.
- The system must reject invalid, used, or cancelled codes.
- The system must store code redemption history.
- Each prepaid code can be redeemed for one student only.
- Redeemed code value is added to the student's balance.
- Admin can track manually distributed codes.
- Admin can reset a student's balance to 0 for manual refund handling.
- Student balance can be used partially across multiple courses.
- Student balance cannot become negative.
- Admin can manually add or subtract student balance.
- Prepaid codes do not expire.
- Admin can cancel an active prepaid code.
- Prepaid codes have serial numbers for manual distribution tracking.

### Enrollment and Access

- Students can enroll in a paid course after successful payment/code redemption.
- Students can access only courses they are enrolled in.
- Students buy teacher courses separately.
- The system must prevent access to unpublished courses.

### Learning and Progress

- Students can watch enrolled video lessons.
- Videos should not be directly downloadable.
- Students can mark lesson completion manually, and the system can record completion automatically.
- Students can solve MCQ quizzes.
- The system tracks student course progress.
- Automatic lesson completion happens after watching 90% of the video.
- Quiz score is shown to the student.
- Student cannot retry a quiz in MVP.
- Quiz result affects course progress.

### Parent View

- Parents can link to student accounts.
- Parents can view linked student enrollments.
- Parents can view linked student progress.
- Parents can redeem prepaid codes for one linked student at a time.
- Parent links to student using student ID.

### Admin and Reports

- Admin can manage users.
- Admin can manage teachers and education centers.
- Admin can manage secondary years, subjects, terms, and chapters.
- Admin can manage course approval status.
- Admin can manage prepaid codes.
- Admin can view course enrollment reports.
- Admin can view prepaid code reports.
- Teachers can view reports for their own courses.
- Education centers can view reports for their own teachers/courses.
- Admin can view teacher sales reports.
- Admin can view student progress reports.

## Existing Non-Functional Requirements

The documentation currently defines these basic non-functional requirements:

- The website must support Arabic layout and content.
- The website must work on mobile and desktop browsers.
- User data must be protected by login and role permissions.
- Video playback should be stable for students.
- The system should record important admin actions.

## Important Business Rules

Use these rules when thinking about architecture:

- Courses are hidden until admin approval.
- Payment is done using prepaid codes in the MVP.
- Direct card or wallet payment is out of scope.
- Students buy teacher courses separately.
- Videos must not be directly downloadable.
- A parent can link to one or more students.
- A teacher can be independent or linked to one education center only.
- Each prepaid code can be redeemed for one student only.
- Redeemed code value is added to the student's balance.
- Student balance can be used partially across multiple courses.
- Student balance cannot become negative.
- Prepaid codes do not expire.
- Refunds are handled manually outside the system.
- Lesson completion can be manual or automatic.
- Automatic lesson completion happens after watching 90% of the video.
- MVP quizzes use MCQ questions only.
- Quiz retry is not allowed in MVP.
- Quiz result affects course progress.
- MVP reports include codes, enrollments, teacher sales, and student progress.

## Your Big Task

Complete the sections below.

Do not write code. Think like a software architect.

## Part 1 - Rewrite the System Goal

Write the system goal in your own words.

```text
System Goal:

```

## Part 2 - Identify Actors

List the human actors and external system actors.

```text
Human Actors:
1.
2.
3.
4.
5.

External System Actors:
1.
2.
3.
```

## Part 3 - Separate Functional Requirements by Module

Choose the most important 3 to 5 requirements for each module.

```text
1. Identity and Access
- 
- 
- 

2. Course Catalog
- 
- 
- 

3. Course Management
- 
- 
- 

4. Prepaid Code and Balance
- 
- 
- 

5. Enrollment and Access Control
- 
- 
- 

6. Learning, Quiz, and Progress
- 
- 
- 

7. Parent View
- 
- 
- 

8. Admin and Reports
- 
- 
- 
```

## Part 4 - Improve the Non-Functional Requirements

The current non-functional requirements are useful, but they are too general.

Rewrite them to be more measurable.

Example:

Weak:
Video playback should be stable for students.

Better:
Video playback should start within 3 seconds for most students under normal network conditions.

```text
NFR-01 Arabic Support:

NFR-02 Mobile and Desktop:

NFR-03 Security and Permissions:

NFR-04 Video Playback:

NFR-05 Audit Trail:

NFR-06 Performance:

NFR-07 Data Integrity:

NFR-08 Availability:
```

## Part 5 - Identify Architecture Drivers

Select the top 5 architecture drivers.

For each one, explain why it matters and how it affects architecture.

```text
1. Driver:
   Why it matters:
   Architecture impact:

2. Driver:
   Why it matters:
   Architecture impact:

3. Driver:
   Why it matters:
   Architecture impact:

4. Driver:
   Why it matters:
   Architecture impact:

5. Driver:
   Why it matters:
   Architecture impact:
```

## Part 6 - Find Risky Requirements

Some requirements are risky because they affect money, access, privacy, or correctness.

Identify at least 5 risky requirements.

```text
1. Risky Requirement:
   Risk:
   Possible protection:

2. Risky Requirement:
   Risk:
   Possible protection:

3. Risky Requirement:
   Risk:
   Possible protection:

4. Risky Requirement:
   Risk:
   Possible protection:

5. Risky Requirement:
   Risk:
   Possible protection:
```

## Part 7 - First Architecture Style Recommendation

Choose one initial architecture style.

Recommended options:

- Layered Architecture
- Clean Architecture
- Modular Monolith
- Microservices
- Event-Driven Architecture

For this MVP, do not choose microservices unless you can strongly defend it.

```text
Recommended Architecture Style:

Why this style fits the MVP:

Why not microservices now:

What modules should be separated clearly inside the codebase:
1.
2.
3.
4.
5.
```

## Part 8 - Open Questions for the Product Owner

Write questions that must be answered before final architecture design.

```text
1.
2.
3.
4.
5.
```

## Review Checklist

Before you finish, check your answer:

- Did you separate functional requirements from non-functional requirements?
- Did you make non-functional requirements measurable?
- Did you identify architecture drivers, not only features?
- Did you connect every driver to architecture impact?
- Did you notice money-related risks around prepaid codes and student balance?
- Did you notice access-control risks around courses, parents, teachers, centers, and admins?
- Did you avoid jumping to microservices without a strong reason?

