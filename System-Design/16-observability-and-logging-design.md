# Step 17 - Observability and Logging Design

## Purpose

Define what the team should log, monitor, and trace to support debugging and operations.

## Logging

Log important business events:

- Login success/failure without passwords
- Prepaid code redemption
- Course enrollment
- Balance adjustment
- Course approval/rejection
- Video playback access denied
- Quiz submission

Log technical errors:

- Unhandled exceptions
- Database failures
- Video provider failures
- Failed background jobs

## Metrics

Track:

```text
API response time
API error rate
Login failures
Code redemption failures
Enrollment failures
Video playback access failures
Database query performance
```

## Tracing

Use correlation IDs across requests.

Important flows to trace:

- Login
- Code redemption
- Course enrollment
- Video playback access
- Quiz submission

## Audit vs Logs

Audit logs are business records and should be stored in the database.

Application logs are operational records and can go to console/cloud logging.

## Recommended Tools

For .NET/Azure:

```text
Serilog or built-in .NET logging
OpenTelemetry
Azure Application Insights later
```

## Developer Notes

- Never log passwords.
- Never log full auth cookies.
- Include UserId when safe.
- Include request correlation ID.
- Use structured logs, not only plain strings.

