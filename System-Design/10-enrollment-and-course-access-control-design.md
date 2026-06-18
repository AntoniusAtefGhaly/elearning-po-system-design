# Step 12 - Enrollment and Course Access Control Design

## Purpose

Define when a student can enroll in a course and when any user can access course content.

## Core Rules

- Students can browse only approved and published courses.
- Students can view public course details before enrollment.
- Students can access lessons, videos, quizzes, and progress only after enrollment.
- A student cannot enroll in the same course twice.
- A student cannot enroll if balance is not enough.
- Enrollment and balance deduction must happen in one transaction.
- Unpublished courses must not be accessible to students.

## Access Matrix

| Resource | Student | Parent | Teacher | Education Center | Admin |
| --- | --- | --- | --- | --- | --- |
| Course catalog | Published only | Published only | Published only | Published only | All |
| Course draft | No | No | Own courses | Linked teacher courses if allowed | All |
| Lesson metadata | Enrolled courses | No | Own courses | Linked teacher courses | All |
| Video playback | Enrolled courses | No | Own courses preview | No by default | Support only |
| Quiz taking | Enrolled courses | No | No | No | No |
| Progress | Own | Linked students | Own course students | Linked teacher course students | All |

## Enrollment Flow

```text
1. Student requests enrollment.
2. Backend authenticates user.
3. Backend confirms user is a student.
4. Backend loads course.
5. Backend confirms course is approved and published.
6. Backend checks no existing enrollment.
7. Backend loads student balance with concurrency protection.
8. Backend confirms balance is enough.
9. Backend deducts balance.
10. Backend creates balance transaction.
11. Backend creates enrollment.
12. Backend commits transaction.
```

## Content Access Flow

```text
1. Student requests lesson, quiz, or video access.
2. Backend authenticates user.
3. Backend loads requested resource.
4. Backend confirms resource belongs to a published course.
5. Backend confirms student is enrolled in that course.
6. Backend allows access.
```

## Required Constraints

```text
Enrollments unique StudentId + CourseId
Courses must have ApprovalStatus and PublicationStatus
StudentBalances.CurrentAmount >= 0
```

## Developer Notes

- Do not rely on Angular route guards for paid access.
- Backend must check enrollment for lesson, quiz, progress, and video-token endpoints.
- Store `Enrollment.PurchaseAmount` to preserve historical sales reports.

