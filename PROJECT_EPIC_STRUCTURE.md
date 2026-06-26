# Learning Management System Backlog

## Project: E-Learning Platform

## Structure

```text
Project
└── Epic
    └── Feature / User Story
        └── FE / BE / QA Tasks
```

## Guidelines

- Each LMS module is represented by its own Epic.
- Business user stories come from the `User Stories` section of the documents in `Modules`.
- Original story IDs are shown with their module prefix because some documents reuse the same IDs.
- Features group related stories without splitting the work too deeply.
- FE, BE, and QA tasks are intentionally broad because this is a learning project.
- Technical stories are included only where they establish shared project foundations.

---

# Epic 0: Technical Foundation

## Epic Goal

Create a working technical foundation that allows the team to develop all LMS business modules using consistent architecture, API, UI, database, security, testing, and delivery standards.

---

## Feature 0.1: Solution and Clean Architecture

### TECH-01: Create the Backend Solution Structure

**Technical Story:** As a backend team, we want a Clean Architecture solution so that business modules are separated, testable, and maintainable.

**Acceptance Criteria**

- The solution builds without errors.
- The solution contains API, Application, Domain, Infrastructure, Resources, Database, and test projects.
- Project dependencies follow Clean Architecture rules.
- Business logic does not exist inside API controllers.
- Domain does not depend on Application, Infrastructure, or API.
- Application does not depend on Infrastructure or API.
- Every project has a clear responsibility documented in the project README.

**FE Tasks**

- Review the API project naming and planned module boundaries with the BE team.
- Agree on request, response, pagination, validation-error, and date formats.

**BE Tasks**

- Create the main solution and `src` and `tests` folders.
- Create the Domain project for entities, value objects, enums, and domain rules.
- Create the Application project for use cases, commands, queries, DTOs, validators, and interfaces.
- Create the Infrastructure project for database access, repositories, storage, email, and external services.
- Create the API project for controllers, middleware, filters, and startup configuration.
- Create the Resources project for English and Arabic messages.
- Create a Database project or agreed migration location.
- Create Application and API test projects.
- Configure project references and dependency injection registration.
- Enable nullable reference types and common build settings.
- Add `.editorconfig`, `.gitignore`, and basic coding conventions.
- Add a sample module folder that demonstrates the expected structure.

**QA Tasks**

- Verify that the complete solution restores and builds.
- Verify that invalid project references are not introduced.
- Review the sample module structure with FE and BE.

### TECH-02: Define Shared Application Standards

**Technical Story:** As a development team, we want shared implementation standards so that every LMS module follows the same patterns.

**Acceptance Criteria**

- Commands, queries, DTOs, validators, and handlers use one agreed structure.
- APIs return a consistent success and error format.
- Pagination, sorting, filtering, date, and enum formats are documented.
- A sample end-to-end operation demonstrates the agreed pattern.

**FE Tasks**

- Define TypeScript models for the common API response and paginated response.
- Define common handling for validation, business, unauthorized, forbidden, and server errors.
- Agree on date, time-zone, enum, and file-upload formats.

**BE Tasks**

- Configure MediatR or the selected application request pattern.
- Create common `Result` and paginated-result models.
- Create pagination, sorting, and filtering request models.
- Configure request validation and pipeline behavior.
- Configure object mapping where required.
- Define common application exceptions and error codes.
- Add a simple sample command, query, handler, validator, and controller.
- Document naming conventions for features, endpoints, DTOs, commands, and queries.

**QA Tasks**

- Verify common success and error responses.
- Verify pagination, sorting, and filtering behavior.
- Verify the sample operation from API request to database response.

---

## Feature 0.2: Database Foundation

### TECH-03: Configure Database Access and Migrations

**Technical Story:** As a backend team, we want a standard database foundation so that LMS data is stored consistently and schema changes are controlled.

**Acceptance Criteria**

- The application connects to the local development database.
- The initial migration can create the database successfully.
- Entity mappings and database constraints use agreed conventions.
- Audit fields are populated consistently.
- Database configuration is not hard-coded in source code.

**FE Tasks**

- Confirm the identifiers, timestamps, enum values, and pagination metadata expected from the API.

**BE Tasks**

- Create the application `DbContext`.
- Configure the database provider and connection string.
- Create base entity and auditable entity models.
- Define conventions for primary keys, foreign keys, table names, schemas, indexes, and decimal values.
- Configure entity mappings using Fluent API.
- Configure created, updated, and optional soft-delete fields.
- Create the initial migration.
- Create a controlled seed-data mechanism for roles and essential reference data.
- Configure transaction handling for multi-step business operations.
- Document migration creation and database update commands.
- Ensure secrets and connection strings can be supplied through environment configuration.

**QA Tasks**

- Create a database from the initial migration.
- Verify migration execution on a clean database.
- Verify seed data does not create duplicates when executed again.
- Verify required constraints, relationships, and audit fields.

---

## Feature 0.3: API Foundation

### TECH-04: Configure API Standards and Middleware

**Technical Story:** As an API consumer, we want consistent API behavior so that frontend integration and troubleshooting are predictable.

**Acceptance Criteria**

- Swagger documents the available endpoints and models.
- API errors use the common response format.
- Every request has a correlation ID.
- CORS, localization, health checks, and API configuration work.
- Sensitive implementation details are not returned in production errors.

**FE Tasks**

- Configure the base API URL for each environment.
- Create the shared HTTP client and interceptors.
- Add common API error and loading handling.
- Verify the sample API integration from the frontend.

**BE Tasks**

- Configure controllers and API routing conventions.
- Configure Swagger and XML documentation.
- Add global exception-handling middleware.
- Add correlation-ID middleware.
- Configure request and response logging without exposing passwords or tokens.
- Configure CORS for approved frontend origins.
- Configure English and Arabic localization.
- Add application and database health checks.
- Configure environment-specific settings.
- Add API versioning only if required by the project standard.
- Create a base controller or shared response helper only when needed.

**QA Tasks**

- Verify Swagger endpoint definitions and response examples.
- Test validation, not-found, unauthorized, forbidden, conflict, and server-error responses.
- Verify correlation IDs in responses and logs.
- Verify CORS, localization, and health checks.

---

## Feature 0.4: Security Foundation

### TECH-05: Configure Authentication and Authorization Infrastructure

**Technical Story:** As a platform team, we want secure authentication and authorization foundations so that LMS users and APIs are protected.

**Acceptance Criteria**

- Authentication middleware validates access tokens.
- Authorization policies can protect endpoints by role and permission.
- Passwords and security tokens are never stored as plain text.
- Secrets are loaded through secure configuration.
- Security events can be audited.

**FE Tasks**

- Create the authentication-state structure.
- Add route guards and unauthorized handling.
- Define secure access-token handling according to the selected authentication approach.
- Avoid storing sensitive values in insecure browser storage.

**BE Tasks**

- Configure the selected identity and authentication framework.
- Configure secure password hashing and password-policy settings.
- Configure access-token and refresh-token options.
- Create the current-user service.
- Define Student, Parent, Teacher, and Admin roles.
- Define the initial permission and authorization-policy structure.
- Add authentication and authorization middleware.
- Configure secret and token settings through environment configuration.
- Add placeholders for security-event and audit logging.
- Configure secure headers and rate-limiting foundations where required.

**QA Tasks**

- Verify protected endpoints reject anonymous users.
- Verify role and policy restrictions.
- Verify passwords, tokens, and secrets are not exposed in responses or logs.
- Verify expired and invalid token behavior.

---

## Feature 0.5: Frontend Foundation

### TECH-06: Create the Frontend Application Structure

**Technical Story:** As a frontend team, we want a consistent application structure and design foundation so that LMS screens can be developed efficiently.

**Acceptance Criteria**

- The frontend builds and runs for development and production.
- Routing and lazy-loaded business modules work.
- Arabic RTL layout is supported.
- Shared API, form, validation, loading, error, and notification patterns are available.
- The application works on agreed desktop and mobile viewports.

**FE Tasks**

- Create the frontend project using the approved framework and version.
- Define `core`, `shared`, `layout`, and business-module folders.
- Configure development, QA, and production environments.
- Configure routing and lazy loading.
- Create the public, authenticated, Admin, Teacher, Student, and Parent layout foundations.
- Configure global styling, typography, Arabic RTL direction, and responsive breakpoints.
- Create shared buttons, inputs, selectors, tables, dialogs, alerts, and file-upload controls.
- Configure reactive forms and common validators.
- Configure global loading and error handling.
- Create the API client and authentication interceptor.
- Add shared notification and confirmation services.
- Configure frontend linting, formatting, and testing.

**BE Tasks**

- Provide the sample API contract used for frontend integration.
- Support frontend environment and CORS configuration.
- Agree on upload, download, localization, and pagination contracts.

**QA Tasks**

- Verify development and production builds.
- Verify routing, layouts, RTL direction, and responsive behavior.
- Verify shared validation, loading, and error states.
- Verify the sample frontend-to-API flow.

---

## Feature 0.6: Testing and Quality Foundation

### TECH-07: Establish Automated Testing and Quality Standards

**Technical Story:** As a development team, we want automated quality checks so that regressions are detected early.

**Acceptance Criteria**

- FE and BE test projects execute successfully.
- A sample unit test and integration test demonstrate the expected patterns.
- Test data and test configuration do not depend on production systems.
- Pull requests have agreed review and quality expectations.

**FE Tasks**

- Configure the frontend unit-test framework.
- Add a sample component or service test.
- Configure linting and formatting checks.
- Define the frontend test-file and test-case naming conventions.

**BE Tasks**

- Configure Application unit tests.
- Configure API integration tests.
- Add test fixtures and reusable test-data builders where useful.
- Add a sample handler unit test.
- Add a sample API integration test.
- Configure code coverage reporting.
- Define which business rules require unit or integration tests.

**QA Tasks**

- Define the test strategy for functional, integration, regression, security, and performance testing.
- Define severity, priority, and defect states.
- Create a smoke-test checklist for every deployment.
- Define minimum Definition of Ready and Definition of Done criteria.

---

## Feature 0.7: Logging, Audit, and Monitoring

### TECH-08: Configure Application Observability

**Technical Story:** As a support team, we want useful logs and health information so that failures can be diagnosed.

**Acceptance Criteria**

- Logs contain timestamp, level, environment, application, and correlation ID.
- Exceptions are logged with useful technical context.
- Passwords, tokens, and personal data are not exposed.
- Health endpoints report application and database status.
- The logging destination can be changed by environment.

**FE Tasks**

- Add global client-error handling.
- Include the server correlation ID when displaying or reporting unexpected errors.
- Avoid logging tokens, passwords, or personal information in the browser.

**BE Tasks**

- Configure structured application logging.
- Add request correlation and exception logging.
- Define audit-log fields for important business and Admin actions.
- Configure health checks for the API and database.
- Configure environment-specific logging levels and destinations.
- Add sensitive-data filtering.
- Document how developers trace an error using a correlation ID.

**QA Tasks**

- Generate a controlled error and verify its correlation ID.
- Verify health responses for healthy and unavailable dependencies.
- Verify that sensitive data does not appear in logs.
- Verify that audit records include actor, action, target, reason, and timestamp where applicable.

---

## Feature 0.8: Local Development and Delivery

### TECH-09: Prepare Development Workflow and CI Foundation

**Technical Story:** As a development team, we want repeatable local setup and build validation so that every developer can work consistently.

**Acceptance Criteria**

- A new developer can run FE, BE, and the database using documented steps.
- Environment settings and secrets are documented without committing secret values.
- The build process validates compilation and automated tests.
- Branch, pull-request, and code-review rules are documented.

**FE Tasks**

- Document frontend prerequisites, installation, run, test, and build commands.
- Add environment-file examples without secrets.
- Ensure the frontend build can run in CI.

**BE Tasks**

- Document SDK, database, migration, run, test, and build commands.
- Add safe example configuration files.
- Add Docker support only if the team plans to use it.
- Create CI steps for restore, build, test, and artifact creation.
- Document branch naming, commit expectations, and pull-request review rules.

**QA Tasks**

- Follow the README on a clean environment and report missing steps.
- Define deployment smoke tests.
- Verify that a failed build or failed test blocks the quality pipeline.

---

## Epic 0 Completion Criteria

Epic 0 is complete when:

- FE and BE applications run locally.
- The solution follows the agreed Clean Architecture dependencies.
- The database can be created from migrations and seeded safely.
- Swagger, health checks, logging, localization, and global error handling work.
- Authentication and authorization foundations protect a sample endpoint.
- One sample vertical flow works from frontend to API to database.
- FE and BE automated tests execute successfully.
- Development and build instructions are documented and verified.

---

# Epic 1: Identity and Access Management

## Feature 1.1: User Registration and Family Access

### IAM-US-01: Student Registration

**User Story:** As a student, I want to register so that I can use the platform.

**Acceptance Criteria:** Student enters required data; duplicate identifiers are rejected; verification is triggered; the account is created in the correct initial status.

**FE Tasks**

- Build the student registration and verification experience.

**BE Tasks**

- Implement student registration, unique-identifier validation, account creation, and verification triggering.

**QA Tasks**

- Test successful registration, validation, duplicates, and initial account status.

### IAM-US-02: Parent Registration and Student Linking

**User Story:** As a parent, I want to register and link to my child so that I can follow progress.

**Acceptance Criteria:** Parent account is created; parent logs in; an approved student identifier is submitted; the linked student becomes visible in the parent dashboard.

**FE Tasks**

- Build parent registration, student linking, and linked-student display.

**BE Tasks**

- Implement parent registration and secure parent-student linking.

**QA Tasks**

- Test registration, valid and invalid links, duplicate links, and parent access restrictions.

## Feature 1.2: Teacher Account Approval

### IAM-US-03: Teacher Account Approval

**User Story:** As a teacher, I want my account approved so that I can create courses.

**Acceptance Criteria:** Teacher submits profile and verification data; Admin reviews the application; approved teacher gains access; rejected teacher receives a reason and cannot publish courses.

**FE Tasks**

- Build teacher verification submission, approval-status display, and Admin review screens.

**BE Tasks**

- Implement teacher verification submission, approval and rejection workflow, access control, and notifications.

**QA Tasks**

- Test teacher submission, approval, rejection, reasons, and course-access restrictions.

## Feature 1.3: Account Administration and Recovery

### IAM-US-04: User Account Management

**User Story:** As an admin, I want to manage user accounts so that platform access is controlled.

**Acceptance Criteria:** Admin can search users, view status, activate or suspend accounts, and all sensitive actions are logged.

**FE Tasks**

- Build user search, account details, and status-management screens.

**BE Tasks**

- Implement user queries, account-status actions, authorization, and audit logging.

**QA Tasks**

- Test search, activation, suspension, permissions, and audit records.

### IAM-US-05: Password Reset

**User Story:** As a user, I want to reset my password so that I can regain access if I forget it.

**Acceptance Criteria:** User requests reset; the system sends a valid one-time recovery method; an expired or reused reset method is rejected; the new password is saved successfully.

**FE Tasks**

- Build forgot-password, recovery verification, and new-password screens.

**BE Tasks**

- Implement secure password-reset requests, one-time recovery validation, expiry, and password update.

**QA Tasks**

- Test valid, invalid, expired, and reused recovery methods and password rules.

### IAM-US-06: Account Suspension

**User Story:** As an admin, I want to suspend risky accounts so that unauthorized or policy-violating access is stopped.

**Acceptance Criteria:** Admin changes account status to Suspended; the user can no longer authenticate; the action is recorded in the audit log.

**FE Tasks**

- Add account suspension with confirmation and reason.

**BE Tasks**

- Implement suspension, session revocation, login prevention, and audit logging.

**QA Tasks**

- Test suspension, active-session termination, blocked login, and audit history.

---

# Epic 2: Teacher Management

## Feature 2.1: Teacher Profile and Verification

### TM-US-T01: Complete Teacher Profile

**User Story:** As a teacher, I want to complete my profile and upload documents so that I can get verified.

**Acceptance Criteria:** Teacher fills in required profile data, selects subjects, uploads required documents, and the system sets the account to Pending Approval.

**FE Tasks**

- Build the teacher profile, subject selection, and document-upload form.

**BE Tasks**

- Implement profile creation, document storage, subject selection, and Pending Approval status.

**QA Tasks**

- Test required profile data, documents, subjects, and approval status.

### TM-US-T02: Edit Teacher Profile

**User Story:** As a teacher, I want to edit my profile so that my information is always up to date.

**Acceptance Criteria:** Teacher updates allowed fields successfully, and changes that affect verification trigger re-review when policy requires it.

**FE Tasks**

- Build teacher profile editing and show re-review status when applicable.

**BE Tasks**

- Implement allowed profile updates and re-review rules.

**QA Tasks**

- Test allowed and restricted changes and verification-impacting updates.

### TM-US-T06: Prevent Duplicate Teacher Accounts

**User Story:** As a teacher, I want to register with unique identity information so that duplicate accounts are prevented.

**Acceptance Criteria:** The system validates configured unique identifiers and blocks registration when duplicates are detected.

**FE Tasks**

- Display unique-identifier validation errors during teacher registration.

**BE Tasks**

- Enforce teacher email, phone, or configured identity uniqueness.

**QA Tasks**

- Test duplicate and valid teacher registrations.

## Feature 2.2: Teacher Review and Status

### TM-US-T03: Review Teacher Applications

**User Story:** As an admin, I want to review pending teacher applications so that I can verify credentials.

**Acceptance Criteria:** Admin can view pending teachers, open a profile, review uploaded documents, and choose Approve or Reject.

**FE Tasks**

- Build the pending-teacher list and application review page.

**BE Tasks**

- Implement pending-application queries and approval decisions.

**QA Tasks**

- Test application listing, details, document access, approval, and rejection.

### TM-US-T04: Reject Teacher With a Reason

**User Story:** As an admin, I want to reject a teacher with a reason so that they know what to fix.

**Acceptance Criteria:** Admin enters a mandatory rejection reason, and the teacher receives a clear notification describing the required correction.

**FE Tasks**

- Add teacher rejection with a mandatory reason and teacher feedback display.

**BE Tasks**

- Implement rejection-reason validation, status update, notification, and audit logging.

**QA Tasks**

- Test required reasons, teacher notification, and rejected status.

### TM-US-T05: Suspend Teacher Account

**User Story:** As an admin, I want to suspend a teacher account so that policy-violating or risky activity can be controlled.

**Acceptance Criteria:** Admin changes the status to Suspended, teaching access is restricted according to platform rules, and the action is logged.

**FE Tasks**

- Add teacher suspension and display the resulting status.

**BE Tasks**

- Implement teacher suspension, teaching-access restrictions, and audit logging.

**QA Tasks**

- Test suspension, restricted actions, and audit history.

## Feature 2.3: Verified Teaching Scope

### TM-US-T07: Create Courses for Verified Subjects

**User Story:** As a teacher, I want to create courses only for subjects I am verified in so that I teach within my approved scope.

**Acceptance Criteria:** The system shows only verified subjects for course creation and blocks attempts to use unverified subjects.

**FE Tasks**

- Show verified subjects only in the course form.

**BE Tasks**

- Validate teacher-subject approval during course creation.

**QA Tasks**

- Test verified and unverified subject selection.

---

# Epic 3: Student Management

## Feature 3.1: Student Learning and Progress

### SM-US-01: Enroll in Courses

**User Story:** As a student, I want to enroll in courses so that I can start learning.

**Acceptance Criteria:** Enrollment succeeds only when course access rules are met, and the course appears in the student's dashboard.

**FE Tasks**

- Add enrollment actions and display enrolled courses on the student dashboard.

**BE Tasks**

- Integrate enrollment rules and return the student's enrolled courses.

**QA Tasks**

- Test successful and blocked enrollment and dashboard visibility.

### SM-US-02: Track Student Progress

**User Story:** As a student, I want to track my progress so that I know my completion status.

**Acceptance Criteria:** Progress percentage updates automatically when lessons, quizzes, or assignments are completed.

**FE Tasks**

- Display course and activity progress to the student.

**BE Tasks**

- Calculate and update progress from completed learning activities.

**QA Tasks**

- Test progress calculations after lessons, quizzes, and assignments.

### SM-US-04: Record Attendance

**User Story:** As a teacher, I want to record attendance so that student participation is tracked.

**Acceptance Criteria:** Teacher can mark attendance for scheduled course sessions and save the record successfully.

**FE Tasks**

- Build the teacher attendance-entry screen.

**BE Tasks**

- Implement scheduled-session attendance recording.

**QA Tasks**

- Test attendance entry, updates, permissions, and saved records.

## Feature 3.2: Parent Monitoring

### SM-US-03: Monitor Child Progress

**User Story:** As a parent, I want to monitor my child's progress so that I can support learning.

**Acceptance Criteria:** Parent can access linked student progress reports, attendance records, and released results.

**FE Tasks**

- Build parent views for linked-student progress, attendance, and results.

**BE Tasks**

- Provide parent reporting queries restricted to linked students.

**QA Tasks**

- Test linked and unlinked student access and displayed learning data.

## Feature 3.3: Student Administration and Communication

### SM-US-05: Manage Student Records

**User Story:** As an admin, I want to manage student records so that data remains accurate.

**Acceptance Criteria:** Admin can search students, update allowed record fields, and activate or deactivate accounts based on permissions.

**FE Tasks**

- Build student search, details, edit, activation, and deactivation screens.

**BE Tasks**

- Implement student queries, permitted updates, account-status actions, and authorization.

**QA Tasks**

- Test search, updates, status changes, and Admin permissions.

### SM-US-06: Receive Learning Reminders

**User Story:** As a student, I want to receive reminders and updates so that I do not miss important learning events.

**Acceptance Criteria:** Student receives notifications for enrollment, schedule changes, deadlines, and released results.

**FE Tasks**

- Display student notifications and links to related learning items.

**BE Tasks**

- Generate notifications for the required student events.

**QA Tasks**

- Test event triggers, recipients, content, and related links.

---

# Epic 4: Content and Course Management

## Feature 4.1: Course Creation and Structure

### CCM-US-01: Create Course Draft

**User Story:** As a teacher, I want to create a basic course draft so that I can plan my curriculum before publishing.

**Acceptance Criteria:** Course is saved in Draft status, and core metadata such as title, description, and price settings are stored correctly.

**FE Tasks**

- Build the basic course-draft form.

**BE Tasks**

- Implement draft creation and storage of core course metadata.

**QA Tasks**

- Test required metadata, pricing, and Draft status.

### CCM-US-02: Create Course

**User Story:** As a teacher, I want to create a course so that I can provide learning content to students.

**Acceptance Criteria:** Teacher enters required information, saves the course, and the course is created successfully.

**FE Tasks**

- Build the complete course create and edit experience.

**BE Tasks**

- Implement course creation, validation, ownership, and persistence.

**QA Tasks**

- Test valid and invalid course creation and teacher ownership.

### CCM-US-03: Organize Course Structure

**User Story:** As a teacher, I want to organize my course into subjects, modules, and lessons so that content is structured and easy to follow.

**Acceptance Criteria:** Teacher can add, edit, reorder, and remove structure elements successfully.

**FE Tasks**

- Build the course structure editor.

**BE Tasks**

- Implement subject, module, and lesson operations and ordering.

**QA Tasks**

- Test add, edit, reorder, remove, and ownership rules.

### CCM-US-04: Upload Educational Materials

**User Story:** As a teacher, I want to upload educational materials so that students can access learning resources.

**Acceptance Criteria:** Uploaded content is attached to lessons and becomes available according to publication and access rules.

**FE Tasks**

- Add material upload, progress, preview, and removal.

**BE Tasks**

- Implement secure file storage, lesson attachment, validation, and access control.

**QA Tasks**

- Test allowed files, upload failures, lesson attachment, and access rules.

## Feature 4.2: Course Review and Publishing

### CCM-US-05: Review Course Before Publishing

**User Story:** As a teacher, I want my course to be reviewed before publishing so that it complies with platform policies.

**Acceptance Criteria:** When the teacher submits a course for publishing, the system performs automated review, blocks violations, and provides clear feedback when issues exist.

**FE Tasks**

- Add publishing submission and display automated-review feedback.

**BE Tasks**

- Implement publishing validation, automated review, violation blocking, and feedback.

**QA Tasks**

- Test valid submissions, policy violations, and feedback.

### CCM-US-06: Publish Course

**User Story:** As a teacher, I want to publish a course so that students can access it.

**Acceptance Criteria:** Course meets publishing requirements and becomes visible to eligible students.

**FE Tasks**

- Add course publication and status display.

**BE Tasks**

- Implement publishing requirements, status transition, and catalog visibility.

**QA Tasks**

- Test eligible and ineligible publication and student visibility.

## Feature 4.3: Course Discovery and Access

### CCM-US-08: Browse Available Courses

**User Story:** As a student, I want to browse available courses so that I can find learning opportunities.

**Acceptance Criteria:** Student can search courses and view course details, syllabus information, and access conditions.

**FE Tasks**

- Build the course catalog, search, filters, and course details.

**BE Tasks**

- Implement published-course search and details queries.

**QA Tasks**

- Test search, details, syllabus, access conditions, and unpublished-course exclusion.

### CCM-US-09: Access Enrolled Courses

**User Story:** As a student, I want to access enrolled courses so that I can study the learning materials.

**Acceptance Criteria:** Student can open and use content only for courses they are authorized to access.

**FE Tasks**

- Build the enrolled-course content experience.

**BE Tasks**

- Enforce enrollment-based course and material access.

**QA Tasks**

- Test enrolled, non-enrolled, and direct-content access.

## Feature 4.4: Course Engagement

### CCM-US-07: Monitor Student Attendance and Progress

**User Story:** As a teacher, I want to monitor student attendance and progress so that I can evaluate engagement.

**Acceptance Criteria:** Teacher can view attendance status, lesson progress, and quiz outcomes for enrolled students.

**FE Tasks**

- Build teacher views for attendance, lesson progress, and quiz outcomes.

**BE Tasks**

- Provide course-engagement queries restricted to the course teacher.

**QA Tasks**

- Test engagement data, teacher ownership, and student privacy.

### CCM-US-10: Complete Lesson Quiz

**User Story:** As a student, I want to complete a lesson quiz so that I can unlock the next lesson and continue learning.

**Acceptance Criteria:** Quiz is submitted, graded automatically, score is displayed, and the next lesson is unlocked only if the passing score is achieved.

**FE Tasks**

- Build lesson-quiz submission, score display, and lesson unlocking.

**BE Tasks**

- Implement quiz submission, automatic grading, passing rules, and lesson access.

**QA Tasks**

- Test pass, fail, score display, retry behavior, and lesson locking.

---

# Epic 5: Enrollment Management

## Feature 5.1: Course Enrollment

### EM-US-E01: Enroll in a Paid Course

**User Story:** As a student, I want to enroll in a paid course after payment so that I can access its content.

**Acceptance Criteria:** Payment succeeds; Enrollment status becomes Active; content is immediately accessible; the course appears in the student dashboard.

**FE Tasks**

- Build paid enrollment confirmation and success states.

**BE Tasks**

- Create an Active enrollment after confirmed payment and grant content access.

**QA Tasks**

- Test payment-linked enrollment, status, access, and dashboard display.

### EM-US-E02: Enroll in a Free Course

**User Story:** As a student, I want to enroll in a free course directly so that I can start learning without payment.

**Acceptance Criteria:** Student selects Enroll; Enrollment status becomes Active; Payment ID is empty; content is immediately accessible.

**FE Tasks**

- Add direct enrollment for free courses.

**BE Tasks**

- Implement free enrollment without payment and grant access.

**QA Tasks**

- Test free enrollment, empty Payment ID, status, and access.

### EM-US-E06: Prevent Duplicate Enrollment

**User Story:** As a student, I want to be prevented from enrolling twice in the same course so that I do not accidentally pay twice.

**Acceptance Criteria:** A repeated enrollment is blocked with an already-enrolled message and a link to the existing enrollment.

**FE Tasks**

- Display existing-enrollment guidance instead of repeating purchase.

**BE Tasks**

- Enforce unique active enrollment per student and course.

**QA Tasks**

- Test repeated and concurrent enrollment attempts.

## Feature 5.2: Enrollment Views and Access

### EM-US-E03: View Enrolled Courses

**User Story:** As a student, I want to view all my enrolled courses so that I can track my learning journey.

**Acceptance Criteria:** Dashboard displays Course Name, Teacher Name, Enrollment Date, Progress, and Status.

**FE Tasks**

- Build the My Courses view with the required enrollment information.

**BE Tasks**

- Provide the student's enrollment list and progress summary.

**QA Tasks**

- Test displayed values, statuses, and student data isolation.

### EM-US-E05: View Enrolled Students

**User Story:** As a teacher, I want to see all students enrolled in my courses so that I can understand my audience.

**Acceptance Criteria:** Teacher sees student Name, Enrollment Date, and Progress; the teacher cannot edit or delete enrollment records.

**FE Tasks**

- Build the teacher course-enrollment list as read-only.

**BE Tasks**

- Provide teacher-owned course enrollment queries without modification actions.

**QA Tasks**

- Test displayed information, read-only behavior, and teacher ownership.

### EM-US-E07: Preserve Enrollment After Teacher Suspension

**User Story:** As the system, I want to preserve existing enrollments when a teacher is suspended so that students' learning is not disrupted.

**Acceptance Criteria:** New enrollments are blocked; existing enrollments remain Active; enrolled students retain content access.

**FE Tasks**

- Display that new enrollment is unavailable while preserving enrolled-student access.

**BE Tasks**

- Block new enrollment and preserve existing active enrollment access.

**QA Tasks**

- Test new and existing enrollment behavior after teacher suspension.

### EM-US-E08: Complete Enrollment

**User Story:** As the system, I want to mark enrollments as Completed when students finish the course so that completion rates can be tracked.

**Acceptance Criteria:** Progress is 100%; the final assessment is passed or not required; status becomes Completed; a completion notification is sent.

**FE Tasks**

- Display completed enrollment status and completion feedback.

**BE Tasks**

- Implement completion rules, status update, and notification.

**QA Tasks**

- Test completion with and without a final assessment.

## Feature 5.3: Cancellation and Refund

### EM-US-E04: Cancel Enrollment and Request Refund

**User Story:** As a student, I want to cancel my enrollment within the allowed period to get a refund if the course does not meet my expectations.

**Acceptance Criteria:** Cancellation is allowed within seven days when progress is below 20% and the enrollment is refund eligible; status becomes Pending Refund; access is suspended; Admin and student are notified. Otherwise, a specific error is displayed.

**FE Tasks**

- Build cancellation, eligibility feedback, confirmation, and Pending Refund status.

**BE Tasks**

- Implement cancellation eligibility, access suspension, status update, and notifications.

**QA Tasks**

- Test all eligible and ineligible cancellation combinations.

### EM-US-E10: Review Refund Requests

**User Story:** As an admin, I want to review pending refund requests so that I can prevent abuse of the refund policy.

**Acceptance Criteria:** Admin reviews progress and enrollment date, approves or rejects with a mandatory reason, enrollment and access are updated correctly, refund is triggered when approved, and the student is notified.

**FE Tasks**

- Build the pending-refund list and approve or reject workflow.

**BE Tasks**

- Implement refund decisions, reasons, payment action, enrollment access changes, and notifications.

**QA Tasks**

- Test approval, rejection, reasons, refund triggering, access, and notifications.

### EM-US-E09: Administrative Enrollment Cancellation

**User Story:** As an admin, I want to manually cancel a student's enrollment without a refund for policy violations.

**Acceptance Criteria:** Status becomes Cancelled, no refund is issued, a mandatory reason is stored, the action is audited, access is removed, and the student cannot re-enroll in the same course.

**FE Tasks**

- Add administrative cancellation with a mandatory reason.

**BE Tasks**

- Implement cancellation without refund, access removal, permanent re-enrollment blocking, and audit logging.

**QA Tasks**

- Test cancellation, no-refund behavior, access removal, blocking, and audit history.

---

# Epic 6: Assessment Management

## Feature 6.1: Assessment Authoring

### AM-US-01: Create Exam

**User Story:** As a teacher, I want to create an exam so that I can evaluate student knowledge.

**Acceptance Criteria:** Teacher enters exam details; the exam is saved successfully; the exam appears in the teacher dashboard.

**FE Tasks**

- Build exam creation and teacher exam-list screens.

**BE Tasks**

- Implement exam creation, validation, ownership, and retrieval.

**QA Tasks**

- Test valid and invalid exam creation and dashboard display.

### AM-US-02: Add Assessment Questions

**User Story:** As a teacher, I want to add questions to an assessment so that students can answer them.

**Acceptance Criteria:** Questions are created successfully and linked to the assessment.

**FE Tasks**

- Build question creation and assessment-question management.

**BE Tasks**

- Implement question creation, validation, and assessment linkage.

**QA Tasks**

- Test question creation, types, validation, and linkage.

## Feature 6.2: Assessment Participation and Review

### AM-US-03: Take Quizzes and Exams

**User Story:** As a student, I want to take quizzes and exams so that I can evaluate my learning progress.

**Acceptance Criteria:** Student accesses available assessments and submits answers successfully.

**FE Tasks**

- Build assessment access, answer entry, and submission.

**BE Tasks**

- Implement assessment availability, attempts, answer storage, and submission.

**QA Tasks**

- Test authorized access, answer submission, and unavailable assessments.

### AM-US-04: Review Assessment Submissions

**User Story:** As a teacher, I want to review submissions so that I can evaluate student performance.

**Acceptance Criteria:** Teacher can review submissions and assign grades and feedback.

**FE Tasks**

- Build the teacher submission-review and feedback screen.

**BE Tasks**

- Provide submission queries and save grades and feedback.

**QA Tasks**

- Test submission review, grading, feedback, and teacher authorization.

## Feature 6.3: Parent Assessment View

### AM-US-05: View Child Assessment Results

**User Story:** As a parent, I want to view my child's assessment results so that I can monitor academic performance.

**Acceptance Criteria:** Parent can access linked student results.

**FE Tasks**

- Build the parent assessment-results view.

**BE Tasks**

- Provide results restricted to linked students.

**QA Tasks**

- Test linked and unlinked student result access.

---

# Epic 7: Grading Management

## Feature 7.1: Grade Student Work

### GM-US-01: Automatic Grading

**User Story:** As a student, I want automatic grading.

**Acceptance Criteria:** Objective questions are graded automatically.

**FE Tasks**

- Display automatic grading status and score.

**BE Tasks**

- Implement objective-question grading and score calculation.

**QA Tasks**

- Test correct and incorrect answers and calculated scores.

### GM-US-02: Grade Essays

**User Story:** As a teacher, I want to grade essays.

**Acceptance Criteria:** Teacher can assign and save scores.

**FE Tasks**

- Build essay scoring and feedback entry.

**BE Tasks**

- Implement authorized manual score and feedback saving.

**QA Tasks**

- Test valid scores, score limits, saving, and permissions.

### GM-US-05: Publish Results

**User Story:** As a teacher, I want to publish results.

**Acceptance Criteria:** Students see only approved grades.

**FE Tasks**

- Add result review and publication.

**BE Tasks**

- Implement result approval, publication, and visibility rules.

**QA Tasks**

- Test published and unpublished result visibility.

### GM-US-06: Modify Results With Reason

**User Story:** As a teacher, I want to modify results with a reason.

**Acceptance Criteria:** A reason is mandatory and the change is audit logged.

**FE Tasks**

- Add result modification with a mandatory reason.

**BE Tasks**

- Implement result changes, reason validation, recalculation, and audit logging.

**QA Tasks**

- Test modifications, required reasons, recalculation, and audit history.

## Feature 7.2: View Academic Results

### GM-US-03: View Published Results

**User Story:** As a student, I want to view results.

**Acceptance Criteria:** Only published results are visible.

**FE Tasks**

- Build the student results view.

**BE Tasks**

- Provide published results restricted to the current student.

**QA Tasks**

- Test published and unpublished visibility and student isolation.

### GM-US-07: Parent Views Child Grades

**User Story:** As a parent, I want to view my child's grades so that I can monitor their academic performance.

**Acceptance Criteria:** Parent can view exam grades, quiz scores, pass/fail status, and overall course grade for a linked student and cannot modify grade data.

**FE Tasks**

- Build the read-only parent grades view.

**BE Tasks**

- Provide grades restricted to linked students.

**QA Tasks**

- Test displayed grade information, read-only behavior, and link restrictions.

### GM-US-08: Browse Resolved Exam Results

**User Story:** As a student, I want to browse my resolved exam results so that I can monitor my learning progress.

**Acceptance Criteria:** The request returns the complete matching results for the target Student ID.

**FE Tasks**

- Build resolved-exam result browsing.

**BE Tasks**

- Implement resolved-result queries with student authorization.

**QA Tasks**

- Test complete results, filtering, and student access restrictions.

## Feature 7.3: Grading Oversight

### GM-US-04: Monitor Grading

**User Story:** As an admin, I want to monitor grading.

**Acceptance Criteria:** Grading audit information is available.

**FE Tasks**

- Build the grading audit view.

**BE Tasks**

- Record and expose secured grading audit information.

**QA Tasks**

- Test audit completeness, accuracy, and Admin-only access.

---

# Module Summary

| Epic | Source Module | Business Stories |
| --- | --- | ---: |
| Epic 0 | Technical Foundation | 1 technical story |
| Epic 1 | Identity and Access Management | 6 stories |
| Epic 2 | Teacher Management | 7 stories |
| Epic 3 | Student Management | 6 stories |
| Epic 4 | Content and Course Management | 10 stories |
| Epic 5 | Enrollment Management | 10 stories |
| Epic 6 | Assessment Management | 5 stories |
| Epic 7 | Grading Management | 8 stories |

# Naming Convention

```text
Project: E-Learning Platform
Epic:    EP-05 Enrollment Management
Feature: FT-05.01 Course Enrollment
Story:   EM-US-E01 Enroll in a Paid Course
Task:    FE / BE / QA Task
```