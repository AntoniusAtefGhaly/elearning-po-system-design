# E-Learning Platform Backlog Structure

## Project: Learning Management System (LMS)

This backlog uses a small number of business-focused epics. Technical foundation, security, testing, and operations are included as enabling features inside the business epics.

## Backlog Hierarchy

```text
Project
└── Epic
    └── Feature
        └── User Story
            ├── FE Task
            ├── BE Task
            └── QA Task
```

---

## Epic 1: Platform Access and User Administration

### Business Objective

Enable students, parents, teachers, and administrators to access the LMS securely and manage their accounts, profiles, roles, and academic master data.

### Feature 1.1: LMS Technical Foundation

#### User Story: Establish the LMS Application Foundation

**FE Tasks**

- Create the frontend application and module structure.
- Configure routing, environments, state management, and API communication.
- Create the shared Arabic RTL application layout.
- Create shared form, table, dialog, loading, empty, and error components.
- Configure frontend validation and error handling.
- Configure frontend unit and component testing.

**BE Tasks**

- Create the Clean Architecture solution.
- Create Domain, Application, Infrastructure, API, Resources, Database, and test projects.
- Configure project references and dependency injection.
- Configure MediatR, validation, mapping, localization, and common result models.
- Configure the application database and initial migration.
- Configure logging, correlation IDs, exception handling, Swagger, CORS, and health checks.
- Configure backend unit and integration testing.

**QA Tasks**

- Define the LMS test strategy and defect workflow.
- Define test entry and exit criteria.
- Verify that FE and BE applications build and run.
- Verify database creation and migration execution.
- Verify Arabic RTL behavior on supported browsers.

### Feature 1.2: Registration and Authentication

#### User Story: Register and Sign In as an LMS User

**FE Tasks**

- Create student registration.
- Create parent registration.
- Create login and logout.
- Handle invalid credentials and expired sessions.
- Create unauthorized and access-denied pages.

**BE Tasks**

- Implement student and parent registration.
- Configure authentication and secure session handling.
- Implement login, logout, and current-user services.
- Prevent duplicate accounts.
- Record important authentication events.

**QA Tasks**

- Test student and parent registration.
- Test valid and invalid login.
- Test duplicate registration.
- Test logout and expired sessions.
- Test disabled and suspended accounts.

### Feature 1.3: Roles and Permissions

#### User Story: Access LMS Functions According to User Role

**FE Tasks**

- Add role-based route guards.
- Show or hide actions based on permissions.
- Create role-specific navigation for Student, Parent, Teacher, and Admin.

**BE Tasks**

- Define Student, Parent, Teacher, and Admin roles.
- Define permissions and authorization policies.
- Protect API endpoints and business resources.
- Seed initial roles and permissions.

**QA Tasks**

- Test the permission matrix for every role.
- Test direct URL and API access.
- Test resource ownership restrictions.
- Test permission changes.

### Feature 1.4: Teacher Onboarding and Administration

#### User Story: Apply and Maintain a Teacher Profile

**FE Tasks**

- Create the teacher profile form.
- Support subject, biography, profile image, and document entry.
- Allow teachers to update permitted profile information.
- Display teacher verification status and rejection reason.

**BE Tasks**

- Create and update teacher profiles.
- Store teacher subjects, images, and documents.
- Prevent duplicate teacher accounts.
- Restrict course creation to approved teachers and verified subjects.

**QA Tasks**

- Test complete and incomplete teacher applications.
- Test duplicate teacher prevention.
- Test teacher profile updates.
- Test subject restrictions.

#### User Story: Review and Manage Teacher Applications

**FE Tasks**

- Create the admin teacher-review queue.
- Create teacher application details.
- Add approve, reject, and suspend actions.
- Require a rejection or suspension reason.

**BE Tasks**

- Create teacher application queries.
- Implement approval, rejection, and suspension workflows.
- Store decisions, reasons, users, and timestamps.
- Enforce teacher status in protected operations.

**QA Tasks**

- Test approval, rejection, and suspension.
- Test required reasons.
- Test invalid status transitions.
- Verify decision history.

### Feature 1.5: Student and Parent Profiles

#### User Story: Manage a Student Profile

**FE Tasks**

- Create the student profile page.
- Allow updates to permitted profile fields.
- Create the student dashboard shell.

**BE Tasks**

- Create student profile queries and update commands.
- Enforce editable-field and authorization rules.
- Record profile changes.

**QA Tasks**

- Test student profile retrieval and updates.
- Test invalid data.
- Test unauthorized profile access.

#### User Story: Link a Parent to a Student

**FE Tasks**

- Create the parent dashboard.
- Create the link-student form using student ID.
- Display linked students.

**BE Tasks**

- Implement parent-to-student linking.
- Validate student ID and prevent duplicate links.
- Restrict parent access to linked students.

**QA Tasks**

- Test valid and invalid student links.
- Test duplicate links.
- Test parent access isolation.

### Feature 1.6: Academic Master Data

#### User Story: Manage the LMS Academic Structure

**FE Tasks**

- Create management pages for secondary years, subjects, terms, chapters, and categories.
- Add search, filtering, activation, and deactivation.
- Create reusable lookup selectors.

**BE Tasks**

- Implement CRUD and status management for academic master data.
- Enforce uniqueness and dependency rules.
- Provide lookup APIs for course and reporting modules.
- Add reference-data caching where appropriate.

**QA Tasks**

- Test academic-data creation and updates.
- Test duplicate values.
- Test activation and deactivation.
- Test dependent-data restrictions.

---

## Epic 2: Course Marketplace and Content Lifecycle

### Business Objective

Allow approved teachers to build structured courses, enable administrators to review and publish them, and allow users to discover published courses.

### Feature 2.1: Course Authoring

#### User Story: Create and Maintain a Course Draft

**FE Tasks**

- Create the teacher course list.
- Create course create and edit forms.
- Support title, description, price, subject, year, term, chapter, category, and image.
- Display course lifecycle status.

**BE Tasks**

- Create course commands and queries.
- Enforce teacher approval and verified-subject rules.
- Validate course ownership and editable statuses.
- Allow administrators to edit course prices.
- Record course change history.

**QA Tasks**

- Test draft creation and editing.
- Test ownership and subject restrictions.
- Test course pricing rules.
- Test invalid status updates.

### Feature 2.2: Course Structure and Learning Materials

#### User Story: Organize a Course into Modules and Lessons

**FE Tasks**

- Create the course structure editor.
- Add, edit, reorder, and remove modules and lessons.
- Display content completeness.

**BE Tasks**

- Implement module and lesson management.
- Support ordering and hierarchy validation.
- Prevent invalid deletion of referenced content.

**QA Tasks**

- Test module and lesson operations.
- Test ordering.
- Test invalid hierarchy changes.
- Test ownership restrictions.

#### User Story: Upload Course Learning Materials

**FE Tasks**

- Add video and document upload controls.
- Display upload progress and material metadata.
- Add preview, download, and removal actions where permitted.

**BE Tasks**

- Implement secure media upload and storage.
- Validate file type, size, and ownership.
- Store media metadata.
- Protect learning files from unauthorized access.
- Support non-downloadable video delivery.

**QA Tasks**

- Test allowed and blocked files.
- Test maximum file size.
- Test upload failure recovery.
- Test unauthorized media access.
- Verify video URLs are not directly downloadable.

### Feature 2.3: Course Review and Publishing

#### User Story: Submit a Course for Administrative Review

**FE Tasks**

- Add course completeness validation.
- Add review submission and confirmation.
- Display review status and admin feedback.

**BE Tasks**

- Validate course readiness.
- Implement review submission.
- Prevent edits that conflict with the review workflow.
- Record submission history.

**QA Tasks**

- Test complete and incomplete submissions.
- Test repeated submissions.
- Test status and edit restrictions.

#### User Story: Approve, Reject, and Publish a Course

**FE Tasks**

- Create the admin course-review queue.
- Create the review details page.
- Add approve and reject actions.
- Require rejection feedback.

**BE Tasks**

- Implement approval, rejection, and publication.
- Enforce valid lifecycle transitions.
- Publish only complete approved courses.
- Record reviewer decisions and timestamps.

**QA Tasks**

- Test approval, rejection, and publication.
- Test required rejection feedback.
- Test invalid transitions.
- Verify unpublished courses remain inaccessible.

### Feature 2.4: Course Catalog and Details

#### User Story: Discover Published Courses

**FE Tasks**

- Create the public course catalog.
- Add search and filters for year, subject, term, chapter, and teacher.
- Add sorting and pagination.
- Create responsive course cards and empty states.

**BE Tasks**

- Create the published-course search API.
- Implement filters, sorting, and pagination.
- Exclude draft, rejected, and suspended content.
- Optimize catalog queries.

**QA Tasks**

- Test search and every filter.
- Test combined filters and pagination.
- Verify only published courses are returned.
- Test mobile and desktop layouts.

#### User Story: View Course Details Before Purchase

**FE Tasks**

- Create the course details page.
- Display teacher, price, description, subject, structure, and lesson summary.
- Display enrollment or purchase status.

**BE Tasks**

- Create the public course-details query.
- Return permitted course and teacher information.
- Hide protected lesson content before enrollment.

**QA Tasks**

- Validate course details.
- Test missing and unpublished courses.
- Verify protected content is hidden.

---

## Epic 3: Student Wallet, Purchase, and Enrollment

### Business Objective

Enable administrators to distribute prepaid value, allow students or parents to redeem it, and convert student balance into secure course enrollment.

### Feature 3.1: Prepaid Code Administration

#### User Story: Generate and Manage Prepaid Codes

**FE Tasks**

- Create the prepaid-code management page.
- Add code generation by value and quantity.
- Display serial number, value, status, and redemption information.
- Add cancellation for active codes.

**BE Tasks**

- Generate unique prepaid codes and serial numbers.
- Support active, used, and cancelled statuses.
- Prevent changes to used codes.
- Record generation, distribution, cancellation, and redemption history.
- Ensure prepaid codes do not expire.

**QA Tasks**

- Test code generation and uniqueness.
- Test status transitions.
- Test active-code cancellation.
- Test restrictions for used codes.
- Verify audit history.

### Feature 3.2: Student Balance

#### User Story: Redeem a Prepaid Code for a Student

**FE Tasks**

- Create student code redemption.
- Create parent redemption for a selected linked student.
- Display the updated student balance.
- Display clear invalid-code errors.

**BE Tasks**

- Validate active and unused codes.
- Redeem each code for one student only.
- Add code value to student balance atomically.
- Record redemption history.
- Prevent duplicate and concurrent redemption.

**QA Tasks**

- Test student and parent redemption.
- Test invalid, used, and cancelled codes.
- Test concurrent redemption attempts.
- Verify balance and redemption history.

#### User Story: Administer Student Balance

**FE Tasks**

- Create student balance administration.
- Add manual credit, debit, and reset-to-zero actions.
- Require an adjustment reason.
- Display balance transaction history.

**BE Tasks**

- Implement manual balance adjustments.
- Prevent negative balances.
- Store amount, reason, administrator, and timestamp.
- Support reset-to-zero for manual refund handling.

**QA Tasks**

- Test credit, debit, and reset.
- Test insufficient balance.
- Test required adjustment reasons.
- Verify transaction history.

### Feature 3.3: Paid Course Enrollment

#### User Story: Purchase and Enroll in a Course

**FE Tasks**

- Create the course-purchase confirmation flow.
- Display price, available balance, and resulting balance.
- Display enrollment success and failure states.

**BE Tasks**

- Validate the student, course, publication status, and balance.
- Deduct the course price and create enrollment in one transaction.
- Prevent duplicate enrollment.
- Prevent the balance from becoming negative.
- Record enrollment and wallet transactions.

**QA Tasks**

- Test successful purchase.
- Test insufficient balance.
- Test duplicate enrollment.
- Test unpublished courses.
- Test concurrent purchase attempts.
- Verify transaction consistency.

### Feature 3.4: Enrollment Access and Lifecycle

#### User Story: Access Only Purchased Courses

**FE Tasks**

- Create the student My Courses page.
- Display active and completed enrollments.
- Route students to enrolled course content.
- Display an access-denied state when required.

**BE Tasks**

- Create student enrollment queries.
- Enforce enrollment-based course and media access.
- Preserve purchased access when a teacher is suspended.
- Prevent access to unpublished or unauthorized content.

**QA Tasks**

- Test enrolled and non-enrolled access.
- Test direct API and media access.
- Test teacher suspension behavior.
- Test completed enrollments.

#### User Story: Allow Teachers to View Course Enrollments

**FE Tasks**

- Create the teacher course-student list.
- Display enrollment and progress summaries.
- Add search and filtering.

**BE Tasks**

- Create teacher enrollment queries.
- Restrict results to teacher-owned courses.
- Return student enrollment and progress summaries.

**QA Tasks**

- Test teacher-owned course access.
- Test cross-teacher data isolation.
- Test filtering and pagination.

---

## Epic 4: Learning Delivery, Assessment, and Academic Outcomes

### Business Objective

Deliver purchased learning content, track student progress, assess learning, publish grades, and give students and parents visibility into academic outcomes.

### Feature 4.1: Lesson Delivery and Progress

#### User Story: Learn Through Enrolled Course Lessons

**FE Tasks**

- Create the lesson player.
- Display course navigation and lesson materials.
- Track video playback progress.
- Allow manual lesson completion.
- Automatically request completion after 90% video viewing.

**BE Tasks**

- Provide secure lesson-content access.
- Record video watch progress.
- Record manual and automatic lesson completion.
- Make progress updates idempotent.
- Calculate course progress.

**QA Tasks**

- Test lesson navigation and playback.
- Test manual completion.
- Test automatic completion at 90%.
- Test repeated and out-of-order progress updates.
- Test unauthorized access.

#### User Story: View Student Course Progress

**FE Tasks**

- Create the student progress page.
- Display completed lessons, assessment contribution, and overall percentage.
- Display progress on the student dashboard and My Courses.

**BE Tasks**

- Create student progress queries.
- Calculate lesson and assessment progress.
- Mark enrollment completed according to business rules.

**QA Tasks**

- Validate progress calculations.
- Test partial and complete courses.
- Test enrollment completion.

### Feature 4.2: Assessment Authoring

#### User Story: Create and Publish Course Assessments

**FE Tasks**

- Create teacher assessment management.
- Create exam and quiz forms.
- Add objective and essay questions with answers and scores.
- Add assessment publication controls.

**BE Tasks**

- Implement assessment, question, and answer management.
- Validate total scores and correct-answer rules.
- Restrict assessments to teacher-owned courses.
- Implement assessment publication.
- Prevent unsafe edits after student submissions.

**QA Tasks**

- Test exam and quiz creation.
- Test question types and score validation.
- Test publication requirements.
- Test ownership restrictions.
- Test editing after submissions.

### Feature 4.3: Assessment Participation

#### User Story: Complete a Published Assessment

**FE Tasks**

- Create the student assessment page.
- Display questions and answer controls.
- Save or submit answers according to business rules.
- Display submission confirmation.
- Support quiz retry.

**BE Tasks**

- Validate enrollment and published-assessment access.
- Create assessment attempts and answer submissions.
- Prevent invalid or duplicate final submissions.
- Support quiz retries.
- Record attempt timestamps and status.

**QA Tasks**

- Test objective and essay answers.
- Test unauthorized and unpublished assessment access.
- Test duplicate submission.
- Test quiz retries.
- Test interrupted attempts.

### Feature 4.4: Grading and Result Publishing

#### User Story: Grade Student Assessment Attempts

**FE Tasks**

- Create the teacher submission-review page.
- Display submitted answers.
- Support manual essay grading and feedback.
- Display automatically calculated objective scores.

**BE Tasks**

- Automatically grade objective questions.
- Support manual essay grading.
- Calculate total score, percentage, and pass/fail result.
- Restrict grading to authorized teachers.
- Record grading history.

**QA Tasks**

- Validate automatic grading.
- Test manual grading.
- Test mixed question types.
- Test score boundaries.
- Test grading authorization.

#### User Story: Publish and Correct Assessment Results

**FE Tasks**

- Create result review and publication.
- Allow result correction with a mandatory reason.
- Display publication and correction history.

**BE Tasks**

- Implement result generation and publication.
- Prevent students from viewing unpublished results.
- Support result changes with a required reason.
- Recalculate affected progress.
- Record all grading changes.

**QA Tasks**

- Test result generation and publication.
- Test unpublished-result protection.
- Test result correction.
- Verify audit history and progress recalculation.

### Feature 4.5: Student and Parent Academic Views

#### User Story: View My Learning Results

**FE Tasks**

- Create the student results page.
- Display score, percentage, pass/fail status, feedback, and attempt history.

**BE Tasks**

- Create student result queries.
- Return published results only.
- Restrict data to the authenticated student.

**QA Tasks**

- Test published and unpublished results.
- Test result accuracy.
- Test student data isolation.

#### User Story: Monitor a Linked Student's Learning

**FE Tasks**

- Create parent views for enrollments, progress, and grades.
- Allow switching between linked students.

**BE Tasks**

- Create parent progress and result queries.
- Restrict access to linked students.
- Return published results only.

**QA Tasks**

- Test linked-student progress and grades.
- Test switching between students.
- Test unlinked-student access.

---

## Epic 5: Business Operations, Reporting, and Release

### Business Objective

Give administrators and teachers operational control, reliable business reports, auditability, system monitoring, and a production-ready LMS.

### Feature 5.1: Role-Based Dashboards

#### User Story: View an Operational LMS Dashboard

**FE Tasks**

- Create Admin, Teacher, Student, and Parent dashboards.
- Display role-relevant summaries and quick actions.
- Add loading, empty, and error states.

**BE Tasks**

- Create role-specific dashboard summary APIs.
- Enforce role and ownership restrictions.
- Optimize dashboard queries.

**QA Tasks**

- Validate dashboard values.
- Test every role.
- Test data isolation and performance.

### Feature 5.2: Business Reporting

#### User Story: Analyze LMS Business Performance

**FE Tasks**

- Create reports for course enrollments, prepaid codes, teacher sales, and student progress.
- Add date, teacher, course, subject, and status filters.
- Add pagination and Excel/PDF export.

**BE Tasks**

- Create enrollment, code, sales, and progress report queries.
- Restrict teachers to their own course reports.
- Allow administrators to view platform-wide reports.
- Generate Excel and PDF exports.
- Optimize large report queries.

**QA Tasks**

- Validate report values and totals.
- Test filters and exports.
- Test teacher and administrator access.
- Test large datasets.

### Feature 5.3: Audit and Administrative Oversight

#### User Story: Review Important LMS Actions

**FE Tasks**

- Create audit views for teacher decisions, course decisions, wallet adjustments, code redemption, enrollment, and grading.
- Add search, filters, and pagination.

**BE Tasks**

- Record important business and administrative actions.
- Store user, action, reason, timestamp, and relevant old/new values.
- Protect sensitive information.
- Create secured audit queries.

**QA Tasks**

- Verify all required actions are recorded.
- Verify audit data accuracy and immutability.
- Verify sensitive information is excluded.
- Test audit permissions.

### Feature 5.4: Notifications

#### User Story: Receive Important LMS Notifications

**FE Tasks**

- Create an in-app notification list and unread counter.
- Link notifications to relevant courses, assessments, and results.

**BE Tasks**

- Publish notifications for teacher approval, course review, enrollment, assessment, and result events.
- Create localized notification templates.
- Implement background delivery, retries, and duplicate prevention.

**QA Tasks**

- Test recipients and message content.
- Test Arabic templates.
- Test retries and duplicate prevention.
- Test notification links.

### Feature 5.5: Monitoring and Supportability

#### User Story: Operate and Support the LMS Reliably

**BE Tasks**

- Configure structured logging and correlation IDs.
- Configure application, database, storage, and background-job health checks.
- Add performance metrics and dependency monitoring.
- Filter credentials and personal information from logs.
- Document common support and recovery procedures.

**QA Tasks**

- Test health endpoints and dependency failures.
- Verify error correlation.
- Verify sensitive information is excluded from logs.
- Test recovery scenarios.

### Feature 5.6: CI/CD and Environment Deployment

#### User Story: Build and Deploy the LMS Consistently

**FE Tasks**

- Configure automated frontend build and tests.
- Configure environment-specific builds.
- Publish frontend artifacts.

**BE Tasks**

- Configure automated backend build and tests.
- Configure database migration deployment.
- Configure secrets and environment settings.
- Publish backend artifacts.
- Configure deployment health validation and rollback.

**QA Tasks**

- Define quality gates.
- Execute deployment smoke tests.
- Validate development, QA, and production-like environments.
- Verify rollback.

### Feature 5.7: MVP Release Readiness

#### User Story: Release the LMS MVP

**FE Tasks**

- Resolve critical frontend defects.
- Verify responsive Arabic RTL behavior.
- Verify supported browser compatibility.
- Optimize production assets.

**BE Tasks**

- Resolve critical backend defects.
- Review security, authorization, and dependency vulnerabilities.
- Optimize critical APIs and database queries.
- Verify production configuration and migrations.
- Prepare technical runbooks.

**QA Tasks**

- Complete end-to-end regression testing.
- Complete security and performance testing.
- Validate all MVP business flows.
- Prepare the test report and known-issues list.
- Obtain business release approval.

---

## Epic Summary

| Epic | Main LMS Business Scope |
| --- | --- |
| Epic 1 | Platform foundation, users, roles, teachers, students, parents, and academic master data |
| Epic 2 | Course authoring, content, approval, publishing, catalog, and course details |
| Epic 3 | Prepaid codes, student wallet, purchase, enrollment, and course access |
| Epic 4 | Lesson delivery, progress, assessments, grading, results, and parent monitoring |
| Epic 5 | Dashboards, reports, audit, notifications, monitoring, deployment, and release |

## Work Item Naming Convention

```text
Epic:    EP-03 Student Wallet, Purchase, and Enrollment
Feature: FT-03.03 Paid Course Enrollment
Story:   US-03.03.01 Purchase and Enroll in a Course
Task:    FE-03.03.01 Create Course Purchase Flow
Task:    BE-03.03.02 Implement Transactional Enrollment
Task:    QA-03.03.03 Test Purchase and Enrollment Rules
```

## Backlog Rules

- Epics represent large LMS business outcomes.
- Features represent releasable business capabilities.
- User Stories describe value delivered to a user or administrator.
- FE, BE, and QA Tasks contain implementation and verification work.
- Technical work should be connected to the business feature it enables.
- Every User Story must have acceptance criteria before entering a sprint.
- Each sprint should deliver at least one working vertical slice across FE, BE, and QA.
