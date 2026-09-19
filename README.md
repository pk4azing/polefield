# PoleField

Fulcrum-class field data platform for **utility pole management, measurement, and inspection** — planned for reliability, offline-first capture, and multi-tenant SaaS scale.

**Status:** Planning only. No application code yet.

## Documents

| Doc | Purpose |
|-----|---------|
| [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md) | System design, components, stack |
| [docs/DATA_MODEL.md](docs/DATA_MODEL.md) | Core entities (orgs, forms, records, poles, attachments) |
| [docs/SYNC_PROTOCOL.md](docs/SYNC_PROTOCOL.md) | Offline-first sync, idempotency, conflicts |
| [docs/RELIABILITY.md](docs/RELIABILITY.md) | SLOs, failure modes, ops |
| [docs/ROADMAP.md](docs/ROADMAP.md) | Phased delivery plan |
| [docs/MONDAY_TASKS.md](docs/MONDAY_TASKS.md) | Task board spec (Monday.com + GitHub Issues) |

## Product goal

Build a platform comparable to [Fulcrum](https://www.fulcrumapp.com/) for pole workflows:

- Mobile field capture (offline, photos, GPS, structured forms)
- Pole survey / inspection / joint-use attachment inventory
- GIS-native storage (PostGIS) and export (GeoJSON, ArcGIS)
- Multi-tenant SaaS with org-scoped data isolation
- API + webhooks for engineering / MRE downstream systems

## Recommended stack (aligned with existing A-Zing repos)

| Layer | Choice | Rationale |
|-------|--------|-----------|
| API | Django 5 + DRF | Matches `azing-django` patterns; fast admin, auth, multi-tenant |
| Database | PostgreSQL 16 + PostGIS | Spatial queries, industry standard for GIS |
| Mobile | React Native + WatermelonDB | Proven offline-first pattern; single codebase iOS/Android |
| Object storage | S3-compatible (MinIO dev) | Photos, video, signatures |
| Queue | Celery + Redis | Media processing, exports, webhooks |
| Web portal | Django templates or Next.js | Admin + project dashboards |
| Deploy | Docker Compose → VPS/K8s | Matches FinScore / azing-django ops |

## Tracking

- **Monday.com board:** https://a-zing-force.monday.com/boards/5031424397 (38 tasks, 6 phases)
- **GitHub:** https://github.com/pk4azing/polefield

## License

Private — pk4azing
