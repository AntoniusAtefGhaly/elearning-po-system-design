# Step 07 - API Design

## 1. Purpose

This step designs the Backend API surface for the E-learning MVP.

It answers:

- What API resources should exist?
- What endpoint groups are needed?
- Which endpoints are sensitive?
- Where must authorization be enforced?
- How should the most important flows behave?

This is not final OpenAPI/Swagger documentation. It is architecture-level API design.

## 2. API Style

Recommended style:

```text
REST-style JSON APIs over HTTPS
```

Why REST fits the MVP:

- The product is resource-oriented: users, courses, lessons, enrollments, codes, quizzes, progress.
- It is easy for web frontend teams to consume.
- It is simple enough for an MVP.
- It can be documented with OpenAPI later.

## 3. API Design Principles

### Principle 1 - Backend Owns Authorization

The frontend can hide buttons, but the backend must enforce all access rules.

Every sensitive endpoint must check:

- Current user identity
- User role
- Resource ownership
- Parent-student link
- Teacher-course ownership
- Enrollment status
- Course publication status

### Principle 2 - Commands Should Express Business Actions

Some APIs are not simple CRUD.

Examples:

```text
POST /api/prepaid-codes/redeem
POST /api/courses/{courseId}/enrollments
POST /api/courses/{courseId}/submit-for-approval
POST /api/admin/courses/{courseId}/approve
POST /api/lessons/{lessonId}/playback-access
POST /api/quizzes/{quizId}/attempts
```

These names are acceptable because they represent business actions.

### Principle 3 - Never Trust IDs From the Client Alone

If the client sends:

```text
studentId
courseId
teacherId
```

The backend must verify the current user is allowed to act on those IDs.

### Principle 4 - Sensitive Operations Need Idempotency or Duplicate Protection

Important flows:

- Code redemption
- Course enrollment
- Quiz submission

Protection can come from:

- Unique database constraints
- Idempotency keys, if needed
- Backend duplicate checks
- Transactions

### Principle 5 - Use Consistent Error Shape

All errors should return a consistent response shape.

Example:

```json
{
  "error": {
    "code": "INSUFFICIENT_BALANCE",
    "message": "Student balance is not enough to enroll in this course."
  }
}
```

## 4. Main API Groups

```text
/api/auth
/api/me
/api/students
/api/parents
/api/teachers
/api/curriculum
/api/courses
/api/lessons
/api/prepaid-codes
/api/balances
/api/enrollments
/api/quizzes
/api/progress
/api/reports
/api/admin
```

## 5. Authentication APIs

```text
POST /api/auth/register/student
POST /api/auth/register/parent
POST /api/auth/login
POST /api/auth/logout
GET  /api/me
```

Notes:

- Student registration does not require parent approval.
- Teacher accounts require admin approval.
- Password reset is likely needed later, even if not explicitly documented.

## 6. Student and Parent APIs

### Student

```text
GET /api/students/{studentId}
GET /api/students/{studentId}/balance
GET /api/students/{studentId}/enrollments
GET /api/students/{studentId}/progress
```

Authorization:

- Student can access own data.
- Parent can access linked student data.
- Teacher can access limited progress only for students enrolled in own courses.
- Admin can access all.

### Parent

```text
POST /api/parents/{parentId}/student-links
GET  /api/parents/{parentId}/students
DELETE /api/parents/{parentId}/student-links/{studentId}
```

Link request example:

```json
{
  "studentCode": "STU-2026-000123"
}
```

MVP rule:

Parent links to student using student ID/code. No approval workflow in MVP.

## 7. Teacher APIs

```text
GET   /api/teachers/{teacherId}
PATCH /api/teachers/{teacherId}
GET   /api/teachers/{teacherId}/courses
GET   /api/teachers/{teacherId}/reports/enrollments
GET   /api/teachers/{teacherId}/reports/progress
```

Authorization:

- Teacher can manage own profile and courses.
- Admin can manage all teachers.

## 8. Curriculum APIs

```text
GET /api/curriculum/secondary-years
GET /api/curriculum/subjects
GET /api/curriculum/terms
GET /api/curriculum/chapters
```

Admin management:

```text
POST   /api/admin/curriculum/secondary-years
POST   /api/admin/curriculum/subjects
POST   /api/admin/curriculum/terms
POST   /api/admin/curriculum/chapters
PATCH  /api/admin/curriculum/chapters/{chapterId}
DELETE /api/admin/curriculum/chapters/{chapterId}
```

Notes:

- Public read endpoints can be cached.
- Admin write endpoints require audit logs if changes affect published content.

## 9. Course and Lesson APIs

### Course Catalog

```text
GET /api/courses
GET /api/courses/{courseId}
```

Common filters:

```text
secondaryYearId
subjectId
termId
chapterId
teacherId
page
pageSize
```

Rules:

- Public/student catalog returns only approved and published courses.
- Draft or rejected courses are not visible to students.

### Teacher Course Management

```text
POST  /api/teacher/courses
GET   /api/teacher/courses/{courseId}
PATCH /api/teacher/courses/{courseId}
POST  /api/teacher/courses/{courseId}/submit-for-approval
POST  /api/teacher/courses/{courseId}/lessons
PATCH /api/teacher/lessons/{lessonId}
DELETE /api/teacher/lessons/{lessonId}
```

Authorization:

- Teacher can manage only own courses.

### Admin Course Approval

```text
GET  /api/admin/courses/pending-approval
POST /api/admin/courses/{courseId}/approve
POST /api/admin/courses/{courseId}/reject
PATCH /api/admin/courses/{courseId}/price
```

Approval request:

```json
{
  "notes": "Approved for MVP publishing."
}
```

Reject request:

```json
{
  "reason": "Course description is incomplete."
}
```

Audit required:

- Course approved
- Course rejected
- Course price edited by admin

## 10. Video APIs

```text
POST /api/lessons/{lessonId}/playback-access
POST /api/lessons/{lessonId}/progress-events
```

Playback access response:

```json
{
  "lessonId": "lesson-id",
  "playbackUrl": "https://video-provider.example/signed-url",
  "expiresAt": "2026-06-05T18:30:00Z"
}
```

Authorization:

- User must be an enrolled student for the course.
- Course must be approved and published.
- Lesson must belong to that course.

Important:

- Do not return permanent public video URLs.
- Use signed URLs or provider playback tokens.

Progress event request:

```json
{
  "watchedPercentage": 92,
  "currentSecond": 690,
  "durationSeconds": 750
}
```

Backend rule:

- If watched percentage is at least 90%, mark lesson complete automatically.

## 11. Prepaid Code and Balance APIs

### Admin Prepaid Code Management

```text
POST /api/admin/prepaid-codes
GET  /api/admin/prepaid-codes
POST /api/admin/prepaid-codes/{codeId}/cancel
```

Generate request:

```json
{
  "value": 100,
  "count": 50
}
```

Rules:

- Codes have fixed values.
- Codes do not expire.
- Codes have serial numbers.
- Cancelled or used codes cannot be redeemed.

### Redeem Code

```text
POST /api/prepaid-codes/redeem
```

Request:

```json
{
  "code": "ABC123XYZ",
  "studentId": "student-id"
}
```

Authorization:

- Student can redeem for self.
- Parent can redeem for linked student.
- Admin support behavior should be explicit if needed.

Transaction:

- Mark code as used.
- Create redemption history.
- Increase student balance.
- Create balance transaction.

### Balance APIs

```text
GET  /api/students/{studentId}/balance
GET  /api/students/{studentId}/balance-transactions
POST /api/admin/students/{studentId}/balance-adjustments
POST /api/admin/students/{studentId}/balance-reset
```

Manual adjustment request:

```json
{
  "amount": 50,
  "reason": "Manual correction after support case."
}
```

Rules:

- Balance cannot become negative.
- Every balance change must create a transaction.
- Admin manual changes must be audited.

## 12. Enrollment APIs

```text
POST /api/courses/{courseId}/enrollments
GET  /api/students/{studentId}/enrollments
GET  /api/enrollments/{enrollmentId}
```

Enroll request:

```json
{
  "studentId": "student-id"
}
```

For a normal student user, the backend can infer `studentId` from the current user. Parent enrollment is not clearly required in MVP, so avoid adding it unless confirmed.

Transaction:

- Validate course is published.
- Validate student is not already enrolled.
- Validate balance is enough.
- Deduct balance.
- Create balance transaction.
- Create enrollment.

Common errors:

```text
COURSE_NOT_AVAILABLE
ALREADY_ENROLLED
INSUFFICIENT_BALANCE
NOT_ALLOWED
```

## 13. Quiz APIs

### Teacher Quiz Management

```text
POST  /api/teacher/courses/{courseId}/quizzes
PATCH /api/teacher/quizzes/{quizId}
POST  /api/teacher/quizzes/{quizId}/questions
PATCH /api/teacher/quiz-questions/{questionId}
```

### Student Quiz Taking

```text
GET  /api/quizzes/{quizId}
POST /api/quizzes/{quizId}/attempts
GET  /api/quizzes/{quizId}/attempts/me
```

Attempt request:

```json
{
  "answers": [
    {
      "questionId": "question-id-1",
      "answerOptionId": "answer-option-id-1"
    }
  ]
}
```

Rules:

- Student must be enrolled in the course.
- Quiz must belong to the course or lesson.
- Student can retry quiz in MVP.
- Score is shown to student.
- Quiz result affects progress.

## 14. Progress APIs

```text
GET  /api/students/{studentId}/progress
GET  /api/courses/{courseId}/progress/me
POST /api/lessons/{lessonId}/complete
```

Manual lesson complete:

```json
{
  "source": "Manual"
}
```

Rules:

- Student can update own progress only for enrolled courses.
- Parent can read linked student progress.
- Teacher can read progress for students enrolled in own courses.
- Admin can read all progress.

## 15. Reports APIs

### Admin Reports

```text
GET /api/admin/reports/enrollments
GET /api/admin/reports/prepaid-codes
GET /api/admin/reports/teacher-sales
GET /api/admin/reports/student-progress
```

### Teacher Reports

```text
GET /api/teacher/reports/enrollments
GET /api/teacher/reports/progress
```

Rules:

- Reports must always be scoped by role and ownership.
- Report endpoints are read-heavy and may need pagination.
- Heavy reports can later move to background jobs or read models.

## 16. Admin APIs

```text
GET   /api/admin/users
PATCH /api/admin/users/{userId}/status
GET   /api/admin/teachers/pending-approval
POST  /api/admin/teachers/{teacherId}/approve
POST  /api/admin/teachers/{teacherId}/reject
GET   /api/admin/audit-logs
```

Audit required:

- User status changed
- Teacher approved/rejected
- Course approved/rejected
- Prepaid code generated/cancelled
- Balance adjusted/reset

## 17. API Security Checklist

For every endpoint, define:

```text
1. Who can call it?
2. Which role is required?
3. Which relationship is required?
4. Does the resource need to be published or approved?
5. Is the operation read-only or state-changing?
6. Does it need a transaction?
7. Does it need an audit log?
8. Does it expose sensitive data?
```

## 18. Endpoint Risk Table

| Endpoint | Risk | Required Protection |
| --- | --- | --- |
| `POST /api/prepaid-codes/redeem` | Duplicate redemption or wrong student balance | Transaction, unique constraints, parent/student authorization |
| `POST /api/courses/{courseId}/enrollments` | Free access or negative balance | Transaction, balance lock, enrollment uniqueness |
| `POST /api/lessons/{lessonId}/playback-access` | Paid video leakage | Enrollment check, short-lived video URL/token |
| `POST /api/quizzes/{quizId}/attempts` | Invalid quiz access or incorrect retry handling | Enrollment check, store each retry as a separate attempt |
| `GET /api/students/{studentId}/progress` | Parent/teacher data leakage | Relationship-based authorization |
| `POST /api/admin/students/{studentId}/balance-adjustments` | Admin abuse or support mistake | Admin permission, reason, audit log |
| `POST /api/admin/courses/{courseId}/approve` | Unreviewed content becomes visible | Admin permission, status transition, audit log |

## 19. Versioning Recommendation

For MVP, start simple:

```text
/api/...
```

When external clients or mobile apps appear, consider:

```text
/api/v1/...
```

Do not overcomplicate versioning before the API has stable external consumers.

## 20. Step 07 Conclusion

The API should be designed around business resources and business actions.

The most important API rule is:

> The backend must enforce every business rule and permission, even if the frontend already hides the action.

The highest-risk endpoints are prepaid code redemption, enrollment purchase, video playback access, quiz attempt submission, progress access, and admin balance changes.

The next step is authentication and authorization design.
