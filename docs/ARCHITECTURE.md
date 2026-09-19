# Architecture

Fulcrum-class field data platform for pole management — multi-tenant, offline-first, GIS-native.

See also: [CODEBASE_AUDIT.md](CODEBASE_AUDIT.md) for what exists in `all-repos` today.

## System diagram

```
Mobile (Flutter or RN + local DB)     Web portal (Django / Next.js)
         │                                      │
         └──────────────┬───────────────────────┘
                        ▼
              Django 5 + DRF  (/v1/)
         JWT · tenant middleware · idempotent sync
                        │
      ┌─────────────────┼─────────────────┐
      ▼                 ▼                 ▼
 PostgreSQL+PostGIS   Redis+Celery      S3/MinIO
```

## Components

1. **Tenant & identity** — orgs, users, roles, device registration (pattern: LFRAS `Evaluator` / membership)
2. **Form builder** — versioned JSON schema, conditional logic (pattern: devcentra `form_schema`)
3. **Record store** — jsonb + PostGIS geom, child records for attachments
4. **Sync service** — outbox/inbox, client UUIDs, server sequence ([SYNC_PROTOCOL.md](SYNC_PROTOCOL.md))
5. **GIS export** — GeoJSON, Query API, ArcGIS push (phase 4)
6. **Pole templates** — inspection, survey/MRE, joint-use

## Reuse from existing repos

| Need | Source |
|------|--------|
| Multi-tenant + RBAC + audit | LFRAS_LPHONE |
| Dynamic forms | devcentra SchemaForm / form_schema |
| Geocoding / distance (pre-PostGIS) | MiCi `core/geo.py` |
| Docker + healthchecks | azing-django, FinScore |
| Celery workers | firstsource-sar-edi |
| Photo + GPS EXIF checks | MiCi local_jobs image metadata |

## Stack (confirmed against codebase audit)

| Layer | Choice |
|-------|--------|
| API | Django 5 + DRF + SimpleJWT |
| DB | PostgreSQL 16 + PostGIS |
| Mobile | Flutter (preferred) or Expo + WatermelonDB |
| Queue | Celery + Redis |
| Storage | S3-compatible |
| Deploy | Docker Compose → VPS (azing-django pattern) |

## Reliability

99.9% API · zero data loss via client outbox · org-scoped RLS · see [RELIABILITY.md](RELIABILITY.md).

## Deployment phases

1. Single VPS — web, worker, db, redis, minio
2. Scale — read replica, horizontal web/workers, CDN for media
