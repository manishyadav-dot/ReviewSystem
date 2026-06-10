# Staging Environment

Pre-production environment for integration testing and user acceptance testing.

## Characteristics

- Production-like configuration and scaling
- Anonymized or synthetic test data only
- Full CI/CD deployment on merge to `release/*` branches
- Monitoring and alerting enabled

## Access

- Restricted to development team and designated UAT testers.
- Deployments require passing CI pipeline — no manual overrides.
