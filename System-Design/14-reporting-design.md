# Step 14 - Reporting Design

## Purpose

Define MVP reports, ownership rules, and data sources.

## MVP Reports

| Report | Audience | Data Source |
| --- | --- | --- |
| Course enrollment report | Admin, Teacher, Center | Enrollments, Courses, Students |
| Prepaid code report | Admin | PrepaidCodes, CodeRedemptions |
| Teacher sales report | Admin, Teacher, Center | Enrollments, Courses, Teachers |
| Student progress report | Admin, Parent, Teacher, Center | LessonProgress, QuizAttempts, Enrollments |
| Balance transaction report | Admin | BalanceTransactions |

## Authorization Rules

- Admin can see all reports.
- Teacher can see only own course reports.
- Center can see only linked teacher/course reports.
- Parent can see only linked student progress.
- Student can see own learning progress.

## Reporting Principles

- Reports must use backend authorization filters.
- Use `Enrollment.PurchaseAmount` for historical sales, not current course price.
- Use pagination for large reports.
- Start with real-time SQL queries.
- Move heavy reports to background jobs/read models only when needed.

## Common Filters

```text
Date range
Teacher
Course
Subject
Secondary year
Student
Code status
Center
```

## Developer Notes

- Do not build reports directly from frontend filtering of all data.
- Do not expose admin report endpoints to teachers/centers.
- Add indexes after identifying report query patterns.

