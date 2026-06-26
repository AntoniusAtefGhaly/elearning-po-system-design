# E-Learning Platform - Developer Module Business Reference

## 1. Purpose

This document is the single business reference for developers before implementation.

It summarizes the module business documents into a practical developer handoff:

- What each module owns
- What is inside MVP
- What is future scope
- Main business rules
- Key entities
- Important flows
- User story and backlog references

This is not a raw merge of the module documents. It is the cleaned reference version.

## 2. Product Scope Summary

The product is an Arabic-first e-learning website for Egyptian high school students and private course teachers.

Students can:

- Register and log in
- Browse published teacher courses
- Redeem prepaid codes into balance
- Buy teacher courses separately using balance
- Watch enrolled lessons
- Solve assessments/quizzes
- Track progress
- View published results

Teachers can:

- Register and complete profile verification
- Create and manage course drafts
- Upload lessons and materials
- Create assessments/quizzes
- View enrolled students and progress
- Review grading where needed

Parents can:

- Register and log in
- Link to a student using student ID
- Redeem prepaid codes for one linked student
- View linked student progress and grades

Admins can:

- Manage users
- Approve/reject teachers
- Approve/publish courses
- Manage prepaid codes and student balance
- View reports
- Audit sensitive actions

## 3. MVP Decisions Developers Must Follow

| Area | MVP Decision |
| --- | --- |
| Language | Arabic only at launch. English is future scope. |
| Grades | Egyptian secondary/high school years 1, 2, and 3. |
| Curriculum | Courses follow official Egyptian curriculum by year, subject, term, chapter. |
| Teachers | Teacher is individual. No education center scope. |
| Course purchase | Student buys each teacher course separately. No bundles in MVP. |
| Payment | Prepaid codes add balance. No payment gateway in MVP. |
| Balance | Balance can be partially used across courses. Balance cannot be negative. |
| Prepaid code | One code is redeemed once for one student. Codes do not expire. Admin can cancel active code. |
| Refund | Manual only. If eligible, admin resets balance to 0 and returns money outside system. No refund after course usage. |
| Video protection | No direct download. Advanced watermarking is future scope. |
| Lesson completion | Manual and automatic. Automatic completion after watching 90% of video. |
| Quiz retry | Retry is allowed in MVP. Store attempts separately. |
| Parent link | Parent links to student using student ID. Approval workflow is out of scope. |
| Notifications | Future scope. Do not make MVP behavior depend on notifications. |
| Attendance | Future scope. |
| Free courses | Future scope. MVP course purchase requires balance. |
| Archive/delete/restore course lifecycle | Future scope. MVP supports draft, pending approval, approved/published, rejected. |

## 4. Module Prefixes

| Module | Prefix | Example |
| --- | --- | --- |
| Identity & Access Management | IM | US-IM-01 |
| Teacher Management | TM | US-TM-01 |
| Student Management | SM | US-SM-01 |
| Content & Course Management | CM | US-CM-01 |
| Enrollment Management | EM | US-EM-01 |
| Assessment Management | AM | US-AM-01 |
| Grading Management | GM | US-GM-01 |
| Payment & Subscription Management | PM | Future detailed stories |
| Notification Management | NM | Future detailed stories |
| Parent Portal | PP | Future detailed stories |
| Reporting & Analytics | RA | Future detailed stories |
| Administration | AD | Future detailed stories |

## 5. Module 01 - Identity & Access Management

### Purpose

Handles authentication, user accounts, roles, authorization, and basic access control.

### MVP Responsibilities

- Student registration
- Parent registration
- Login/logout
- Teacher account submission for approval
- Admin approval/rejection of teacher accounts
- Basic profile update
- Role-based access control

### Actors

| Actor | Needs |
| --- | --- |
| Student | Create account, log in, access enrolled learning content |
| Parent | Create account, link to student, view progress, redeem codes |
| Teacher | Access teacher dashboard after approval |
| Admin | Approve teachers and manage user access |

### Business Rules

- Students can register without parent approval.
- Parents can register and link to students using student ID.
- Teacher cannot publish courses before admin approval.
- Each user has one primary role in MVP: Student, Parent, Teacher, or Admin.
- Users can access only screens and actions allowed for their role.
- Admin actions should be auditable.
- Duplicate phone or email is not allowed for registration.

### Key Entities

| Entity | Key Fields |
| --- | --- |
| User | Id, name, phone, email, password hash, role, status |
| StudentProfile | UserId, studentId, secondaryYear |
| ParentProfile | UserId |
| TeacherProfile | UserId, subject, bio, profileImageUrl, documents, approvalStatus |

### Core Flows

1. Student registers.
2. System validates duplicate phone/email.
3. Student account is created.
4. Student logs in and accesses student dashboard.

Teacher approval flow:

1. Teacher submits profile and documents.
2. Admin reviews teacher data.
3. Admin approves or rejects.
4. Approved teacher can access teacher course features.

### Story References

- US-IM-01 Student Registration
- US-IM-02 Parent Registration
- US-IM-03 Teacher Account Approval
- US-IM-04 Admin User Management

## 6. Module 02 - Teacher Management

### Purpose

Manages teacher profile lifecycle from onboarding and verification to status management.

### MVP Responsibilities

- Teacher onboarding
- Profile management
- Verification documents
- Admin approval/rejection
- Teacher status management
- Verified subject control for course creation

### Actors

| Actor | Needs |
| --- | --- |
| Teacher | Complete profile, upload documents, select teaching subject, become approved |
| Admin | Review applications, approve/reject teachers, suspend/reactivate teachers |

### Business Rules

- Teacher must provide name, phone, subject, bio, profile image, and documents.
- Teacher account remains pending until admin approval.
- Rejected teacher cannot publish courses.
- Rejection requires a reason.
- Suspended teacher cannot create new courses.
- New enrollments are blocked for suspended teacher courses.
- Existing enrolled students keep access if teacher is suspended.
- National ID and phone should be unique.
- Teacher can create courses only for verified subjects.

### Key Entities

| Entity | Key Fields |
| --- | --- |
| TeacherProfile | UserId, fullName, nationalId, bio, profileImageUrl, yearsOfExperience, approvalStatus, accountStatus |
| TeacherDocument | Id, teacherId, documentType, fileUrl, uploadedAt |
| TeacherSubjectLink | Id, teacherId, subjectId, status |
| TeacherAuditLog | Id, teacherId, action, adminId, timestamp, reason |

### Core Flows

Teacher onboarding:

1. Teacher registers.
2. Teacher completes profile.
3. Teacher uploads documents.
4. System marks teacher as pending approval.
5. Admin approves or rejects.

Teacher suspension:

1. Admin suspends teacher.
2. Teacher loses ability to create/manage new teaching activities.
3. New enrollments in teacher courses are blocked.
4. Existing students keep access.

### Story References

- US-TM-01 Complete Teacher Profile
- US-TM-02 Edit Teacher Profile
- US-TM-03 Review Teacher Application
- US-TM-04 Reject Teacher With Reason
- US-TM-05 Suspend Teacher Account
- US-TM-06 Prevent Duplicate Teacher Accounts
- US-TM-07 Create Courses for Verified Subjects

## 7. Module 03 - Student Management

### Purpose

Manages student profile, enrolled course visibility, learning activity, progress, and parent monitoring access.

### MVP Responsibilities

- Student profile management
- Student enrolled courses dashboard
- Progress tracking
- Parent read-only progress view
- Admin student account management

### Future Responsibilities

- Attendance tracking
- Student notifications

### Actors

| Actor | Needs |
| --- | --- |
| Student | View enrolled courses, track progress |
| Parent | Monitor linked student progress |
| Teacher | View progress for students enrolled in own courses |
| Admin | Manage student accounts |

### Business Rules

- Student can access only enrolled and authorized course content.
- Student progress updates after lesson completion.
- Automatic lesson completion happens after watching 90% of video.
- Parent can view only linked student data.
- Parent cannot modify student academic data.
- Attendance is future scope.
- Notifications are future scope.

### Key Entities

| Entity | Key Fields |
| --- | --- |
| StudentProfile | StudentId, userId, secondaryYear, status |
| Enrollment | EnrollmentId, studentId, courseId, status |
| LessonProgress | Id, studentId, lessonId, completionStatus, completedAt |
| ParentStudentLink | Id, parentId, studentId |

### Core Flows

Progress flow:

1. Student opens enrolled lesson.
2. Student watches lesson or marks it complete.
3. System records progress.
4. Progress is visible to student, linked parent, and course teacher.

### Story References

- US-SM-01 Update Student Profile
- US-SM-02 View Enrolled Courses
- US-SM-03 Track Student Progress
- US-SM-04 Parent Monitors Student Progress
- US-SM-05 Admin Manages Student Records
- US-SM-06 Record Attendance - Future
- US-SM-07 Student Notifications - Future

## 8. Module 04 - Content & Course Management

### Purpose

Responsible for creating, organizing, publishing, and delivering courses and learning materials.

### MVP Responsibilities

- Create and edit course drafts
- Manage course metadata: title, description, thumbnail, price, year, subject, term, chapter
- Organize course structure
- Upload videos and documents
- Submit courses for review
- Admin publishes approved courses
- Student browses published courses
- Enrolled student accesses course content
- Lesson quiz progression

### Future Responsibilities

- Archive/delete/restore course lifecycle
- Free course enrollment
- Automated policy review
- Attendance tracking

### Actors

| Actor | Needs |
| --- | --- |
| Teacher | Create, organize, submit, and manage course content |
| Student | Browse courses and access enrolled content |
| Admin | Approve and publish courses |

### Business Rules

- Only approved teachers can create and manage courses.
- Teacher owns their own courses.
- Draft courses are visible only to their owner and admin.
- Published courses are visible in the catalog.
- Student can access course content only after enrollment.
- Unenrolled student can view course details and syllabus only.
- Course must be linked to curriculum data.
- Course publishing requires admin approval in MVP.
- Course archive/delete/restore is future scope.
- Free course enrollment is future scope.

### Key Entities

| Entity | Key Fields |
| --- | --- |
| Course | Id, title, description, status, price, teacherId, yearId, subjectId, termId, chapterId |
| Category | Id, name |
| Tag | Id, name |
| Subject | Id, name |
| CourseModule | Id, courseId, title, order |
| Lesson | Id, moduleId, title, order, status |
| Video | Id, lessonId, mediaFileId, duration |
| Document | Id, lessonId, mediaFileId |
| MediaFile | Id, fileUrl, fileType, size |

### Core Flows

Course creation flow:

1. Approved teacher creates course draft.
2. Teacher adds curriculum classification.
3. Teacher creates modules and lessons.
4. Teacher uploads videos/documents.
5. Teacher submits course for review.
6. Admin approves and publishes course.
7. Course appears in catalog.

Content access flow:

1. Student opens course details.
2. Student buys/enrolls in course.
3. Student opens lesson.
4. System checks active enrollment.
5. Student can watch authorized content.

### Story References

- US-CM-01 Create Course Draft
- US-CM-02 Organize Course Structure
- US-CM-03 Upload Learning Materials
- US-CM-04 Submit Course for Review
- US-CM-05 Publish Course
- US-CM-06 Browse Courses
- US-CM-07 Access Enrolled Course Content
- US-CM-08 Lesson Quiz Progression
- US-CM-09 Archive/Delete/Restore Course - Future
- US-CM-10 Free Course Enrollment - Future

## 9. Module 05 - Enrollment Management

### Purpose

Controls the relationship between student purchase, course enrollment, and course content access.

### MVP Responsibilities

- Enroll student in paid course after balance purchase
- Prevent duplicate enrollment
- Enforce course content access by enrollment status
- Show enrolled students to teacher as read-only
- Preserve access when teacher is suspended
- Mark enrollment complete
- Support manual refund handling

### Future Responsibilities

- Advanced refund request workflow
- Pending refund status
- Automated refund approval/rejection flow
- Free course enrollment

### Actors

| Actor | Needs |
| --- | --- |
| Student | Buy/enroll in course, view enrolled courses, access content |
| Teacher | View enrolled students and progress |
| Admin | Handle support cases and manual refunds |
| System | Enforce access and duplicate enrollment rules |

### Business Rules

- Student can enroll only in published courses.
- Student must have enough balance before buying course.
- Student balance cannot become negative.
- Student cannot enroll in the same course twice.
- Enrollment and balance deduction must happen in one transaction.
- Only active enrollment grants paid content access.
- Teacher can view enrollments for own courses only.
- Teacher cannot modify or delete enrollment records.
- If teacher is suspended, new enrollments are blocked but existing enrolled students keep access.
- Manual refund is allowed only if student has not used any course content.
- No refund after the student buys a course and watches lessons.

### Key Entities

| Entity | Key Fields |
| --- | --- |
| Enrollment | Id, studentId, courseId, status, enrollmentDate, priceAtEnrollment |
| EnrollmentAuditLog | Id, enrollmentId, action, performedBy, timestamp, reason |
| StudentBalance | StudentId, currentAmount |
| BalanceTransaction | Id, studentId, amount, type, reason, createdBy |

### Core Flows

Paid enrollment flow:

1. Student selects published course.
2. System checks student balance.
3. System checks duplicate enrollment.
4. System deducts balance.
5. System creates active enrollment.
6. Student gets course access.

Manual refund flow:

1. Student requests refund outside system.
2. Admin checks if course was unused.
3. If eligible, admin resets balance to 0.
4. Money return happens manually outside the platform.
5. Action is logged.

### Story References

- US-EM-01 Enroll in Paid Course
- US-EM-02 Prevent Duplicate Enrollment
- US-EM-03 Enrollment Access Control
- US-EM-04 View Enrolled Students
- US-EM-05 Preserve Access When Teacher Is Suspended
- US-EM-06 Mark Enrollment Completed
- US-EM-07 Manual Refund Handling
- US-EM-08 Advanced Refund Workflow - Future

## 10. Module 06 - Assessment Management

### Purpose

Manages creation, publishing, submission, and review of assessments, quizzes, exams, assignments, questions, and answers.

### MVP Responsibilities

- Create exams
- Create quizzes
- Add questions
- Publish assessments
- Student submits answers
- Track attempts and completion status
- Teacher reviews submissions when needed
- Parent views linked student assessment results

### Future Responsibilities

- Assessment notifications and reminders
- Advanced scheduling rules
- Late submission penalties
- Advanced retake approvals

### Actors

| Actor | Needs |
| --- | --- |
| Student | Take quizzes/exams, submit answers, view grades and feedback |
| Teacher | Create assessments, questions, review submissions, publish results |
| Parent | Monitor linked student assessment results |
| Admin | Manage assessment settings and reports |

### Business Rules

- Only approved teachers can create assessments.
- Assessment can be published only if it has at least one question.
- Student can access assessments only for enrolled courses.
- Student cannot submit after deadline if a deadline exists.
- Each assessment must have a grading rule.
- Assessment results must be stored for reporting.
- Quiz retry is allowed in MVP.
- Attempts must be stored separately.
- Published active assessments should not be modified in a way that breaks existing attempts.

### Key Entities

| Entity | Key Fields |
| --- | --- |
| Assessment | Id, courseId, lessonId, title, type, startDate, dueDate, totalMarks, status |
| Question | Id, assessmentId, questionText, questionType, marks |
| Answer | Id, questionId, studentId, answerText |
| Submission | Id, studentId, assessmentId, submittedAt, status |
| AssessmentAttempt | Id, assessmentId, studentId, attemptNumber, startedAt, submittedAt |
| GradingRule | Id, assessmentId, passingScore, weight |

### Core Flows

Assessment flow:

1. Teacher creates assessment.
2. Teacher adds questions and grading rule.
3. Teacher publishes assessment.
4. Student opens assessment from enrolled course.
5. Student submits answers.
6. System stores attempt.
7. Grading module calculates or stores result.

### Story References

- US-AM-01 Create Exam
- US-AM-02 Create Quiz
- US-AM-03 Add Questions
- US-AM-04 Publish Assessment
- US-AM-05 Submit Assessment Answers
- US-AM-06 Review Submissions
- US-AM-07 View Assessment Results
- US-AM-08 Assessment Notifications - Future

## 11. Module 07 - Grading Management

### Purpose

Handles scoring, grading, result generation, result publication, grade modification, and grading audit history.

### MVP Responsibilities

- Automatically grade objective questions
- Allow manual essay grading
- Calculate score, percentage, and pass/fail status
- Generate draft results
- Publish results
- Allow result modification with reason
- Let students view own published results
- Let parents view linked student grades
- Let admin monitor grading audit

### Future Responsibilities

- Result notifications
- Advanced analytics
- Exam review mode
- Multiple exam attempts policy beyond quiz retry

### Actors

| Actor | Needs |
| --- | --- |
| Student | View published results |
| Teacher | Grade, review, publish, and modify results |
| Parent | View linked student's grades |
| Admin | Monitor grading audit |

### Business Rules

- Student cannot receive results before submission.
- Objective questions are graded automatically.
- Essay questions require teacher grading.
- Result is not generated until grading is complete.
- Score cannot exceed maximum score.
- Student can view only own published results.
- Parent can view only linked student grade data.
- Teacher can grade only assessments belonging to own courses.
- Generated result remains hidden until teacher publishes it.
- Published result can be modified only with valid reason.
- All grading and modification actions are logged.

### Key Entities

| Entity | Key Fields |
| --- | --- |
| ExamGrade | Id, studentId, examId, attemptNumber, score, passFailStatus, gradingStatus |
| QuestionGrade | Id, gradeId, questionId, score, gradedBy |
| Result | Id, studentId, assessmentId, score, maxScore, percentage, isPassed, status, generatedAt, publishedAt |
| ResultModificationLog | Id, resultId, teacherId, oldScore, newScore, reason, modifiedAt |
| CourseGrade | Id, studentId, courseId, weightedAverage, passFailStatus |
| GradingAuditLog | Id, gradeId, actionType, performedBy, actionAt, notes |

### Core Flows

Result generation flow:

1. Student submits assessment.
2. System grades objective questions.
3. Teacher grades manual questions if needed.
4. System generates draft result.
5. Teacher reviews result.
6. Teacher publishes result.
7. Student and linked parent can view published result.

Result modification flow:

1. Teacher requests result modification.
2. System requires reason.
3. Teacher updates score.
4. System recalculates result.
5. System records audit log.

### Story References

- US-GM-01 Automatic Objective Grading
- US-GM-02 Manual Essay Grading
- US-GM-03 Generate Result
- US-GM-04 Publish Results
- US-GM-05 Modify Result With Reason
- US-GM-06 Student Views Results
- US-GM-07 Parent Views Grades
- US-GM-08 Admin Monitors Grading
- US-GM-09 Result Notifications - Future

## 12. Module 08 - Payment & Subscription Management

### Purpose

Handles prepaid codes and student balance in MVP.

Payment gateway, subscriptions, and invoices are future scope.

### MVP Responsibilities

- Generate prepaid codes
- Cancel active prepaid codes
- Redeem prepaid code into student balance
- Manage student balance
- Admin manually adds/subtracts balance
- Track code serial numbers for manual distribution

### Future Responsibilities

- Payment gateway
- Subscriptions
- Invoices
- Online wallet integrations

### Business Rules

- Prepaid code has a value such as 50 EGP or 100 EGP.
- Codes are generated in the database.
- Codes are manually distributed in MVP.
- Code does not expire.
- Code can be redeemed only once.
- One code is redeemed for one student only.
- Parent can redeem code for one linked student.
- Code has serial number for manual tracking.
- Admin can cancel active code.
- Balance can be partially used across multiple courses.
- Balance cannot become negative.
- Admin can manually add/subtract balance.

### Key Entities

| Entity | Key Fields |
| --- | --- |
| PrepaidCode | Id, code, serialNumber, value, status, createdAt, cancelledAt |
| CodeRedemption | Id, prepaidCodeId, studentId, redeemedByUserId, redeemedAt |
| StudentBalance | StudentId, currentAmount |
| BalanceTransaction | Id, studentId, amount, type, reason, createdBy, createdAt |

### Core Flows

Code redemption flow:

1. Student or parent enters prepaid code.
2. System validates code exists, active, and unused.
3. System links redemption to one student.
4. System adds code value to student balance.
5. System marks code as redeemed.
6. System records balance transaction.

### Story References

Detailed Module 08 user stories still need to be added.

Related backlog items:

- PB-47 Prepaid code generation
- PB-48 Prepaid code redemption
- PB-49 Student balance management

## 13. Module 09 - Notification Management

### Status

Future scope.

Do not block MVP functionality on notification delivery.

### Future Responsibilities

- Email notifications
- In-app notifications
- Alerts and reminders
- Assessment reminders
- Result notifications
- Course update notifications

## 14. Module 10 - Parent Portal

### Purpose

Provides parents with visibility into linked student progress and grades.

### MVP Responsibilities

- Parent registration is handled by Identity & Access.
- Parent-student link uses student ID.
- Parent can view linked student progress.
- Parent can view linked student assessment results and grades.
- Parent can redeem prepaid code for one linked student.

### Future Responsibilities

- Parent approval workflow
- Advanced parent dashboard
- Parent notifications

## 15. Module 11 - Reporting & Analytics

### Purpose

Provides basic operational reports for admins and teachers.

### MVP Reports

- Codes report
- Enrollment report
- Teacher sales report
- Student progress report

### Business Rules

- Reports must respect role and ownership.
- Teacher sees only own course reports.
- Parent sees only linked student progress/grades.
- Admin can see platform-wide reports.

### Story References

Detailed Module 11 user stories still need to be added.

Related backlog item:

- PB-50 Basic code, enrollment, sales, and progress reports

## 16. Module 12 - Administration

### Purpose

Handles system-wide administration and configuration.

### MVP Responsibilities

- User management
- Teacher approval
- Course approval
- Curriculum data management
- Prepaid code management
- Balance management
- Reports access

### Future Responsibilities

- System monitoring
- Platform configuration
- Advanced admin settings

## 17. Cross-Module Rules

| Rule | Applies To |
| --- | --- |
| Role-based access must be checked on backend APIs, not only frontend screens. | All modules |
| Teacher can manage only own courses and assessments. | Teacher, Course, Assessment, Grading |
| Parent can read only linked student data. | Student, Parent, Assessment, Grading |
| Student can access paid content only with active enrollment. | Enrollment, Content |
| Balance operations must be transactional and auditable. | Payment, Enrollment |
| Code redemption must prevent duplicate use. | Payment |
| Enrollment purchase must prevent duplicate enrollment. | Enrollment |
| Quiz retries must create separate attempts. | Assessment, Grading |
| Sensitive admin actions require audit logs. | Admin, Teacher, Payment, Grading |

## 18. Recommended API Areas

These are not final endpoints, but they help developers organize controllers/services.

| API Area | Examples |
| --- | --- |
| Identity | register, login, logout, current user |
| Teachers | teacher profile, document upload, approval, status |
| Students | student profile, dashboard, progress |
| Courses | course draft, course structure, lessons, materials, publish |
| Catalog | browse courses, filter, course details |
| Payments | prepaid code generation, redemption, balance |
| Enrollments | course purchase, enrollment status, enrolled students |
| Assessments | create assessment, questions, publish, submit attempt |
| Grading | grade submission, generate result, publish result, modify result |
| Reports | codes, enrollments, teacher sales, student progress |
| Admin | user management, curriculum, approvals, settings |

## 19. Suggested Build Order

1. Identity & Access Management
2. Teacher Management
3. Student Management basics
4. Content & Course Management
5. Payment enablers: prepaid codes and balance
6. Enrollment Management
7. Video lessons and progress tracking
8. Assessment Management
9. Grading Management
10. Parent progress and grade views
11. Basic reports

## 20. Open Items To Add Later

These items are known gaps for future refinement:

- Detailed Module 08 user stories for prepaid code and balance
- Detailed Module 11 user stories for reports
- Final API contracts
- Final database schema
- Wireframes
- Non-functional requirements by priority
- Detailed audit log fields
- Detailed course publishing workflow states
