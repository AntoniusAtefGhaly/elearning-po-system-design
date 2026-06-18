# Step 13 - Progress and Quiz Tracking Design

## Purpose

Define how lesson progress, video completion, and quiz attempts are stored and calculated.

## Core Rules

- Lesson completion can be manual or automatic.
- Automatic completion happens after watching 90% of video.
- MVP quizzes are MCQ only.
- Student cannot retry a quiz in MVP.
- Quiz result affects course progress.
- Progress must be visible to student, linked parent, teacher, center, and admin according to permissions.

## Data Records

```text
LessonProgress
- StudentId
- LessonId
- WatchedPercentage
- IsCompleted
- CompletionSource
- CompletedAt

QuizAttempt
- StudentId
- QuizId
- Score
- SubmittedAt

CourseProgress
- Can be calculated from LessonProgress and QuizAttempt
- Store only if performance requires it
```

## Video Progress Flow

```text
1. Student watches video.
2. Angular sends progress event every 15-30 seconds and on pause/end.
3. Backend validates enrollment.
4. Backend updates LessonProgress.
5. If watched percentage >= 90, backend marks lesson completed.
```

## Quiz Submission Flow

```text
1. Student submits quiz answers.
2. Backend validates enrollment.
3. Backend checks no existing attempt for StudentId + QuizId.
4. Backend scores answers.
5. Backend stores QuizAttempt.
6. Backend updates progress if quiz affects progress.
```

## Required Constraints

```text
LessonProgress unique StudentId + LessonId
QuizAttempts unique StudentId + QuizId
WatchedPercentage between 0 and 100
```

## Developer Notes

- Do not enforce quiz retry rule only in Angular.
- Keep scoring logic in backend.
- Avoid sending video progress every second.
- Reports should read progress through authorized queries only.

