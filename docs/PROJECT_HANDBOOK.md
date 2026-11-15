# EmailBot / IntelliMailPilot — Project Handbook

> **Repository:** [vaishnavsawant1994-stack/EmailBot](https://github.com/vaishnavsawant1994-stack/EmailBot)  
> **Documentation review:** 15 November 2026 · **Scope:** checked-in source and existing documentation, not a fresh end-to-end certification.

## 1. Purpose and intended audience

**Goal:** Email operations product for contacts, sender identities, campaign sequences, scheduling, replies and reporting.

**Who this serves:** Outbound sales, research and campaign operations teams.

## 2. Product features and expected journeys

1. Manage leads and mail identities.
2. Compose and schedule multistep campaigns.
3. Process campaign worker jobs and inbound replies.
4. Provide reporting, warm-up and operational dashboards.

These are described product areas or repository-supported development paths. See the status and limitations below before claiming live feature completeness.

## 3. Technical architecture and project structure

Maintained Next.js application under `dashboard-next/`; MongoDB/Mongoose, SMTP and Microsoft Graph adapters, worker scripts and standalone packaging. `campaign_engine/` and `legacy/` contain older implementations. Planning files under `project-management/`.

## 4. Implementation maturity and evidence

Significant UI/API/worker assets exist. Real email delivery, safe throttling, compliance and production operations require live provider and exact-head checks.

**Evidence level:** Repository source, current README and available manifest/structure were inspected. No new unit-test run, database migration, browser acceptance, security penetration test, CI re-run or live deployment is implied by this document. Treat older gate reports as date- and commit-specific records.

## 5. Installation, development and validation

Work inside `dashboard-next/`; `npm install`, inspect `npm run check:env` / `npm run check:mail`, then `npm run dev`. Do not run campaign workers or `deploy:ecs` against real accounts before authorization.

Recheck exact commands, package versions and environment variables against the current source. Use disposable credentials and isolated local/test data; never run destructive migrations or seed scripts against an unknown database.

## 6. Security, data and operational boundaries

- Unsolicited messaging and sender reputation laws require explicit controls.
- Do not expose tokens, contact lists or mailbox data.
- Reconcile retries, unsubscribes, bounces and idempotent delivery.

For production use additionally verify access control, errors, secrets, backup/recovery, monitoring and relevant legal/privacy responsibilities.

## 7. Recommended next milestones

1. Inventory active vs legacy workflows.
2. Test suppression, consent and bounce/unsubscribe behavior.
3. Qualify worker concurrency and delivery receipts.
4. Document deploy, backups and observability.

## 8. Source documents and change policy

- [`README.md`](../README.md)
- [`dashboard-next/package.json`](../dashboard-next/package.json)
- [`PROJECT_AUDIT.md`](../PROJECT_AUDIT.md)
- [`SYSTEM_ARCHITECTURE.md`](../SYSTEM_ARCHITECTURE.md)
- [`project-management/`](../project-management/)

This handbook supplements rather than replaces authoritative specs, security rules and exact-SHA qualification. Update it whenever the application architecture, deployment status, feature contract or project ownership changes.
