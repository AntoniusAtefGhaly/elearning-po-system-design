# E-Learning Website - Combined Required Documents

## Purpose

This file combines all required product and business documents into one Markdown reference for easier review.

## Included Documents

- 02-product-vision-and-scope.md
- 03-stakeholders-and-user-roles.md
- 04-business-requirements.md
- 05-functional-requirements-srs.md
- 06-user-stories-and-acceptance-criteria.md
- 08-product-backlog.md
- 11-screen-list.md

---

## 02-product-vision-and-scope

## E-Learning Website - Product Vision and Scope

### 1. Purpose

This document defines the product vision and MVP scope.

### 2. Product Vision

Create an Arabic-first e-learning website for Egyptian secondary school students where students can buy teacher courses using prepaid codes, watch lessons, solve simple quizzes, and track progress.

### 3. MVP Users

| User | Main Need |
| --- | --- |
| Student | Study online and track progress |
| Parent | Pay/redeem codes and view progress |
| Teacher | Publish and manage courses |
| Admin | Manage approvals, codes, users, and reports |

### 4. MVP Scope

The first release supports:

- Secondary 1, Secondary 2, and Secondary 3
- All core subjects
- Arabic interface
- Official Egyptian curriculum structure
- Private teachers
- Prepaid code payment
- Separate purchase for each teacher course
- No direct video download

### 5. Main Features

#### Student

- Register and log in
- Browse courses
- Redeem prepaid code
- Enroll in a course
- Watch lessons
- Solve quizzes and assessments
- View progress

#### Parent

- Register and log in
- Link to student
- Redeem prepaid code
- View student progress

#### Teacher

- Manage profile
- Create courses
- Add lessons and quizzes
- Submit courses for approval
- View enrolled students and progress

#### Admin

- Manage users
- Approve teachers and courses
- Manage curriculum data
- Generate prepaid codes
- View basic reports
- Manually adjust student balance

### 6. Out of Scope

- Mobile app
- Live classes
- Chat or forum
- Certificates
- English interface
- Subject bundles
- Direct online payment gateway
- Subscriptions and invoices
- Free course enrollment
- Course archive/delete/restore lifecycle
- Notifications
- Attendance tracking
- Advanced video watermarking
- Parent-student link approval workflow

### 7. Main Business Rules

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
| R-14 | Assessment and grading scope follows the Assessment Management and Grading Management module documents. |
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
| R-30 | Quiz retry is allowed in MVP. |
| R-31 | Quiz result affects course progress. |
| R-32 | MVP reports include codes, enrollments, teacher sales, and student progress. |
| R-33 | MVP payment uses prepaid codes and student balance only; payment gateway is future scope. |

### 8. Success for This Training Project

The documentation is successful if a software team can understand the MVP scope, users, features, and business rules.


---

## 03-stakeholders-and-user-roles

## E-Learning Website - Stakeholders and User Roles

### 1. Purpose

This document defines the main users and what each user can do.

### 2. Stakeholders

| Stakeholder | Interest |
| --- | --- |
| Students | Study courses and track progress |
| Parents | Pay and monitor progress |
| Teachers | Sell and manage courses |
| Admins | Manage the platform |
| Software Team | Build the system from clear requirements |

### 3. User Roles

#### Student

Can:

- Register and log in
- Register without parent approval
- Browse courses
- Redeem prepaid code
- Enroll in courses
- Watch enrolled lessons
- Solve assessments/quizzes
- View own progress

Cannot:

- Access paid courses without enrollment
- Publish courses
- Generate prepaid codes

#### Parent

Can:

- Register and log in
- Link to student account
- Redeem prepaid code
- View linked student progress

Cannot:

- View unlinked students
- Publish courses
- Generate prepaid codes

#### Teacher

Can:

- Manage profile
- Create draft courses
- Add lessons and assessments/quizzes
- Submit courses for approval
- View enrolled students and progress for own courses

Cannot:

- Publish without admin approval
- Generate prepaid codes
- Manage other teachers' courses

#### Admin

Can:

- Manage users
- Approve teachers
- Approve courses
- Manage years, subjects, terms, and chapters
- Generate and manage prepaid codes
- Manually adjust student balance
- View reports

### 4. Simple Permission Matrix

| Action | Student | Parent | Teacher | Admin |
| --- | --- | --- | --- | --- |
| Browse courses | Yes | Yes | Yes | Yes |
| Redeem code | Yes | Yes | No | Manage |
| Enroll in course | Yes | For student | No | Support |
| Watch lessons | Yes | No | Own courses | Support |
| View progress | Own | Linked student | Own courses | All |
| Create course | No | No | Yes | Support |
| Approve course | No | No | No | Yes |
| Generate codes | No | No | No | Yes |

### 5. Main Relationships

- One parent can link to one or more students.
- Parent links to student using student ID.
- One teacher can create many courses.
- Teachers are individual users in MVP.
- One student can enroll in many courses.
- One prepaid code can be redeemed for one student only.
- Prepaid codes have serial numbers and do not expire.
- Admin approves teachers and courses.

### 6. Confirmed Decisions

1. Students can register without parent approval.
2. A parent cannot redeem one code for multiple students.
3. Teacher sets course price, and admin can edit it.


---

## 04-business-requirements

## E-Learning Website - Business Requirements

### 1. Purpose

This document lists the main business requirements for the e-learning website MVP.

It explains what the business needs the system to support, without going into detailed technical design.

### 2. Product Scope

The MVP is an Arabic-first e-learning website for Egyptian secondary school students, parents, teachers, and admins.

The platform supports Secondary 1, Secondary 2, and Secondary 3.

### 3. Business Requirements

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

### 4. Business Rules

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
| R-18 | Assessment and grading scope follows the Assessment Management and Grading Management module documents. |
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
| R-34 | Quiz retry is allowed in MVP. |
| R-35 | Quiz result affects course progress. |
| R-36 | MVP reports include codes, enrollments, teacher sales, and student progress. |
| R-37 | MVP payment uses prepaid codes and student balance only; payment gateway is future scope. |

### 5. Out of Scope

The MVP does not include:

- Mobile app
- Live classes
- Chat or forums
- AI recommendations
- Certificates
- English interface
- Subject bundles
- Direct online payment gateway
- Subscriptions and invoices
- Free course enrollment
- Course archive/delete/restore lifecycle
- Notifications
- Attendance tracking
- Advanced video protection such as watermarking
- Parent-student link approval workflow

### 6. Open Questions

No open business requirement questions for now.

### 7. Next Document

The next document should be the Functional Requirements / SRS. It will explain what each system module must do in more detail.


---

## 05-functional-requirements-srs

## E-Learning Website - Functional Requirements / SRS

### 1. Purpose

This document describes the main system functions needed for the MVP.

### 2. System Modules

The system is divided into these business modules:

Detailed module documents 08 to 12 are planned for Phase 2. MVP still includes prepaid code and student balance rules under Payment & Subscription Management.

- Payment & Subscription Management
- Notification Management
- Parent Portal
- Reporting & Analytics
- Administration

#### 2.1 Identity & Access Management

Description: Handles authentication, user accounts, roles, and authorization.

Responsibilities:

- User registration
- Login/logout
- Role management: Student, Teacher, Admin, Parent
- Access control using RBAC

#### 2.2 Teacher Management

Description: Manages teacher profiles and their lifecycle within the platform.

Responsibilities:

- Teacher onboarding
- Profile management
- Verification
- Linking teachers to courses

#### 2.3 Student Management

Description: Manages student accounts and learning activity.

Responsibilities:

- Student registration
- Profile management
- Activity tracking
- Course associations

#### 2.4 Content & Course Management

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

#### 2.5 Enrollment Management

Description: Handles student enrollment in courses.

Responsibilities:

- Enroll students in courses
- Cancel enrollment
- Track enrollment status

Key entities:

- Enrollment

#### 2.6 Assessment Management

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

#### 2.7 Grading Management

Description: Handles evaluation and grading of student submissions.

Responsibilities:

- Grade exams
- Calculate scores
- Generate results

Key entities:

- Grade
- Result

#### 2.8 Payment & Subscription Management

Description: Handles prepaid codes and student balance in MVP. Payment gateway, subscriptions, and invoices are future scope.

Responsibilities:

- Generate prepaid codes
- Delete prepaid codes
- Manage student balance

Key entities:

- Prepaid Code
- Payment

#### 2.9 Notification Management

Description: Future scope. Handles all system notifications.

Responsibilities:

- Email notifications
- In-app notifications
- Alerts and reminders

#### 2.10 Parent Portal

Description: Provides parents with visibility into student progress.

Responsibilities:

- Track student performance
- View results
- Monitor activity

#### 2.11 Reporting & Analytics

Description: Provides business intelligence and system analytics.

Responsibilities:

- Student performance reports
- Teacher performance reports
- Platform KPIs

#### 2.12 Administration

Description: System-wide administration and configuration.

Responsibilities:

- User management
- System monitoring
- Platform configuration

### 3. Functional Requirements

#### 3.1 Identity & Access Management

| ID | Requirement |
| --- | --- |
| FR-01 | Users can log in and log out. |
| FR-02 | Students can create accounts. |
| FR-03 | Parents can create accounts. |
| FR-04 | Teachers can have accounts approved by admin. |
| FR-05 | Users can update basic profile information. |
| FR-05A | Students can register without parent approval. |
| FR-05B | Teacher approval data includes name, phone, subject, bio, profile image, and documents. |

#### 3.2 Course Catalog

| ID | Requirement |
| --- | --- |
| FR-06 | Students can browse published courses. |
| FR-07 | Students can filter courses by secondary year, subject, term, chapter, and teacher. |
| FR-08 | Students can view course details before enrollment. |
| FR-09 | Course details show teacher, price, description, lessons, and subject information. |

#### 3.3 Content & Course Management

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

#### 3.4 Payment & Subscription Management

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

#### 3.5 Enrollment Management

| ID | Requirement |
| --- | --- |
| FR-21 | Students can enroll in a paid course after successful payment/code redemption. |
| FR-22 | Students can access only courses they are enrolled in. |
| FR-23 | Students buy teacher courses separately. |
| FR-24 | The system must prevent access to unpublished courses. |

#### 3.6 Assessment and Grading Management

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

#### 3.7 Parent Portal

| ID | Requirement |
| --- | --- |
| FR-30 | Parents can link to student accounts. |
| FR-31 | Parents can view linked student enrollments. |
| FR-32 | Parents can view linked student progress. |
| FR-33 | Parents can redeem prepaid codes for one linked student at a time. |
| FR-33A | Parent links to student using student ID. |

#### 3.8 Administration

| ID | Requirement |
| --- | --- |
| FR-34 | Admin can manage users. |
| FR-35 | Admin can manage teachers. |
| FR-36 | Admin can manage secondary years, subjects, terms, and chapters. |
| FR-37 | Admin can manage course approval status. |
| FR-38 | Admin can manage prepaid codes. |

#### 3.9 Reporting & Analytics

| ID | Requirement |
| --- | --- |
| FR-39 | Admin can view course enrollment reports. |
| FR-40 | Admin can view prepaid code reports. |
| FR-41 | Teachers can view reports for their own courses. |
| FR-43 | Admin can view teacher sales reports. |
| FR-44 | Admin can view student progress reports. |

### 4. Basic Non-Functional Requirements

| ID | Requirement |
| --- | --- |
| NFR-01 | The website must support Arabic layout and content. |
| NFR-02 | The website must work on mobile and desktop browsers. |
| NFR-03 | User data must be protected by login and role permissions. |
| NFR-04 | Video playback should be stable for students. |
| NFR-05 | The system should record important admin actions. |

### 5. Open Questions

No open functional requirement questions for now.

### 6. Next Document

The next document should be User Stories and Acceptance Criteria.


---

## 06-user-stories-and-acceptance-criteria

## E-Learning Website - User Stories and Acceptance Criteria

### 1. Purpose

This document converts the module documents into user stories that the software team can use for planning and implementation.

Stories are ordered by system module.

### 2. Scope Note

- MVP stories are planned for the first release.
- Future stories are documented for learning and later phases, but they are not required for MVP implementation.

### 3. Module 01 - Identity & Access Management

#### US-IM-01: Student Registration

As a student, I want to register so that I can use the platform.

Acceptance Criteria:

- Student enters required registration data.
- System rejects duplicate phone or email.
- Account is created successfully.
- Student can log in after registration.

#### US-IM-02: Parent Registration

As a parent, I want to register so that I can follow my child.

Acceptance Criteria:

- Parent enters required registration data.
- Account is created successfully.
- Parent can log in.

#### US-IM-03: Teacher Account Approval

As a teacher, I want my account approved so that I can create courses.

Acceptance Criteria:

- Teacher submits required profile data and documents.
- Admin can approve or reject the teacher.
- Rejected teacher cannot publish courses.

#### US-IM-04: Admin User Management

As an admin, I want to manage user accounts so that platform access is controlled.

Acceptance Criteria:

- Admin can view users.
- Admin can update user status.
- Admin can approve teachers.
- Admin actions are recorded for audit.

### 4. Module 02 - Teacher Management

#### US-TM-01: Complete Teacher Profile

As a teacher, I want to complete my profile and upload documents so that I can get verified.

Acceptance Criteria:

- Teacher enters bio, contact info, subject, and profile image.
- Teacher uploads required verification documents.
- System saves the data and sets teacher status to pending approval.

#### US-TM-02: Edit Teacher Profile

As a teacher, I want to edit my profile so that my information stays up to date.

Acceptance Criteria:

- Teacher can update bio, profile image, and contact information.
- Changes are saved successfully.
- Changes to teaching subjects require re-verification.

#### US-TM-03: Review Teacher Application

As an admin, I want to review pending teacher applications so that I can verify their credentials.

Acceptance Criteria:

- Admin can view pending teacher applications.
- Admin can open teacher profile details and uploaded documents.
- Admin can approve or reject the application.

#### US-TM-04: Reject Teacher With Reason

As an admin, I want to reject a teacher with a reason so that the teacher knows what to fix.

Acceptance Criteria:

- Admin must enter a rejection reason.
- Teacher status becomes rejected.
- Rejection reason is saved.

#### US-TM-05: Suspend Teacher Account

As an admin, I want to suspend a teacher account so that a blocked teacher cannot continue teaching.

Acceptance Criteria:

- Admin can change teacher status to suspended.
- Suspended teacher cannot create new courses.
- New enrollments are blocked for suspended teacher courses.
- Existing enrolled students keep access.

#### US-TM-06: Prevent Duplicate Teacher Accounts

As a teacher, I want my National ID and phone to be unique so that duplicate accounts are prevented.

Acceptance Criteria:

- System validates National ID uniqueness.
- System validates phone uniqueness.
- Duplicate registration is rejected with an error message.

#### US-TM-07: Create Courses for Verified Subjects

As a teacher, I want to create courses only for subjects I am verified in so that I teach within my expertise.

Acceptance Criteria:

- Teacher sees only verified subjects during course creation.
- System blocks course creation for unverified subjects.

### 5. Module 03 - Student Management

#### US-SM-01: Update Student Profile

As a student, I want to update my profile so that my academic data is correct.

Acceptance Criteria:

- Student can update allowed profile fields.
- System saves the updated data.
- Student cannot change restricted administrative fields.

#### US-SM-02: View Enrolled Courses

As a student, I want to view my enrolled courses so that I can continue learning.

Acceptance Criteria:

- Student dashboard shows enrolled courses.
- Each course shows status and progress.
- Student can open an active enrolled course.

#### US-SM-03: Track Student Progress

As a student, I want to track my progress so that I know my completion status.

Acceptance Criteria:

- Progress updates after lesson completion.
- Automatic completion happens after watching 90% of the video.
- Student can see progress percentage or completion status.

#### US-SM-04: Parent Monitors Student Progress

As a parent, I want to monitor my child's progress so that I can support learning.

Acceptance Criteria:

- Parent can view only linked student data.
- Parent can view enrolled courses and progress.
- Parent cannot modify student academic data.

#### US-SM-05: Admin Manages Student Records

As an admin, I want to manage student records so that data remains accurate.

Acceptance Criteria:

- Admin can view student accounts.
- Admin can update allowed student account data.
- Admin can deactivate student accounts if needed.

#### US-SM-06: Record Attendance - Future

As a teacher, I want to record attendance so that student participation is tracked.

Acceptance Criteria:

- Teacher can mark attendance for own course sessions.
- Attendance is stored for reports.
- This story is future scope, not MVP.

#### US-SM-07: Student Notifications - Future

As a student, I want to receive course notifications so that I do not miss updates.

Acceptance Criteria:

- System can notify students about course updates and schedules.
- This story is future scope, not MVP.

### 6. Module 04 - Content & Course Management

#### US-CM-01: Create Course Draft

As a teacher, I want to create a course draft so that I can prepare my curriculum before publishing.

Acceptance Criteria:

- Teacher can enter course title, description, price, year, subject, term, and chapter.
- Course is saved with draft status.
- Draft course is visible only to the teacher and admin.

#### US-CM-02: Organize Course Structure

As a teacher, I want to organize my course into subjects, modules, and lessons so that content is easy to follow.

Acceptance Criteria:

- Teacher can add, edit, reorder, and remove structure items.
- Lesson belongs to a module.
- Module belongs to a subject.
- Subject belongs to a course.

#### US-CM-03: Upload Learning Materials

As a teacher, I want to upload educational materials so that students can access learning resources.

Acceptance Criteria:

- Teacher can upload videos and documents.
- Uploaded content is linked to lessons.
- Enrolled students can access content after course publication.

#### US-CM-04: Submit Course for Review

As a teacher, I want my course to be reviewed before publishing so that it complies with platform rules.

Acceptance Criteria:

- Teacher can submit a complete course for review.
- Course status changes to pending approval.
- Admin can approve or reject the course.

#### US-CM-05: Publish Course

As an admin, I want to publish approved courses so that students can enroll in them.

Acceptance Criteria:

- Approved course becomes visible in the course catalog.
- Unapproved course remains hidden from students.
- Students can view course details before enrollment.

#### US-CM-06: Browse Courses

As a student, I want to browse available courses so that I can find suitable learning content.

Acceptance Criteria:

- Student can view published courses only.
- Student can search or filter by curriculum data and teacher.
- Student can open course details and syllabus.

#### US-CM-07: Access Enrolled Course Content

As a student, I want to access enrolled courses so that I can study the learning materials.

Acceptance Criteria:

- Student can access content only for enrolled courses.
- Unenrolled student can view course information only.
- Video content is not directly downloadable.

#### US-CM-08: Lesson Quiz Progression

As a student, I want to complete a lesson quiz so that my progress can be recorded.

Acceptance Criteria:

- Student can submit lesson quiz answers.
- System calculates score according to assessment rules.
- Score is shown to the student.
- Quiz retry is allowed in MVP.

#### US-CM-09: Archive/Delete/Restore Course - Future

As a teacher, I want to archive, delete, or restore courses so that I can manage course lifecycle.

Acceptance Criteria:

- Archived courses do not accept new enrollments.
- Deleted courses are soft deleted and auditable.
- This story is future scope, not MVP.

#### US-CM-10: Free Course Enrollment - Future

As a student, I want to enroll in free courses so that I can learn without payment.

Acceptance Criteria:

- Student can enroll without balance deduction.
- Enrollment is created with no payment reference.
- This story is future scope, not MVP.

### 7. Module 05 - Enrollment Management

#### US-EM-01: Enroll in Paid Course

As a student, I want to enroll in a paid course after using my balance so that I can access its content.

Acceptance Criteria:

- Student has enough balance.
- Course is published.
- Student balance is reduced by course price.
- Enrollment status becomes active.
- Course appears in student dashboard.

#### US-EM-02: Prevent Duplicate Enrollment

As a student, I want to be prevented from enrolling twice in the same course so that I do not pay twice.

Acceptance Criteria:

- System checks existing enrollments before purchase.
- Duplicate enrollment is blocked.
- Student receives a clear error message.

#### US-EM-03: Enrollment Access Control

As the system, I want to allow content access only for active enrollments so that paid content is protected.

Acceptance Criteria:

- Active enrolled student can access course content.
- Unenrolled student cannot access paid lessons.
- Access check is enforced on every content request.

#### US-EM-04: View Enrolled Students

As a teacher, I want to see students enrolled in my courses so that I can understand my audience.

Acceptance Criteria:

- Teacher can view enrolled students for own courses.
- Teacher can view enrollment date and progress.
- Teacher cannot edit or delete enrollment records.

#### US-EM-05: Preserve Access When Teacher Is Suspended

As the system, I want to preserve existing enrollments when a teacher is suspended so that students' learning is not disrupted.

Acceptance Criteria:

- New enrollments are blocked for suspended teacher courses.
- Existing enrollments remain active.
- Existing students retain course access.

#### US-EM-06: Mark Enrollment Completed

As the system, I want to mark enrollments as completed when students finish the course so that completion can be tracked.

Acceptance Criteria:

- Enrollment becomes completed when course completion rules are met.
- Progress is updated correctly.
- Completion is visible in student and teacher views.

#### US-EM-07: Manual Refund Handling

As an admin, I want to handle eligible refunds manually so that support cases can be resolved.

Acceptance Criteria:

- Refund is allowed only if the student has not used the course.
- Admin can reset student balance to 0.
- Money return is handled manually outside the system.
- Refund action is logged.

#### US-EM-08: Advanced Refund Workflow - Future

As an admin, I want to review pending refund requests so that refund policy can be controlled automatically.

Acceptance Criteria:

- System supports pending refund status.
- Admin can approve or reject refund requests.
- This story is future scope, not MVP.

### 8. Module 06 - Assessment Management

#### US-AM-01: Create Exam

As a teacher, I want to create an exam so that I can evaluate student knowledge.

Acceptance Criteria:

- Teacher enters exam details.
- Exam is saved successfully.
- Exam appears in teacher dashboard.

#### US-AM-02: Create Quiz

As a teacher, I want to create a quiz so that students can check their understanding.

Acceptance Criteria:

- Teacher enters quiz details.
- Quiz is linked to a course or lesson.
- Quiz is saved successfully.

#### US-AM-03: Add Questions

As a teacher, I want to add questions to an assessment so that students can answer them.

Acceptance Criteria:

- Teacher can create questions.
- Questions are linked to the assessment.
- Assessment cannot be published without at least one question.

#### US-AM-04: Publish Assessment

As a teacher, I want to publish an assessment so that enrolled students can take it.

Acceptance Criteria:

- Assessment has required questions and grading rule.
- Published assessment becomes available to eligible enrolled students.
- Active published assessment cannot be modified in a way that breaks existing attempts.

#### US-AM-05: Submit Assessment Answers

As a student, I want to take quizzes and exams so that I can evaluate my learning progress.

Acceptance Criteria:

- Student can access assessments assigned to enrolled courses.
- Student can submit answers within the allowed time window.
- System records the attempt and completion status.
- Quiz retry is allowed in MVP.

#### US-AM-06: Review Submissions

As a teacher, I want to review submissions so that I can evaluate student performance.

Acceptance Criteria:

- Teacher can view submissions for own assessments.
- Teacher can add grades and feedback where manual review is needed.

#### US-AM-07: View Assessment Results

As a parent, I want to view my child's assessment results so that I can monitor academic performance.

Acceptance Criteria:

- Parent can view results for linked students only.
- Parent has read-only access.

#### US-AM-08: Assessment Notifications - Future

As a student, I want to receive assessment deadline reminders so that I do not miss exams.

Acceptance Criteria:

- System can notify students about upcoming assessments and deadlines.
- This story is future scope, not MVP.

### 9. Module 07 - Grading Management

#### US-GM-01: Automatic Objective Grading

As a student, I want objective questions to be graded automatically so that I can receive results quickly.

Acceptance Criteria:

- System grades objective questions automatically.
- Score does not exceed maximum score.
- Result is stored after grading.

#### US-GM-02: Manual Essay Grading

As a teacher, I want to grade essay answers manually so that subjective answers are evaluated correctly.

Acceptance Criteria:

- Teacher can assign and save scores.
- Teacher can grade only assessments belonging to own courses.
- Grading action is logged.

#### US-GM-03: Generate Result

As the system, I want to generate results after grading so that student performance is recorded.

Acceptance Criteria:

- Result is generated only after grading is complete.
- System calculates score, percentage, and pass/fail status.
- Result is hidden until published.

#### US-GM-04: Publish Results

As a teacher, I want to publish results so that students can view approved grades.

Acceptance Criteria:

- Teacher can review draft results.
- Teacher can publish results.
- Students can view only published results.

#### US-GM-05: Modify Result With Reason

As a teacher, I want to modify results with a reason so that corrections are auditable.

Acceptance Criteria:

- Teacher must enter modification reason.
- System recalculates result after modification.
- Modification is saved in audit log.

#### US-GM-06: Student Views Results

As a student, I want to view my published results so that I can monitor my learning progress.

Acceptance Criteria:

- Student can view only own published results.
- Result shows score, percentage, and pass/fail status.

#### US-GM-07: Parent Views Grades

As a parent, I want to view my child's grades so that I can monitor academic performance.

Acceptance Criteria:

- Parent can view grades for linked students only.
- Parent can view exam grades, quiz scores, pass/fail status, and overall course grade.
- Parent cannot modify grade data.

#### US-GM-08: Admin Monitors Grading

As an admin, I want to monitor grading actions so that grading changes are auditable.

Acceptance Criteria:

- Admin can view grading audit information.
- Audit log shows action, actor, date, and reason where applicable.

#### US-GM-09: Result Notifications - Future

As a student, I want to receive a notification when final results are generated so that I know when to check grades.

Acceptance Criteria:

- System can notify students after final result generation.
- This story is future scope, not MVP.

### 10. Phase 2 Modules

The following module documents are planned for Phase 2 and will need their own user stories later:

- Module 08 - Payment & Subscription Management
- Module 09 - Notification Management
- Module 10 - Parent Portal
- Module 11 - Reporting & Analytics
- Module 12 - Administration


---

## 08-product-backlog

## E-Learning Website - Product Backlog

### 1. Purpose

This document lists the main product backlog items and links them to the module-ordered user stories in document 06.

### 2. Priority Levels

| Priority | Meaning |
| --- | --- |
| Must Have | Required for MVP |
| Should Have | Important, but can be delayed if needed |
| Later | Not part of MVP |

### 3. MVP Backlog by Module

| ID | Module | Feature | Story Reference | Priority |
| --- | --- | --- | --- | --- |
| PB-01 | Identity & Access Management | Student registration/login | US-IM-01 | Must Have |
| PB-02 | Identity & Access Management | Parent registration/login | US-IM-02 | Must Have |
| PB-03 | Identity & Access Management | Teacher account approval | US-IM-03 | Must Have |
| PB-04 | Identity & Access Management | Admin user management | US-IM-04 | Must Have |
| PB-05 | Teacher Management | Complete teacher profile | US-TM-01 | Must Have |
| PB-06 | Teacher Management | Edit teacher profile | US-TM-02 | Must Have |
| PB-07 | Teacher Management | Review teacher application | US-TM-03 | Must Have |
| PB-08 | Teacher Management | Reject teacher with reason | US-TM-04 | Must Have |
| PB-09 | Teacher Management | Suspend teacher account | US-TM-05 | Should Have |
| PB-10 | Teacher Management | Prevent duplicate teacher accounts | US-TM-06 | Must Have |
| PB-11 | Teacher Management | Create courses for verified subjects | US-TM-07 | Must Have |
| PB-12 | Student Management | Update student profile | US-SM-01 | Must Have |
| PB-13 | Student Management | View enrolled courses | US-SM-02 | Must Have |
| PB-14 | Student Management | Track student progress | US-SM-03 | Must Have |
| PB-15 | Student Management | Parent monitors student progress | US-SM-04 | Must Have |
| PB-16 | Student Management | Admin manages student records | US-SM-05 | Should Have |
| PB-17 | Content & Course Management | Create course draft | US-CM-01 | Must Have |
| PB-18 | Content & Course Management | Organize course structure | US-CM-02 | Must Have |
| PB-19 | Content & Course Management | Upload learning materials | US-CM-03 | Must Have |
| PB-20 | Content & Course Management | Submit course for review | US-CM-04 | Must Have |
| PB-21 | Content & Course Management | Publish course | US-CM-05 | Must Have |
| PB-22 | Content & Course Management | Browse courses | US-CM-06 | Must Have |
| PB-23 | Content & Course Management | Access enrolled course content | US-CM-07 | Must Have |
| PB-24 | Content & Course Management | Lesson quiz progression | US-CM-08 | Must Have |
| PB-25 | Enrollment Management | Enroll in paid course | US-EM-01 | Must Have |
| PB-26 | Enrollment Management | Prevent duplicate enrollment | US-EM-02 | Must Have |
| PB-27 | Enrollment Management | Enrollment access control | US-EM-03 | Must Have |
| PB-28 | Enrollment Management | View enrolled students | US-EM-04 | Must Have |
| PB-29 | Enrollment Management | Preserve access when teacher is suspended | US-EM-05 | Should Have |
| PB-30 | Enrollment Management | Mark enrollment completed | US-EM-06 | Must Have |
| PB-31 | Enrollment Management | Manual refund handling | US-EM-07 | Should Have |
| PB-32 | Assessment Management | Create exam | US-AM-01 | Must Have |
| PB-33 | Assessment Management | Create quiz | US-AM-02 | Must Have |
| PB-34 | Assessment Management | Add questions | US-AM-03 | Must Have |
| PB-35 | Assessment Management | Publish assessment | US-AM-04 | Must Have |
| PB-36 | Assessment Management | Submit assessment answers | US-AM-05 | Must Have |
| PB-37 | Assessment Management | Review submissions | US-AM-06 | Should Have |
| PB-38 | Assessment Management | View assessment results | US-AM-07 | Must Have |
| PB-39 | Grading Management | Automatic objective grading | US-GM-01 | Must Have |
| PB-40 | Grading Management | Manual essay grading | US-GM-02 | Should Have |
| PB-41 | Grading Management | Generate result | US-GM-03 | Must Have |
| PB-42 | Grading Management | Publish results | US-GM-04 | Must Have |
| PB-43 | Grading Management | Modify result with reason | US-GM-05 | Should Have |
| PB-44 | Grading Management | Student views results | US-GM-06 | Must Have |
| PB-45 | Grading Management | Parent views grades | US-GM-07 | Must Have |
| PB-46 | Grading Management | Admin monitors grading | US-GM-08 | Should Have |
| PB-47 | Payment & Subscription Management | Prepaid code generation | Module 08 story to add | Must Have |
| PB-48 | Payment & Subscription Management | Prepaid code redemption | Module 08 story to add | Must Have |
| PB-49 | Payment & Subscription Management | Student balance management | Module 08 story to add | Must Have |
| PB-50 | Reporting & Analytics | Basic code, enrollment, sales, and progress reports | Module 11 story to add | Must Have |

### 4. Future Backlog

| ID | Feature | Story Reference | Reason |
| --- | --- | --- | --- |
| L-01 | Record attendance | US-SM-06 | Future scope |
| L-02 | Student/course notifications | US-SM-07 | Future scope |
| L-03 | Archive/delete/restore course lifecycle | US-CM-09 | Future scope |
| L-04 | Free course enrollment | US-CM-10 | Future scope |
| L-05 | Advanced refund workflow | US-EM-08 | Future scope |
| L-06 | Assessment notifications | US-AM-08 | Future scope |
| L-07 | Result notifications | US-GM-09 | Future scope |
| L-08 | Direct online payment gateway | Module 08 future story | MVP uses prepaid codes |
| L-09 | Subscriptions and invoices | Module 08 future story | Not needed for prepaid-code MVP |
| L-10 | Mobile app | Future story | Not needed for first web MVP |
| L-11 | Live classes | Future story | Adds complexity |
| L-12 | Chat/community | Future story | Can be added after learning flow works |
| L-13 | Certificates | Future story | Not important for school-course MVP |
| L-14 | Subject bundles | Future story | Current scope is separate teacher course purchase |
| L-15 | English interface | Future story | Arabic launches first |
| L-16 | Video watermarking | Future story | No-download is MVP protection |

### 5. Suggested Build Order

1. Identity & Access Management
2. Teacher Management
3. Student Management basics
4. Content & Course Management
5. Payment enablers: prepaid codes and student balance
6. Enrollment Management
7. Video lessons and progress tracking
8. Assessment Management
9. Grading Management
10. Parent progress and grade views
11. Basic reports


---

## 11-screen-list

## E-Learning Website - Screen List

### 1. Purpose

This document lists the main MVP screens and maps them to the module-ordered user stories in document 06.

It helps UI/UX and frontend teams understand what pages should exist.

### 2. Public and Identity Screens

| Screen | User | Related Stories | Purpose | Main Actions |
| --- | --- | --- | --- | --- |
| Home Page | Guest | US-CM-06 | Introduce platform and show course entry points | View courses, register, log in |
| Login | All users | US-IM-01, US-IM-02 | Access account | Enter credentials |
| Student Register | Student | US-IM-01 | Create student account | Submit registration form |
| Parent Register | Parent | US-IM-02 | Create parent account | Submit registration form |
| Course Catalog | Guest/Student/Parent | US-CM-06 | Browse available courses | Search, filter, open course |
| Course Details | Guest/Student/Parent | US-CM-06, US-EM-01 | View course information | View price, teacher, lessons, enroll |

### 3. Student Management Screens

| Screen | Related Stories | Purpose | Main Actions |
| --- | --- | --- | --- |
| Student Dashboard | US-SM-02, US-SM-03 | Show student learning summary | View enrolled courses, balance, progress |
| Student Profile | US-SM-01 | Manage student profile | Update allowed profile data |
| My Courses | US-SM-02, US-EM-01 | Show enrolled courses | Open course |
| Progress Page | US-SM-03 | View learning progress | View completed lessons and assessment progress |

### 4. Payment and Enrollment Screens

| Screen | Related Stories | Purpose | Main Actions |
| --- | --- | --- | --- |
| Redeem Code | Module 08 story to add | Add value to student balance | Enter prepaid code |
| Course Purchase | US-EM-01, US-EM-02 | Buy course using balance | Confirm purchase |
| Lesson Player | US-CM-07, US-EM-03 | Watch course lessons | Play video, mark lesson complete |

### 5. Assessment and Grading Screens

| Screen | Related Stories | Purpose | Main Actions |
| --- | --- | --- | --- |
| Assessment Page | US-AM-05, US-CM-08 | Solve assessment/quiz | Select answers, submit, view score |
| Student Results | US-GM-06 | View published results | View score, percentage, pass/fail status |

### 6. Parent Screens

| Screen | Related Stories | Purpose | Main Actions |
| --- | --- | --- | --- |
| Parent Dashboard | US-SM-04 | Show linked students | View students and progress |
| Link Student | US-SM-04 | Connect parent to student | Enter student ID |
| Parent Redeem Code | Module 08 story to add | Add value to linked student balance | Select student, enter code |
| Student Progress View | US-SM-04 | Monitor student learning | View courses, lessons, progress |
| Student Grades View | US-AM-07, US-GM-07 | Monitor academic performance | View assessment results and grades |

### 7. Teacher Screens

| Screen | Related Stories | Purpose | Main Actions |
| --- | --- | --- | --- |
| Teacher Dashboard | US-TM-01, US-EM-04 | Show teacher summary | View courses, enrollments, results |
| Teacher Profile | US-TM-01, US-TM-02 | Manage teacher information | Edit name, phone, subject, bio, image, documents |
| Course List | US-CM-01 | Manage teacher courses | View, create, edit courses |
| Course Editor | US-CM-01, US-CM-02, US-CM-03 | Create or edit course | Set course data, structure, lessons, materials |
| Course Review Submission | US-CM-04 | Submit course for approval | Submit complete course |
| Course Students | US-EM-04 | View enrolled students | View student progress |
| Assessment Management | US-AM-01, US-AM-02, US-AM-03, US-AM-04 | Manage assessments/quizzes | Create, add questions, publish |
| Submission Review | US-AM-06, US-GM-02 | Review and grade submissions | Add grades and feedback |
| Result Publishing | US-GM-03, US-GM-04, US-GM-05 | Manage results | Review, publish, modify with reason |

### 8. Admin Screens

| Screen | Related Stories | Purpose | Main Actions |
| --- | --- | --- | --- |
| Admin Dashboard | US-IM-04 | Show platform summary | View users, courses, codes, reports |
| User Management | US-IM-04, US-SM-05 | Manage users | View, update, deactivate users |
| Teacher Approval | US-IM-03, US-TM-03, US-TM-04, US-TM-05 | Approve teachers | Review teacher data, approve/reject/suspend |
| Course Approval | US-CM-05 | Approve courses | Review course, approve/reject |
| Curriculum Management | US-CM-01, US-CM-02 | Manage curriculum data | Add/edit years, subjects, terms, chapters |
| Prepaid Code Management | Module 08 story to add | Manage prepaid codes | Generate, cancel, track codes |
| Student Balance Management | Module 08 story to add, US-EM-07 | Manage balances | Add/subtract balance, reset for refund |
| Grading Audit | US-GM-08 | Monitor grading actions | View grading audit log |
| Reports | Module 11 story to add | View platform reports | View codes, enrollments, teacher sales, student progress |
| Settings | Future story | Manage basic platform settings | Update simple system settings |

### 9. Future Screens

| Screen | Related Stories | Reason |
| --- | --- | --- |
| Attendance Management | US-SM-06 | Future scope |
| Notifications Center | US-SM-07, US-AM-08, US-GM-09 | Future scope |
| Course Archive/Delete/Restore | US-CM-09 | Future scope |
| Free Course Enrollment | US-CM-10 | Future scope |
| Advanced Refund Requests | US-EM-08 | Future scope |

### 10. Notes

- These are MVP screens plus clearly marked future screens.
- Detailed wireframes can be created later from this list.
- Mobile app screens are not included in MVP.

