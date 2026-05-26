# E-Learning Website - Stakeholders and User Roles

## 1. Purpose

This document defines the stakeholders and user roles for the e-learning website. It explains who is involved in the product, what each role needs, and what each role can do in the system.

This document helps the software team understand permissions, responsibilities, and user relationships before writing detailed requirements.

## 2. Stakeholders

Stakeholders are people or groups who care about the product, even if they do not all use the system directly.

| Stakeholder | Interest in the Product |
| --- | --- |
| Students | Need to study online, access teacher courses, watch lessons, solve quizzes, and track progress |
| Parents | Need to support payment and monitor student progress |
| Teachers | Need to publish courses, manage lessons, and track student activity |
| Education Centers | Need to manage teachers and sell courses under the center brand |
| Platform Admins | Need to manage users, content, codes, approvals, reports, and settings |
| Business Owner | Needs the product to support a clear business model and controlled growth |
| Software Team | Needs clear requirements, roles, business rules, and scope |

## 3. User Roles

The MVP has five main system roles:

1. Student
2. Parent
3. Teacher
4. Education Center
5. Admin

## 4. Student Role

### Description

The student is the main learning user. Students use the platform to browse courses, redeem prepaid codes, enroll in teacher courses, watch lessons, solve quizzes, and track progress.

### Main Goals

- Find courses for their secondary year and subject.
- Select a trusted teacher.
- Access paid lessons after payment/code redemption.
- Study lessons online.
- Track learning progress.
- Practice through basic quizzes.

### Main Permissions

- Register and log in.
- Edit own profile.
- Browse published courses.
- Filter courses by secondary year, subject, term, chapter, and teacher.
- View course details and free preview content.
- Redeem prepaid access codes.
- Enroll in paid courses.
- Watch enrolled lessons.
- Solve quizzes.
- View own progress.
- View own enrollment history.

### Restrictions

- Cannot access paid courses without valid enrollment.
- Cannot publish courses.
- Cannot approve teachers or courses.
- Cannot generate prepaid codes.
- Cannot view other students' progress.
- Cannot directly download protected videos.

## 5. Parent Role

### Description

The parent supports the student by handling payment/code redemption and viewing student progress. Parent access is included in the MVP.

### Main Goals

- Link to their child or children.
- Support payment using prepaid codes.
- View student progress.
- Understand which courses the student is enrolled in.

### Main Permissions

- Register and log in.
- Edit own profile.
- Link to one or more student accounts.
- Redeem prepaid access codes for a linked student, depending on final payment design.
- View linked student course enrollments.
- View linked student progress.

### Restrictions

- Cannot watch lessons as the student unless explicitly allowed later.
- Cannot solve quizzes for the student.
- Cannot publish courses.
- Cannot approve content.
- Cannot generate prepaid codes.
- Cannot view students who are not linked to the parent account.

## 6. Teacher Role

### Description

The teacher creates and manages course content. Teachers can be independent private-course teachers or linked to an education center.

### Main Goals

- Publish structured courses.
- Organize lessons according to the Egyptian curriculum.
- Sell courses to students.
- Track student enrollments and progress.
- Build trust through teacher profile and course quality.

### Main Permissions

- Log in.
- Manage teacher profile.
- Create draft courses.
- Edit own courses.
- Add lessons.
- Add video lesson content.
- Add basic quizzes.
- Organize content by secondary year, subject, term, and chapter.
- View students enrolled in own courses.
- View progress for students enrolled in own courses.
- Submit courses for admin approval.

### Restrictions

- Cannot publish a course without admin approval.
- Cannot edit platform curriculum settings unless admin allows it.
- Cannot access courses owned by other teachers.
- Cannot generate prepaid codes.
- Cannot approve own account or own courses.
- Cannot manage platform-wide users.

## 7. Education Center Role

### Description

The education center represents an organization that manages teachers and courses. It may publish or supervise courses through teachers under the center.

### Main Goals

- Manage center profile.
- Manage teachers linked to the center.
- Sell courses under the center brand.
- Track performance of center teachers and courses.

### Main Permissions

- Log in.
- Manage center profile.
- Add or request teachers under the center.
- View center teachers.
- View courses linked to the center.
- View enrollments and progress for center courses, depending on admin rules.
- Submit center courses for admin approval.

### Restrictions

- Cannot approve its own courses.
- Cannot approve teacher accounts.
- Cannot generate prepaid codes unless admin gives this permission later.
- Cannot view courses or student data outside the center.
- Cannot change platform-wide settings.

## 8. Admin Role

### Description

The admin manages platform operations, approvals, users, content, prepaid codes, reports, and settings.

### Main Goals

- Keep platform data organized.
- Approve trusted teachers and courses.
- Control prepaid code generation and redemption.
- Monitor enrollments and revenue.
- Support students, parents, teachers, and centers.

### Main Permissions

- Manage students.
- Manage parents.
- Manage teachers.
- Manage education centers.
- Approve or reject teacher accounts.
- Approve or reject courses.
- Manage secondary years.
- Manage subjects.
- Manage terms and chapters.
- Generate prepaid access codes with fixed values.
- Cancel or expire prepaid codes.
- View code redemption history.
- Manage course access if support is needed.
- View enrollment reports.
- View revenue or code-value reports.
- Manage platform settings.

### Restrictions

- Admin actions should be logged for auditing.
- Admin should not change student progress manually unless a support/admin correction flow is defined later.

## 9. Role Relationship Rules

| Relationship | Rule |
| --- | --- |
| Parent to Student | A parent can be linked to one or more students |
| Student to Parent | A student may be linked to one or more parents/guardians if allowed |
| Teacher to Course | A teacher can create many courses |
| Course to Teacher | Each course belongs to one main teacher |
| Education Center to Teacher | An education center can have many teachers |
| Teacher to Education Center | A teacher may be independent or linked to one education center |
| Student to Course | A student can enroll in many courses |
| Course to Student | A course can have many enrolled students |
| Admin to Course | Admin approves or rejects courses before publishing |
| Admin to Code | Admin generates, cancels, expires, and tracks prepaid access codes |

## 10. Permission Matrix

| Feature / Action | Student | Parent | Teacher | Education Center | Admin |
| --- | --- | --- | --- | --- | --- |
| Register / log in | Yes | Yes | Limited / Admin approval | Limited / Admin approval | Yes |
| Browse courses | Yes | Yes | Yes | Yes | Yes |
| Redeem prepaid code | Yes | Yes | No | No | Manage only |
| Enroll in course | Yes | For linked student | No | No | Support only |
| Watch lessons | Yes, if enrolled | No | Own courses | Center courses if allowed | Support only |
| Solve quizzes | Yes | No | Preview own quizzes | No | Support only |
| View student progress | Own only | Linked students only | Own enrolled students | Center students if allowed | Yes |
| Create course | No | No | Yes | Through linked teachers | Yes / Support |
| Edit course | No | No | Own courses | Center courses if allowed | Yes |
| Approve course | No | No | No | No | Yes |
| Generate prepaid codes | No | No | No | No | Yes |
| Manage subjects/years/chapters | No | No | No | No | Yes |
| View reports | Own history only | Linked student only | Own course reports | Center reports | Full reports |

## 11. Open Questions

These questions should be answered in later requirements:

1. Can a student create an account without a parent?
2. Can one prepaid code be redeemed by parent only, student only, or both?
3. Can an education center create teachers directly, or must admin approve each teacher?
4. Can a teacher belong to more than one education center?
5. Can a parent pay for multiple students using the same balance?
6. Can admin impersonate users for support, or only view data?

## 12. Next Document

The next document should be the Business Requirements Document. It will define the business needs, rules, and high-level requirements that the system must satisfy.

