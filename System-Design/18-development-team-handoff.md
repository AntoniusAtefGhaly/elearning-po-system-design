# Step 18 - Development Team Handoff

## Purpose

Give the team lead and developers a clear starting point for implementation.

## Approved Stack

```text
Frontend:
Angular + TypeScript

Backend:
ASP.NET Core .NET 10 LTS + C#

Database:
Microsoft SQL Server

ORM:
Entity Framework Core

Auth:
Secure HTTP-only cookie auth

API:
REST JSON + OpenAPI/Swagger

Deployment:
Azure Static Web Apps + Azure Container Apps + Azure SQL Database for learning/demo
```

## Architecture Style

Use:

```text
Modular Monolith with Clean Architecture boundaries
```

Backend modules:

```text
Identity
Users
Curriculum
Courses
Video
PrepaidCodes
Balance
Enrollment
Quizzes
Progress
Reports
Audit
```

## Suggested Implementation Order

1. Backend solution structure and database setup
2. Authentication and user roles
3. Curriculum and course catalog
4. Teacher course management and admin approval
5. Prepaid code and balance
6. Enrollment and access control
7. Lessons and video access placeholder
8. Quiz and progress tracking
9. Parent view
10. Reports
11. Deployment pipeline

## Non-Negotiable Rules

- Backend owns authorization.
- Student balance cannot become negative.
- Code redemption must be transactional.
- Enrollment purchase must be transactional.
- Student cannot access paid content without enrollment.
- Quiz retry is blocked in backend.
- Every balance change has a transaction record.
- Sensitive admin actions are audited.

## Team Lead Responsibilities

- Break architecture into sprint tasks.
- Define coding standards.
- Assign modules to developers.
- Review PRs for architecture violations.
- Ensure tests cover risky flows.
- Keep architecture docs updated when decisions change.

## Developer Responsibilities

- Follow module boundaries.
- Add backend authorization to every sensitive endpoint.
- Write tests for balance, enrollment, access control, and quiz attempts.
- Use migrations for database changes.
- Keep API contracts documented in Swagger/OpenAPI.

## First Sprint Recommendation

Sprint 1 should deliver:

- Backend project structure
- Angular project structure
- SQL Server connection
- EF Core migration setup
- User login/logout with cookie auth
- Basic roles
- Health check endpoint
- Swagger enabled

