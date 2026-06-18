# Step 16 - Deployment and Environment Design

## Purpose

Define how the MVP can be deployed for learning/demo and how it can grow later.

## Free Learning Deployment

```text
Angular frontend:
Azure Static Web Apps

ASP.NET Core backend:
Azure Container Apps

Database:
Azure SQL Database free monthly allowance
```

## Environments

Start with:

```text
Development
Demo
```

Add later:

```text
Staging
Production
```

## Configuration

Use environment variables or managed secrets for:

```text
Database connection string
Cookie settings
Video provider keys
Email/SMS provider keys
Allowed frontend origins
Logging level
```

## Deployment Flow

```text
1. Build Angular frontend.
2. Deploy static files to Azure Static Web Apps.
3. Build ASP.NET Core API Docker image.
4. Deploy API container to Azure Container Apps.
5. Run EF Core migrations against Azure SQL Database.
6. Smoke test login, catalog, enrollment, and progress.
```

## Production Later

Add:

- Paid Azure SQL tier
- Automated backups
- Application monitoring
- Separate staging environment
- Redis if needed
- Background workers if needed
- Paid/private video provider

## Developer Notes

- Do not hardcode secrets.
- Keep connection strings out of source control.
- Database migrations should be reviewed before applying to shared environments.

