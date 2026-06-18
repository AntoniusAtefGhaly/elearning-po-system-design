# Step 11 - Technology Stack Decisions

## Final Stack

| Area | Choice |
| --- | --- |
| Architecture | Modular Monolith with Clean Architecture boundaries |
| Frontend | Angular + TypeScript |
| Backend | ASP.NET Core on .NET 10 LTS + C# |
| Database | Microsoft SQL Server |
| ORM | Entity Framework Core |
| API | REST JSON + OpenAPI/Swagger |
| Authentication | Secure HTTP-only cookie auth |
| Cache | Redis later, not day one |
| Background Jobs | Hangfire later, not day one |
| Video | Cloudflare Stream or Vimeo later |
| Free Deployment | Azure Static Web Apps + Azure Container Apps + Azure SQL Database |for learning

## Why Angular

Choose Angular because the team is already strong in Angular.

This matters more than popularity. Angular also fits this product because the system has many structured screens:

- Student dashboard
- Parent progress view
- Teacher course management
- Education center portal
- Admin dashboard
- Reports
- Quizzes
- Video lesson pages

Angular gives built-in routing, forms, HTTP client, guards, interceptors, dependency injection, and strong TypeScript structure.

## Why ASP.NET Core

Choose ASP.NET Core because it fits:

- Modular monolith backend
- Clean Architecture
- REST APIs
- Role and permission checks
- High-performance web APIs
- Entity Framework Core
- SQL Server
- Microsoft/Azure deployment path

Use .NET 10 LTS for long-term support.

## Why SQL Server

Choose Microsoft SQL Server because the system needs strong relational and transactional behavior.

Important flows need transactions:

- Prepaid code redemption
- Student balance updates
- Course enrollment
- Quiz attempts
- Admin balance adjustments

SQL Server also fits well with ASP.NET Core, Entity Framework Core, and Azure.

## Why Not NoSQL as Primary DB

Do not use MongoDB or another NoSQL database as the primary database for this MVP.

The system is relationship-heavy:

- Parent to student
- Teacher to course
- Center to teacher
- Student to enrollment
- Course to lesson
- Prepaid code to redemption
- Student to balance transactions

A relational database is the better first choice.

## Free Deployment Choice

For learning and demo:

```text
Angular frontend:
Azure Static Web Apps

ASP.NET Core backend:
Azure Container Apps

SQL Server database:
Azure SQL Database
```

This is the most coherent free path because the stack is Microsoft-friendly.

## Deployment Shape

```text
User Browser
  -> Azure Static Web Apps
     Angular frontend

Angular Frontend
  -> Azure Container Apps
     ASP.NET Core API

ASP.NET Core API
  -> Azure SQL Database
     Main application data
```

## Defer Until Needed

Do not add these at the start:

- Redis
- Hangfire
- Paid video streaming
- Kubernetes
- Microservices
- Complex monitoring stack
- Multiple deployment environments

Add them when a real requirement appears.

## Architecture Decision Record

### Decision

Use Angular, ASP.NET Core, SQL Server, and Azure free-tier deployment for the MVP learning version.

### Reason

This stack fits the team, the business requirements, and the architecture:

- Angular matches team strength.
- ASP.NET Core fits the backend architecture.
- SQL Server protects transactional flows.
- Azure gives a natural free deployment path.

### Consequences

Positive:

- Lower delivery risk.
- Strong team fit.
- Good transaction support.
- Clear Microsoft ecosystem.
- Easy path from learning deployment to production deployment.

Tradeoffs:

- SQL Server/Azure may cost money later in production.
- Angular is heavier than simpler frontend libraries.
- Free tiers are for learning and demos, not serious production.

