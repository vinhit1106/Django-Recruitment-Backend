# Architecture decisions (draft)

## ADR-001: API base path

Use `/api/v1/` as the versioned API base path, matching the supplied frontend contract.

## ADR-002: Authentication

Use Django's custom email-based user model and JWT authentication if no existing authentication implementation is present. The exact refresh-token transport and revocation mechanism remain to be confirmed before implementation.

## ADR-003: Database

Use PostgreSQL for the application database. SQLite may be used only for local bootstrapping where PostgreSQL is unavailable, and any constraint or transaction differences must be reported.

## ADR-004: CV files

Treat CVs as private PDF uploads with a 5 MB limit, generated storage names, permission-checked downloads, and no public filesystem exposure. Antivirus scanning is a deployment decision that must be recorded when selected.

## ADR-005: Delivery scope

Implement the smallest monolithic Django/DRF backend that satisfies the supplied endpoint contract. Do not introduce microservices or unrelated dependency upgrades.

All decisions above are provisional because no source checkout, runtime, or existing team decisions were present in the survey directory.
