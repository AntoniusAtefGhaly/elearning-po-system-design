# Step 01 - Requirements to Architecture Drivers

## 1. System Goal

Build an Arabic-first E-learning website for Egyptian secondary school students where students can buy teacher courses using prepaid codes, watch recorded lessons, solve MCQ quizzes, and track learning progress.

The system also allows parents to monitor linked students, teachers to publish and manage courses, education centers to manage their teachers, and admins to control approvals, prepaid codes, balances, reports, and platform setup.

## 2. System Scope

### In Scope

- Student, parent, teacher, education center, and admin accounts
- Teacher and education center approval
- Course catalog organized by year, subject, term, chapter, and teacher
- Teacher course creation and admin course approval
- Recorded video lessons
- MCQ quizzes
- Student progress tracking
- Prepaid code generation, redemption, and balance management
- Paid course enrollment
- Parent-student linking
- Reports for admins, teachers, and education centers
- Admin audit trail for important actions
- Arabic web interface for mobile and desktop browsers

### Out of Scope for MVP

- Mobile app
- Live classes
- Chat or forums
- Certificates
- English interface
- Subject bundles
- Direct card or wallet payment
- Advanced video watermarking
- Parent-student link approval workflow

## 3. Actors

### Human Actors

1. Student
2. Parent
3. Teacher
4. Education Center
5. Admin

### External System Actors

1. Video streaming or video hosting service
2. Email/SMS notification provider, likely future need
3. External payment gateway, out of scope for MVP but likely future need

## 4. Functional Requirement Groups

### Identity and Access

- Users can log in and log out.
- Students and parents can create accounts.
- Teachers and education centers require admin approval.
- Users can update basic profile information.
- The system must enforce role-based access.

### Course Catalog

- Students can browse published courses.
- Students can filter courses by secondary year, subject, term, chapter, and teacher.
- Students can view course details before enrollment.
- Course details include teacher, price, description, lessons, and subject information.

### Course Management

- Teachers can create draft courses.
- Teachers can add lessons, video content, and MCQ quizzes.
- Teachers can submit courses for admin approval.
- Admin can approve or reject courses.
- Teacher can set course price, and admin can edit teacher course prices.

### Prepaid Code and Balance

- Admin can generate prepaid codes with fixed values.
- Student or parent can redeem a valid prepaid code.
- The system must reject invalid, used, or cancelled codes.
- Each prepaid code can be redeemed for one student only.
- Redeemed code value is added to the student's balance.
- Student balance can be used partially across multiple courses.
- Student balance cannot become negative.
- Admin can manually add, subtract, or reset student balance.

### Enrollment and Course Access

- Students can enroll in a paid course using their balance.
- Students can access only courses they are enrolled in.
- Students buy teacher courses separately.
- The system must prevent access to unpublished courses.

### Learning, Quiz, and Progress

- Students can watch enrolled video lessons.
- Videos should not be directly downloadable.
- Students can manually mark lesson completion.
- The system can automatically complete a lesson after watching 90% of the video.
- Students can solve MCQ quizzes.
- Student cannot retry a quiz in MVP.
- Quiz score is shown to the student.
- Quiz result affects course progress.

### Parent View

- Parents can link to student accounts using student ID.
- Parents can view linked student enrollments.
- Parents can view linked student progress.
- Parents can redeem prepaid codes for one linked student at a time.

### Admin and Reports

- Admin can manage users, teachers, education centers, and curriculum data.
- Admin can manage course approval status.
- Admin can manage prepaid codes.
- Admin can view course enrollment reports.
- Admin can view prepaid code reports.
- Admin can view teacher sales reports.
- Admin can view student progress reports.
- Teachers can view reports for their own courses.
- Education centers can view reports for their own teachers and courses.

## 5. Improved Non-Functional Requirements

| ID | Requirement | Architecture Meaning |
| --- | --- | --- |
| NFR-01 | The website must support Arabic RTL layout and Arabic content across all MVP screens. | UI components, layout, validation messages, and database text fields must support Arabic. |
| NFR-02 | The website must work on modern mobile and desktop browsers. | Responsive frontend design is required. |
| NFR-03 | Users must only access data allowed by their role and relationship to the data. | Authorization must check role, ownership, center relationship, parent-student link, enrollment, and course status. |
| NFR-04 | Video playback should start quickly and remain stable for normal student usage. | Video files should be served through a video hosting/streaming service or CDN, not directly from the application server. |
| NFR-05 | Important admin actions must be recorded with actor, action, target, timestamp, and relevant before/after data. | Add audit logging for approval, prepaid code, balance, and user-management actions. |
| NFR-06 | The system should support at least 1,000 concurrent active users for the MVP target. | Backend should be stateless where possible, database queries must be indexed, and heavy video traffic must be offloaded. |
| NFR-07 | Money-like operations must be consistent and protected from duplicate execution. | Prepaid code redemption, balance updates, and enrollment purchase need database transactions and idempotency protection. |
| NFR-08 | Student progress and quiz submissions must not be lost after successful submission. | Progress and quiz writes need durable storage, validation, and transaction boundaries. |

## 6. Architecture Drivers

### Driver 1 - Prepaid Code and Balance Correctness

Why it matters:

The MVP depends on prepaid codes instead of online payments. Bugs here can cause direct financial loss, incorrect student balances, duplicate redemptions, or support problems.

Architecture impact:

- Use relational database transactions.
- Make prepaid code redemption atomic.
- Ensure each code can be redeemed once only.
- Prevent negative student balance at the database and domain level.
- Store balance transaction history, not only the current balance.
- Audit admin balance adjustments.

### Driver 2 - Course Access Control

Why it matters:

Students must only access paid courses after enrollment. Teachers, centers, parents, and admins also need different visibility rules.

Architecture impact:

- Centralize authorization checks.
- Model ownership and relationships clearly.
- Course access should check enrollment, course approval status, and lesson ownership.
- Parent access should require an explicit parent-student link.
- Teacher reports should be scoped to their own courses.
- Center reports should be scoped to linked teachers/courses.

### Driver 3 - Video Playback and Protection

Why it matters:

Video is the heaviest content type. Serving videos through the backend would increase load, cost, and performance risk. The business also requires videos not to be directly downloadable.

Architecture impact:

- Store video metadata in the application database.
- Store/stream actual video files using an external video service or CDN.
- Use signed URLs, expiring tokens, or provider-level access controls.
- Do not expose permanent public video URLs.
- Track playback progress through frontend events sent to the backend.

### Driver 4 - Learning Progress and Quiz Integrity

Why it matters:

Progress affects the student experience, parent monitoring, teacher reports, and admin reports. Quiz results also affect course progress.

Architecture impact:

- Store lesson progress per student and lesson.
- Store quiz attempts and scores as durable records.
- Enforce "no retry in MVP" using backend rules, not only frontend UI.
- Use clear rules for progress calculation.
- Protect progress updates from invalid access.

### Driver 5 - Admin Approval and Auditability

Why it matters:

Teachers and courses cannot become visible without admin approval. Admins also manage prepaid codes and balances, which are sensitive operations.

Architecture impact:

- Use explicit status fields for teacher approval and course approval.
- Keep publish visibility separate from draft editing.
- Record audit logs for approval, rejection, code generation, code cancellation, and balance adjustment.
- Reports and support screens should be able to trace important changes.

## 7. Risky Requirements

| Requirement | Risk | Protection |
| --- | --- | --- |
| Student or parent redeems prepaid code. | Same code may be redeemed twice or redeemed for the wrong student. | Unique redemption constraint, transaction, code status check, redemption history. |
| Student balance cannot become negative. | Race conditions during purchase may overspend balance. | Database transaction, row locking or concurrency token, domain validation. |
| Student enrolls in a paid course. | Student may get access without valid payment or balance deduction. | Purchase/enrollment should happen in one transaction. |
| Students access only enrolled courses. | Unpaid users may access paid content. | Backend authorization on course, lesson, quiz, and video-token endpoints. |
| Videos should not be directly downloadable. | Public video links may be shared. | Signed expiring URLs or provider-level private video access. |
| Parent views linked student progress. | Parent may view unlinked student data. | Parent-student link table and authorization checks. |
| Teacher views course reports. | Teacher may see another teacher's data. | Ownership checks on every report query. |
| Center views teacher/course reports. | Center may see data for unlinked teachers. | Center-teacher relationship checks. |
| Admin manually adjusts balance. | Mistakes or abuse may affect money-like records. | Audit log, reason field, balance transaction ledger. |
| Quiz retry is not allowed. | Student may submit multiple attempts by refreshing or calling API directly. | Backend unique rule per student and quiz. |

## 8. Initial Architecture Recommendation

### Recommended Style

Use a Modular Monolith with Clean Architecture boundaries.

### Why This Fits the MVP

- The MVP has many business modules, but they are still tightly connected.
- Balance, enrollment, progress, and reports need consistent shared data.
- One deployable backend is simpler to build, test, deploy, and operate.
- Clear internal modules can prevent the codebase from becoming messy.
- Future services can be extracted later if real scale or team boundaries require it.

### Why Not Microservices Now

- The current scale target does not justify distributed-system complexity.
- Microservices would make transactions across balance, enrollment, and reporting harder.
- The team would need more DevOps, monitoring, deployment, and failure-handling maturity.
- Most modules still need shared business rules and coordinated data.

## 9. Proposed Backend Modules

1. Identity and Access
2. Users and Profiles
3. Teachers and Education Centers
4. Curriculum
5. Courses and Lessons
6. Video Metadata and Access Tokens
7. Prepaid Codes and Balance
8. Enrollment
9. Learning Progress
10. Quizzes
11. Reports
12. Audit Logs

## 10. Data Storage Recommendation

Use a relational database as the primary database.

Reasons:

- The domain has strong relationships between students, parents, teachers, centers, courses, lessons, enrollments, quizzes, and payments.
- Prepaid code redemption and student balance need transactions.
- Reports require structured queries.
- Authorization depends on relationships and ownership.

Possible later additions:

- Cache for course catalog and frequently-read lookup data.
- Object storage or video provider storage for actual video files.
- Search engine if course search becomes advanced.

## 11. Open Architecture Questions

1. What exact video hosting/streaming provider will be used?
2. What does "stable video playback" mean in measurable terms?
3. How many concurrent users should the MVP support at launch?
4. Should education center data be treated as tenant-isolated data?
5. Can a student belong to more than one education center, or are students platform-wide?
6. Should admin balance adjustment require a reason and approval, or only an audit log?
7. Should parent-student linking require student confirmation in a later phase?
8. Are reports expected to be real-time, near-real-time, or daily summaries?
9. Should the system support multiple devices watching the same course at the same time?
10. What is the required retention period for audit logs and financial-like balance history?

## 12. Step 01 Conclusion

The first architecture decision is to keep the MVP as a Modular Monolith with clear internal module boundaries and a relational database.

The highest-risk areas are prepaid code redemption, student balance, enrollment, paid content access, video access protection, role-based permissions, and progress/quiz correctness.

The next design step is the System Context Diagram.

