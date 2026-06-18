# E-Learning Website - Business Gaps and Clarifications

## 1. Purpose

This document lists business gaps and questions to answer later.

These items do not block the training project now, but they should be clarified before real implementation.

## 1.1 Future Scope Decisions

The following conflicts are intentionally moved to future scope:

- Free course enrollment
- Course archive/delete/restore lifecycle
- Notifications
- Attendance tracking
- Direct payment gateway
- Subscriptions and invoices

## 2. High Priority Gaps

| ID | Gap / Question | Notes |
| --- | --- | --- |
| GAP-01 | What is the course access duration after purchase? | Forever, until end of term, or until school year ends |
| GAP-02 | If course price changes, does it affect only new students or existing enrolled students too? | Recommended: new students only |
| GAP-03 | Who approves refund requests? | Admin only, or another role |
| GAP-04 | When refund happens, does the system cancel code/redemption records or only reset balance? | Current rule: admin resets balance to 0 and money is returned manually |
| GAP-05 | How do we prevent wrong parent-student linking using only student ID? | Could use student approval, OTP, or share code later |
| GAP-06 | What is the platform commission percentage? | Needed for real revenue reporting |
| GAP-07 | When is teacher sale counted? | At purchase time, after lesson start, or after refund period |

## 3. Medium Priority Gaps

| ID | Gap / Question | Notes |
| --- | --- | --- |
| GAP-08 | Who receives manually distributed prepaid codes? | Student, parent, or teacher |
| GAP-09 | Should code status include generated, distributed, used, and cancelled? | Current simple status: active, used, cancelled |
| GAP-10 | Should admin enter a reason when adding/subtracting balance? | Recommended: yes, for audit |
| GAP-11 | How much does quiz affect course progress? | Example: lessons 80%, quizzes 20% |
| GAP-12 | If teacher edits an approved course, does it need approval again? | Important for content control |
| GAP-13 | Is student account uniqueness based on phone, email, or both? | Phone may be more practical for Egypt |

## 4. Recommended Questions to Answer Before Real Implementation

1. Course access duration
2. Parent-student linking safety
3. Price change rule
4. Commission/revenue rule
