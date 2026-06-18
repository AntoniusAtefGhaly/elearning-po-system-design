# E-Learning Website - User Stories and Acceptance Criteria

## 1. Purpose

This document converts the module documents into user stories that the software team can use for planning and implementation.

Stories are ordered by system module.

## 2. Scope Note

- MVP stories are planned for the first release.
- Future stories are documented for learning and later phases, but they are not required for MVP implementation.

## 3. Module 01 - Identity & Access Management

### US-IM-01: Student Registration

As a student, I want to register so that I can use the platform.

Acceptance Criteria:

- Student enters required registration data.
- System rejects duplicate phone or email.
- Account is created successfully.
- Student can log in after registration.

### US-IM-02: Parent Registration

As a parent, I want to register so that I can follow my child.

Acceptance Criteria:

- Parent enters required registration data.
- Account is created successfully.
- Parent can log in.

### US-IM-03: Teacher Account Approval

As a teacher, I want my account approved so that I can create courses.

Acceptance Criteria:

- Teacher submits required profile data and documents.
- Admin can approve or reject the teacher.
- Rejected teacher cannot publish courses.

### US-IM-04: Admin User Management

As an admin, I want to manage user accounts so that platform access is controlled.

Acceptance Criteria:

- Admin can view users.
- Admin can update user status.
- Admin can approve teachers.
- Admin actions are recorded for audit.

## 4. Module 02 - Teacher Management

### US-TM-01: Complete Teacher Profile

As a teacher, I want to complete my profile and upload documents so that I can get verified.

Acceptance Criteria:

- Teacher enters bio, contact info, subject, and profile image.
- Teacher uploads required verification documents.
- System saves the data and sets teacher status to pending approval.

### US-TM-02: Edit Teacher Profile

As a teacher, I want to edit my profile so that my information stays up to date.

Acceptance Criteria:

- Teacher can update bio, profile image, and contact information.
- Changes are saved successfully.
- Changes to teaching subjects require re-verification.

### US-TM-03: Review Teacher Application

As an admin, I want to review pending teacher applications so that I can verify their credentials.

Acceptance Criteria:

- Admin can view pending teacher applications.
- Admin can open teacher profile details and uploaded documents.
- Admin can approve or reject the application.

### US-TM-04: Reject Teacher With Reason

As an admin, I want to reject a teacher with a reason so that the teacher knows what to fix.

Acceptance Criteria:

- Admin must enter a rejection reason.
- Teacher status becomes rejected.
- Rejection reason is saved.

### US-TM-05: Suspend Teacher Account

As an admin, I want to suspend a teacher account so that a blocked teacher cannot continue teaching.

Acceptance Criteria:

- Admin can change teacher status to suspended.
- Suspended teacher cannot create new courses.
- New enrollments are blocked for suspended teacher courses.
- Existing enrolled students keep access.

### US-TM-06: Prevent Duplicate Teacher Accounts

As a teacher, I want my National ID and phone to be unique so that duplicate accounts are prevented.

Acceptance Criteria:

- System validates National ID uniqueness.
- System validates phone uniqueness.
- Duplicate registration is rejected with an error message.

### US-TM-07: Create Courses for Verified Subjects

As a teacher, I want to create courses only for subjects I am verified in so that I teach within my expertise.

Acceptance Criteria:

- Teacher sees only verified subjects during course creation.
- System blocks course creation for unverified subjects.

## 5. Module 03 - Student Management

### US-SM-01: Update Student Profile

As a student, I want to update my profile so that my academic data is correct.

Acceptance Criteria:

- Student can update allowed profile fields.
- System saves the updated data.
- Student cannot change restricted administrative fields.

### US-SM-02: View Enrolled Courses

As a student, I want to view my enrolled courses so that I can continue learning.

Acceptance Criteria:

- Student dashboard shows enrolled courses.
- Each course shows status and progress.
- Student can open an active enrolled course.

### US-SM-03: Track Student Progress

As a student, I want to track my progress so that I know my completion status.

Acceptance Criteria:

- Progress updates after lesson completion.
- Automatic completion happens after watching 90% of the video.
- Student can see progress percentage or completion status.

### US-SM-04: Parent Monitors Student Progress

As a parent, I want to monitor my child's progress so that I can support learning.

Acceptance Criteria:

- Parent can view only linked student data.
- Parent can view enrolled courses and progress.
- Parent cannot modify student academic data.

### US-SM-05: Admin Manages Student Records

As an admin, I want to manage student records so that data remains accurate.

Acceptance Criteria:

- Admin can view student accounts.
- Admin can update allowed student account data.
- Admin can deactivate student accounts if needed.

### US-SM-06: Record Attendance - Future

As a teacher, I want to record attendance so that student participation is tracked.

Acceptance Criteria:

- Teacher can mark attendance for own course sessions.
- Attendance is stored for reports.
- This story is future scope, not MVP.

### US-SM-07: Student Notifications - Future

As a student, I want to receive course notifications so that I do not miss updates.

Acceptance Criteria:

- System can notify students about course updates and schedules.
- This story is future scope, not MVP.

## 6. Module 04 - Content & Course Management

### US-CM-01: Create Course Draft

As a teacher, I want to create a course draft so that I can prepare my curriculum before publishing.

Acceptance Criteria:

- Teacher can enter course title, description, price, year, subject, term, and chapter.
- Course is saved with draft status.
- Draft course is visible only to the teacher and admin.

### US-CM-02: Organize Course Structure

As a teacher, I want to organize my course into subjects, modules, and lessons so that content is easy to follow.

Acceptance Criteria:

- Teacher can add, edit, reorder, and remove structure items.
- Lesson belongs to a module.
- Module belongs to a subject.
- Subject belongs to a course.

### US-CM-03: Upload Learning Materials

As a teacher, I want to upload educational materials so that students can access learning resources.

Acceptance Criteria:

- Teacher can upload videos and documents.
- Uploaded content is linked to lessons.
- Enrolled students can access content after course publication.

### US-CM-04: Submit Course for Review

As a teacher, I want my course to be reviewed before publishing so that it complies with platform rules.

Acceptance Criteria:

- Teacher can submit a complete course for review.
- Course status changes to pending approval.
- Admin can approve or reject the course.

### US-CM-05: Publish Course

As an admin, I want to publish approved courses so that students can enroll in them.

Acceptance Criteria:

- Approved course becomes visible in the course catalog.
- Unapproved course remains hidden from students.
- Students can view course details before enrollment.

### US-CM-06: Browse Courses

As a student, I want to browse available courses so that I can find suitable learning content.

Acceptance Criteria:

- Student can view published courses only.
- Student can search or filter by curriculum data and teacher.
- Student can open course details and syllabus.

### US-CM-07: Access Enrolled Course Content

As a student, I want to access enrolled courses so that I can study the learning materials.

Acceptance Criteria:

- Student can access content only for enrolled courses.
- Unenrolled student can view course information only.
- Video content is not directly downloadable.

### US-CM-08: Lesson Quiz Progression

As a student, I want to complete a lesson quiz so that my progress can be recorded.

Acceptance Criteria:

- Student can submit lesson quiz answers.
- System calculates score according to assessment rules.
- Score is shown to the student.
- Quiz retry is allowed in MVP.

### US-CM-09: Archive/Delete/Restore Course - Future

As a teacher, I want to archive, delete, or restore courses so that I can manage course lifecycle.

Acceptance Criteria:

- Archived courses do not accept new enrollments.
- Deleted courses are soft deleted and auditable.
- This story is future scope, not MVP.

### US-CM-10: Free Course Enrollment - Future

As a student, I want to enroll in free courses so that I can learn without payment.

Acceptance Criteria:

- Student can enroll without balance deduction.
- Enrollment is created with no payment reference.
- This story is future scope, not MVP.

## 7. Module 05 - Enrollment Management

### US-EM-01: Enroll in Paid Course

As a student, I want to enroll in a paid course after using my balance so that I can access its content.

Acceptance Criteria:

- Student has enough balance.
- Course is published.
- Student balance is reduced by course price.
- Enrollment status becomes active.
- Course appears in student dashboard.

### US-EM-02: Prevent Duplicate Enrollment

As a student, I want to be prevented from enrolling twice in the same course so that I do not pay twice.

Acceptance Criteria:

- System checks existing enrollments before purchase.
- Duplicate enrollment is blocked.
- Student receives a clear error message.

### US-EM-03: Enrollment Access Control

As the system, I want to allow content access only for active enrollments so that paid content is protected.

Acceptance Criteria:

- Active enrolled student can access course content.
- Unenrolled student cannot access paid lessons.
- Access check is enforced on every content request.

### US-EM-04: View Enrolled Students

As a teacher, I want to see students enrolled in my courses so that I can understand my audience.

Acceptance Criteria:

- Teacher can view enrolled students for own courses.
- Teacher can view enrollment date and progress.
- Teacher cannot edit or delete enrollment records.

### US-EM-05: Preserve Access When Teacher Is Suspended

As the system, I want to preserve existing enrollments when a teacher is suspended so that students' learning is not disrupted.

Acceptance Criteria:

- New enrollments are blocked for suspended teacher courses.
- Existing enrollments remain active.
- Existing students retain course access.

### US-EM-06: Mark Enrollment Completed

As the system, I want to mark enrollments as completed when students finish the course so that completion can be tracked.

Acceptance Criteria:

- Enrollment becomes completed when course completion rules are met.
- Progress is updated correctly.
- Completion is visible in student and teacher views.

### US-EM-07: Manual Refund Handling

As an admin, I want to handle eligible refunds manually so that support cases can be resolved.

Acceptance Criteria:

- Refund is allowed only if the student has not used the course.
- Admin can reset student balance to 0.
- Money return is handled manually outside the system.
- Refund action is logged.

### US-EM-08: Advanced Refund Workflow - Future

As an admin, I want to review pending refund requests so that refund policy can be controlled automatically.

Acceptance Criteria:

- System supports pending refund status.
- Admin can approve or reject refund requests.
- This story is future scope, not MVP.

## 8. Module 06 - Assessment Management

### US-AM-01: Create Exam

As a teacher, I want to create an exam so that I can evaluate student knowledge.

Acceptance Criteria:

- Teacher enters exam details.
- Exam is saved successfully.
- Exam appears in teacher dashboard.

### US-AM-02: Create Quiz

As a teacher, I want to create a quiz so that students can check their understanding.

Acceptance Criteria:

- Teacher enters quiz details.
- Quiz is linked to a course or lesson.
- Quiz is saved successfully.

### US-AM-03: Add Questions

As a teacher, I want to add questions to an assessment so that students can answer them.

Acceptance Criteria:

- Teacher can create questions.
- Questions are linked to the assessment.
- Assessment cannot be published without at least one question.

### US-AM-04: Publish Assessment

As a teacher, I want to publish an assessment so that enrolled students can take it.

Acceptance Criteria:

- Assessment has required questions and grading rule.
- Published assessment becomes available to eligible enrolled students.
- Active published assessment cannot be modified in a way that breaks existing attempts.

### US-AM-05: Submit Assessment Answers

As a student, I want to take quizzes and exams so that I can evaluate my learning progress.

Acceptance Criteria:

- Student can access assessments assigned to enrolled courses.
- Student can submit answers within the allowed time window.
- System records the attempt and completion status.
- Quiz retry is allowed in MVP.

### US-AM-06: Review Submissions

As a teacher, I want to review submissions so that I can evaluate student performance.

Acceptance Criteria:

- Teacher can view submissions for own assessments.
- Teacher can add grades and feedback where manual review is needed.

### US-AM-07: View Assessment Results

As a parent, I want to view my child's assessment results so that I can monitor academic performance.

Acceptance Criteria:

- Parent can view results for linked students only.
- Parent has read-only access.

### US-AM-08: Assessment Notifications - Future

As a student, I want to receive assessment deadline reminders so that I do not miss exams.

Acceptance Criteria:

- System can notify students about upcoming assessments and deadlines.
- This story is future scope, not MVP.

## 9. Module 07 - Grading Management

### US-GM-01: Automatic Objective Grading

As a student, I want objective questions to be graded automatically so that I can receive results quickly.

Acceptance Criteria:

- System grades objective questions automatically.
- Score does not exceed maximum score.
- Result is stored after grading.

### US-GM-02: Manual Essay Grading

As a teacher, I want to grade essay answers manually so that subjective answers are evaluated correctly.

Acceptance Criteria:

- Teacher can assign and save scores.
- Teacher can grade only assessments belonging to own courses.
- Grading action is logged.

### US-GM-03: Generate Result

As the system, I want to generate results after grading so that student performance is recorded.

Acceptance Criteria:

- Result is generated only after grading is complete.
- System calculates score, percentage, and pass/fail status.
- Result is hidden until published.

### US-GM-04: Publish Results

As a teacher, I want to publish results so that students can view approved grades.

Acceptance Criteria:

- Teacher can review draft results.
- Teacher can publish results.
- Students can view only published results.

### US-GM-05: Modify Result With Reason

As a teacher, I want to modify results with a reason so that corrections are auditable.

Acceptance Criteria:

- Teacher must enter modification reason.
- System recalculates result after modification.
- Modification is saved in audit log.

### US-GM-06: Student Views Results

As a student, I want to view my published results so that I can monitor my learning progress.

Acceptance Criteria:

- Student can view only own published results.
- Result shows score, percentage, and pass/fail status.

### US-GM-07: Parent Views Grades

As a parent, I want to view my child's grades so that I can monitor academic performance.

Acceptance Criteria:

- Parent can view grades for linked students only.
- Parent can view exam grades, quiz scores, pass/fail status, and overall course grade.
- Parent cannot modify grade data.

### US-GM-08: Admin Monitors Grading

As an admin, I want to monitor grading actions so that grading changes are auditable.

Acceptance Criteria:

- Admin can view grading audit information.
- Audit log shows action, actor, date, and reason where applicable.

### US-GM-09: Result Notifications - Future

As a student, I want to receive a notification when final results are generated so that I know when to check grades.

Acceptance Criteria:

- System can notify students after final result generation.
- This story is future scope, not MVP.

## 10. Phase 2 Modules

The following module documents are planned for Phase 2 and will need their own user stories later:

- Module 08 - Payment & Subscription Management
- Module 09 - Notification Management
- Module 10 - Parent Portal
- Module 11 - Reporting & Analytics
- Module 12 - Administration
