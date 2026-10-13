# Backend status

## Scope of this report

This is the Phase 0 repository and environment survey for the Django Recruitment PTIT backend. It records only facts observed in the working directory and checks that were actually attempted.

## Repository findings

Survey date: 2026-10-13 (Asia/Ho_Chi_Minh)

- Working directory: `D:\Project\Python\Django Recruitment Backend`
- The directory contains only the four survey/design documents created during the previous pass; no source files, Django project, application packages, migrations, tests, or dependency manifests were found.
- The directory is not a Git work tree (`git status --short --branch` returned `fatal: not a git repository`).
- No Python executable, `py`, `pip`, `pip3`, Poetry, Conda, or `psql` is available through the current PowerShell `PATH`.
- `uv 0.11.18` is available, but its default cache path could not be initialized. A project-local cache was attempted, then `uv python install 3.12` failed after network connection attempts were blocked by the environment. No Python runtime was installed.
- A Python executable bundled with MySQL Workbench was found, but it is not a complete standalone Python distribution and failed to start because the standard library (`encodings`) is unavailable. It is not suitable for Django.
- No database configuration, `.env`, `.gitignore`, `manage.py`, `requirements.txt`, `pyproject.toml`, or `settings.py` exists to inspect.
- PostgreSQL service `postgresql-x64-17` is running and `localhost:5432` accepted a TCP connection. Credentials and database-level authentication were not tested because `psql` and a Python PostgreSQL client are unavailable.
- There is no existing custom user model, authentication setup, URL configuration, API implementation, or migration history to preserve.

No secrets or environment values were printed during the survey.

## Commands attempted

| Check | Result |
|---|---|
| `git status --short --branch` | Failed because this directory is not a Git repository |
| Repository file listing | Four markdown survey/design files only |
| `python --version`, `py --version`, `pip` discovery | Failed / missing |
| `uv --version` | `uv 0.11.18` is installed |
| `uv python install 3.12` | Failed: outbound download was blocked after retries |
| PostgreSQL service and port check | Service running; `localhost:5432` reachable |
| Dependency manifest and `manage.py` inspection | No matching files |

## Current implementation status

No backend functionality is implemented in this checkout. Consequently, there are no existing endpoints, database models, migrations, permissions, tests, or API compatibility guarantees to validate.

## Smallest viable implementation plan

1. Confirm the intended repository/branch and make the directory a Git work tree, or provide the existing source checkout. The supplied path is currently treated as the intended target, but it has no Git metadata.
2. Install or expose a supported Python runtime (Python 3.11 or 3.12) and create an isolated virtual environment. The current environment cannot download one through `uv`.
3. Bootstrap a Django project with Django REST Framework, PostgreSQL configuration, Simple JWT, CORS, OpenAPI documentation, and environment-based settings.
4. Implement the data model and migrations in dependency order: users and profiles, companies and taxonomy, jobs, CVs, applications, and status history.
5. Add authentication, role permissions, ownership-scoped querysets, validation, private CV handling, and the `/api/v1/` endpoints from the frontend contract.
6. Add focused API tests for authentication, ownership, public job visibility, uploads, applications, state transitions, admin access, and dashboard scope.
7. Run Django checks, migration checks, and the test suite against PostgreSQL when available; record exact results.
8. Add seed data, setup documentation, and an OpenAPI schema after the runtime and repository location are confirmed.

## Blocking items

- The source checkout is empty apart from survey documents and is not a Git work tree.
- Python/Django are unavailable. PostgreSQL is running, but database credentials and SQL-level connectivity are not yet verified.
- No existing schema or frontend implementation is available for compatibility review.

Implementation should not be claimed as runnable until a supported Python runtime is installed and the intended Git checkout is confirmed. The PostgreSQL service itself is available for the next validation step.
