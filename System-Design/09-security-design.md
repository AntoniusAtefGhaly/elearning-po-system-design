# Step 15 - Security Design

## Purpose

Define security guardrails for the MVP.

## Authentication

- Use secure HTTP-only cookie auth for web.
- Use HTTPS only.
- Use cookie expiration and sliding expiration.
- Protect state-changing requests from CSRF.

## Authorization

- Backend must enforce all permissions.
- Use role-based, relationship-based, and state-based authorization.
- Check enrollment before lesson, quiz, progress, and video access.
- Check parent-student link before parent progress access.
- Check teacher ownership before course/report access.
- Check center-teacher relationship before center reports.

## Password Security

- Store password hashes only.
- Never store plain passwords.
- Use ASP.NET Core Identity password hashing or equivalent.
- Add rate limiting for login attempts.

## Input and File Security

- Validate all request DTOs.
- Sanitize text displayed in UI.
- Validate uploaded teacher documents and images.
- Restrict file types and file sizes.
- Store files outside the web root or in a private provider.

## Video Security

- Do not expose permanent public video URLs.
- Use signed URLs or provider playback tokens.
- Issue playback access only after enrollment check.

## Audit Logging

Audit:

- Teacher approval/rejection
- Course approval/rejection
- Prepaid code generation/cancellation/redemption
- Manual balance adjustment/reset
- User suspension/activation

## Developer Notes

- Angular route guards are UX only, not security.
- Avoid leaking whether private resources exist.
- For sensitive resources, consider returning 404 instead of 403.
- Never log passwords, auth cookies, or full sensitive tokens.

