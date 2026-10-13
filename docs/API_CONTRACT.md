# API contract (draft)

This is a planning draft created during the initial repository survey. It is based on the supplied project brief and is not backed by an implementation yet.

## Base URL and conventions

- Base path: `/api/v1/`
- JSON fields use `snake_case`.
- List responses use `{ "count": 0, "next": null, "previous": null, "results": [] }`.
- Errors use `{ "error": { "code": "...", "message": "...", "details": {} } }`.

## Required endpoint groups

Authentication: `/auth/register/`, `/auth/login/`, `/auth/refresh/`, `/auth/logout/`, `/auth/me/`.

Candidate: `/candidate/profile/`, `/candidate/skills/`, `/candidate/experiences/`, `/candidate/cvs/`, `/candidate/applications/`.

Employer and company: `/employer/company/`, `/companies/{id}/`, `/employer/jobs/`, `/employer/applications/`, `/employer/dashboard/`.

Public jobs: `/jobs/`, `/jobs/{id}/`, `/jobs/{id}/apply/`.

Administration: `/admin/users/`, `/admin/categories/`, `/admin/jobs/pending/`, `/admin/jobs/{id}/approve/`, `/admin/jobs/{id}/reject/`, `/admin/dashboard/`.

## Decisions still requiring confirmation

- Whether the frontend already depends on response field names beyond those in the brief.
- JWT storage and logout/revocation policy (cookie versus JSON refresh token).
- Exact job employment-type enum and allowed application status transitions.
- Private storage provider and malware/antivirus scanning policy for CV files.

The full method, request, response, permission, error, and example matrix will be completed after the source checkout and frontend contract are available.
