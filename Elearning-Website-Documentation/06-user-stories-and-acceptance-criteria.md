# E-Learning Website - User Stories and Acceptance Criteria

## 1. Purpose

This document converts the MVP requirements into user stories that the software team can use for planning and implementation.

## 2. Student Stories

### US-01: Student Registration

As a student, I want to create an account so that I can use the learning platform.

Acceptance Criteria:

- Student can enter required registration details.
- Student can log in after successful registration.
- Student cannot register with an already used email or phone number.

### US-02: Browse Courses

As a student, I want to browse courses so that I can find suitable lessons for my school year and subject.

Acceptance Criteria:

- Student can view published courses only.
- Student can filter by secondary year, subject, term, chapter, and teacher.
- Student can open a course details page.

### US-03: Redeem Prepaid Code

As a student, I want to redeem a prepaid code so that I can pay for course access.

Acceptance Criteria:

- Student can enter a prepaid code.
- System accepts active valid codes.
- System rejects invalid, used, expired, or cancelled codes.
- System records successful code redemption.

### US-04: Enroll in Course

As a student, I want to enroll in a teacher course so that I can access its lessons.

Acceptance Criteria:

- Student can enroll after successful payment/code redemption.
- Student can only access enrolled courses.
- Student buys each teacher course separately.

### US-05: Watch Lessons

As a student, I want to watch course lessons so that I can study online.

Acceptance Criteria:

- Student can play video lessons for enrolled courses.
- Student cannot access lessons for unenrolled courses.
- Video is not directly downloadable.

### US-06: Track Progress

As a student, I want to see my progress so that I know what I completed.

Acceptance Criteria:

- System tracks completed lessons.
- Student can see course progress percentage or status.
- Progress updates after lesson completion.

## 3. Parent Stories

### US-07: Parent Registration

As a parent, I want to create an account so that I can follow my child.

Acceptance Criteria:

- Parent can register and log in.
- Parent can link to a student account.
- Parent can only view linked students.

### US-08: View Student Progress

As a parent, I want to view my child's progress so that I can follow their learning.

Acceptance Criteria:

- Parent can view linked student courses.
- Parent can view linked student progress.
- Parent cannot view unlinked students.

### US-09: Parent Redeems Code

As a parent, I want to redeem a prepaid code so that I can support my child's course payment.

Acceptance Criteria:

- Parent can enter a prepaid code.
- System validates the code.
- Successful redemption is linked to the correct student/payment flow.

## 4. Teacher Stories

### US-10: Manage Course

As a teacher, I want to create and manage courses so that I can sell my lessons online.

Acceptance Criteria:

- Teacher can create a draft course.
- Teacher can set year, subject, term, chapter, price, and description.
- Teacher can edit own draft courses.

### US-11: Add Lessons

As a teacher, I want to add lessons to my course so that students can study the content.

Acceptance Criteria:

- Teacher can add lesson title and order.
- Teacher can add video content.
- Teacher can edit or remove own lessons before publishing.

### US-12: Submit Course for Approval

As a teacher, I want to submit my course for approval so that it can be published.

Acceptance Criteria:

- Teacher can submit a complete course for approval.
- Submitted course status changes to pending approval.
- Teacher cannot publish without admin approval.

### US-13: View Course Progress

As a teacher, I want to view student progress in my courses so that I can monitor learning.

Acceptance Criteria:

- Teacher can view enrolled students in own courses.
- Teacher can view progress for own course students.
- Teacher cannot view other teachers' course data.

## 5. Admin Stories

### US-14: Approve Teacher

As an admin, I want to approve teachers so that only allowed teachers can publish courses.

Acceptance Criteria:

- Admin can view pending teacher accounts.
- Admin can approve or reject a teacher.
- Rejected teachers cannot publish courses.

### US-15: Approve Course

As an admin, I want to approve courses so that only reviewed courses appear to students.

Acceptance Criteria:

- Admin can view pending courses.
- Admin can approve or reject a course.
- Approved courses become visible in the catalog.
- Rejected courses remain hidden from students.

### US-16: Generate Prepaid Codes

As an admin, I want to generate prepaid codes so that students or parents can pay using codes.

Acceptance Criteria:

- Admin can generate codes with fixed values.
- Each code has a unique value/code number.
- Each code has a status.
- Admin can view generated codes.

### US-17: Manage Curriculum Data

As an admin, I want to manage years, subjects, terms, and chapters so that courses are organized correctly.

Acceptance Criteria:

- Admin can add and edit secondary years.
- Admin can add and edit subjects.
- Admin can add and edit terms and chapters.
- Courses can be linked to this curriculum data.

## 6. Education Center Stories

### US-18: Manage Center Teachers

As an education center, I want to manage teachers so that the center can organize its courses.

Acceptance Criteria:

- Center can view linked teachers.
- Center can request or add teacher linkage based on admin rules.
- Center can view center-related courses.

## 7. Notes

These stories are MVP-level stories. More detailed stories can be added later during backlog refinement.

