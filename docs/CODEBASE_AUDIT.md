# Codebase audit — reusable patterns

Audit of `/Users/azing/all-repos` (Sep 2026). **No pole/GIS/Fulcrum clone exists today.**

## Closest existing work

| Repo | Relevance | Reuse |
|------|-----------|-------|
| `all-repos/LFRAS_LPHONE` | Multi-tenant Django SaaS, activities, file upload, audit, RBAC | **Best backend base** — tenant model, attachments, validation lifecycle |
| `all-repos/LCRF` | Marketed offline tablet forms | **Empty placeholder** — do not assume it exists |
| `all-repos/devcentra` | JSON `form_schema` + client renderer | **Form engine pattern** for dynamic mobile forms |
| `all-repos/MiCi` | Decimal lat/lng, Nominatim, haversine, GPS EXIF screening | Geo helpers until PostGIS is wired |
| `all-repos/work-monitoring` | localStorage → SQLite sync shim | Reference only — not asset inspection |
| `all-repos/mihu`, `all-repos/azim` | Expo / React Native, camera | Mobile capture patterns |
| `all-repos/azing-django` | Monorepo Django, Docker, multi-product | Production deploy pattern |
| `all-repos/firstsource-sar-edi` | DRF + Celery + JWT + AWS EB | Enterprise API/worker pattern |
| `all-repos/noorva` | NestJS + BullMQ + Docker | Reference if splitting sync to a microservice (not recommended v1) |

## Not found (net-new for PoleField)

- PostGIS / GeoDjango in any repo
- Pole or utility asset models
- Offline sync queue (WatermelonDB, Drift, Realm)
- Fulcrum / ArcGIS / Survey123 integrations
- Implemented LCRF field client

## LFRAS gaps to fix if used as base

From `LFRAS_LPHONE/GAP_ANALYSIS_REPORT.md`:

- Tenant isolation bugs — must harden before pole data
- File validation is extension/filename only — needs content checks for production
- DRF/JWT in requirements but not fully wired — PoleField should wire API from day one

## Build vs extend decision (Phase 0)

| Option | Pros | Cons |
|--------|------|------|
| **A. Extend LFRAS_LPHONE** | Multi-tenant, audit, uploads already built | Compliance domain coupling; tenant bugs to fix |
| **B. New Django app in azing-django monorepo** | Shared infra with A-Zing products | More boilerplate |
| **C. Greenfield repo (this repo)** | Clean pole/GIS domain | Longest path to multi-tenant + audit |

**Recommendation:** Option **C** for repo boundary (this `polefield` repo), but **port patterns** from LFRAS (tenant/RBAC/attachments) and devcentra (form schema) rather than inventing them.

## Mobile choice

| Option | Evidence in repos |
|--------|-------------------|
| **Flutter** (preferred) | `MOBILE_DEV_SETUP.md`, MiCi platform target |
| **Expo / React Native** | Running code in `mihu`, `azim`; WatermelonDB fits offline sync |

Decide in Phase 0 based on team skill and offline-sync library maturity.

## Maps

- **Web/admin:** Leaflet + OSM (already used in azing-django contact page)
- **Mobile:** flutter_map or Mapbox (no Mapbox in production code yet)
