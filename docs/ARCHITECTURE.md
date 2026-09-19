# Architecture

See [README.md](../README.md). Full architecture doc — multi-tenant Django API, PostGIS, React Native offline sync, S3 media, Celery workers.

Key components: Tenant & identity · Form builder · Record store · Sync service · GIS export · Pole domain templates.

Reliability targets: 99.9% API, zero data loss via client outbox, org-scoped RLS.

Deployment: Docker Compose on VPS (phase 1) → horizontal scale + read replica (phase 2).
