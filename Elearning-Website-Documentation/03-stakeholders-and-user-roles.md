# E-Learning Website - Stakeholders and User Roles

## 1. Purpose

This document defines the main users and what each user can do.

## 2. Stakeholders

| Stakeholder | Interest |
| --- | --- |
| Students | Study courses and track progress |
| Parents | Pay and monitor progress |
| Teachers | Sell and manage courses |
| Education Centers | Manage teachers and center courses |
| Admins | Manage the platform |
| Software Team | Build the system from clear requirements |

## 3. User Roles

### Student

Can:

- Register and log in
- Register without parent approval
- Browse courses
- Redeem prepaid code
- Enroll in courses
- Watch enrolled lessons
- Solve basic MCQ quizzes
- View own progress

Cannot:

- Access paid courses without enrollment
- Publish courses
- Generate prepaid codes

### Parent

Can:

- Register and log in
- Link to student account
- Redeem prepaid code
- View linked student progress

Cannot:

- View unlinked students
- Publish courses
- Generate prepaid codes

### Teacher

Can:

- Manage profile
- Create draft courses
- Add lessons and MCQ quizzes
- Submit courses for approval
- View enrolled students and progress for own courses

Cannot:

- Publish without admin approval
- Generate prepaid codes
- Manage other teachers' courses

### Education Center

Can:

- Manage center profile
- Manage linked teachers
- Create teacher accounts
- View center courses and reports

Cannot:

- Approve its own courses
- Generate prepaid codes
- Manage platform settings

### Admin

Can:

- Manage users
- Approve teachers
- Approve courses
- Manage years, subjects, terms, and chapters
- Generate and manage prepaid codes
- Manually adjust student balance
- View reports

## 4. Simple Permission Matrix

| Action | Student | Parent | Teacher | Center | Admin |
| --- | --- | --- | --- | --- | --- |
| Browse courses | Yes | Yes | Yes | Yes | Yes |
| Redeem code | Yes | Yes | No | No | Manage |
| Enroll in course | Yes | For student | No | No | Support |
| Watch lessons | Yes | No | Own courses | Center courses | Support |
| View progress | Own | Linked student | Own courses | Center courses | All |
| Create course | No | No | Yes | With teachers | Support |
| Approve course | No | No | No | No | Yes |
| Generate codes | No | No | No | No | Yes |

## 5. Main Relationships

- One parent can link to one or more students.
- Parent links to student using student ID.
- One teacher can create many courses.
- One education center can have many teachers.
- One teacher can be independent or linked to one education center only.
- One student can enroll in many courses.
- One prepaid code can be redeemed for one student only.
- Prepaid codes have serial numbers and do not expire.
- Admin approves teachers and courses.

## 6. Confirmed Decisions

1. Students can register without parent approval.
2. A teacher cannot belong to more than one education center.
3. A parent cannot redeem one code for multiple students.
4. Teacher sets course price, and admin can edit it.
