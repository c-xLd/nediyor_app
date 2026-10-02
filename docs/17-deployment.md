# Deployment

Environments: local, preview, production.

Flow:
branch → PR → checks → preview → QA → production.

Required: typecheck, lint, tests, E2E critical flow, build, secret scan.

Schema changes use migrations.

Every production deployment has rollback/mitigation path.

Monitor uptime, API errors, latency, AI failures, ingestion failures, price freshness and client crashes.