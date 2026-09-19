# Monday.com board spec — PoleField

Create a **public board** named **PoleField** in your default workspace.

## Groups (phases)

| Group | Color |
|-------|-------|
| Phase 0 — Discovery | `#579BFC` |
| Phase 1 — Platform | `#00CA72` |
| Phase 2 — Mobile offline | `#FDAB3D` |
| Phase 3 — Pole domain | `#A25DDC` |
| Phase 4 — GIS & integrations | `#E2445C` |
| Phase 5 — Reliability | `#FF642E` |

## Columns

| Column | Type |
|--------|------|
| Status | status (Not started / Working on it / Done / Blocked) |
| Priority | status (Critical / High / Medium) |
| Phase | dropdown |
| Owner | people |
| Due date | date |
| GitHub | link |
| Notes | long text |

## Tasks

### Phase 0 — Discovery

1. Codebase audit sign-off — reuse LFRAS, devcentra, MiCi patterns
2. Decide build path — greenfield polefield vs extend LFRAS_LPHONE
3. Decide mobile stack — Flutter vs Expo/React Native
4. Decide maps stack — Leaflet/OSM web; flutter_map vs Mapbox mobile
5. Review LFRAS GAP_ANALYSIS_REPORT — tenant isolation + file validation
6. Stakeholder interviews — utility, contractor, telecom OSP
7. Select primary workflow — inspection vs survey vs joint-use
8. Document compliance requirements (retention, audit)
9. Fulcrum gap analysis — features to match vs differentiate
10. Sign off SLOs and reliability targets
11. Write PRD and mobile/web wireframes

### Phase 1 — Platform foundation

12. Port LFRAS multi-tenant + RBAC pattern into polefield
13. Port devcentra form_schema design to backend API
14. PostGIS enablement spike — geometry fields + GIST indexes
15. Wire DRF + SimpleJWT from day one (not deferred)
16. Evaluate MiCi geo helpers for geocoding pre-PostGIS
17. Django + DRF scaffold with Docker Compose
18. Multi-tenant org model and JWT authentication
19. Form schema engine (JSON) with admin publish
20. Record CRUD API with PostGIS geometry
21. S3 presigned media upload pipeline
22. Web portal — projects, record table, map view
23. CI — lint, test, compose config validate

### Phase 2 — Offline mobile

24. Spike offline DB — Drift (Flutter) vs WatermelonDB (RN)
25. Port devcentra SchemaForm pattern to mobile renderer
26. MiCi GPS EXIF screening on field photos
27. Mobile app shell and auth flow (Flutter or Expo)
28. Local DB schema mirroring server
29. Dynamic form renderer from schema JSON
30. Sync push endpoint — idempotent mutations
31. Sync pull endpoint — sequence cursor + bbox
32. Offline photo capture and background upload
33. GPS capture with optional Bluetooth GPS
34. E2E offline test — 50 records, zero duplicates

### Phase 3 — Pole domain

35. Document LCRF scope — offline tablet forms are not built yet
36. Seed choice lists — owners, materials, attachments
37. Pole inspection app template
38. Pole survey / MRE template with repeatable attachments
39. Joint-use attachment app template
40. Laser measurement CSV import
41. Conflict resolution UI in web portal
42. Pilot — 500 poles with one contractor

### Phase 4 — GIS & integrations

43. GeoJSON / CSV / KML export
44. Query API — read-only SQL subset
45. Webhooks on record submit
46. ArcGIS Feature Service integration
47. PDF report generation per project

### Phase 5 — Reliability & scale

48. Load test — 500 concurrent sync clients
49. Postgres read replica for exports
50. Monitoring and SLO dashboard
51. Backup and restore drill
52. Tenant isolation security audit

## Board (live)

- **Monday board:** https://a-zing-force.monday.com/boards/5031424397
- **Workspace:** Project Management (A-Zing)

## Links

- GitHub repo: https://github.com/pk4azing/polefield
- Architecture: `docs/ARCHITECTURE.md`
- Codebase audit: `docs/CODEBASE_AUDIT.md`
- Sync protocol: `docs/SYNC_PROTOCOL.md`

**Total tasks on board:** 52 (+ 1 overview item)

## Due dates (set on board)

Tasks are due within each phase window from project start (2026-09-19):

| Phase | Window |
|-------|--------|
| Phase 0 | Sep 19 – Oct 3, 2026 |
| Phase 1 | Oct 3 – Nov 16, 2026 |
| Phase 2 | Nov 16, 2026 – Jan 11, 2027 |
| Phase 3 | Jan 11 – Feb 8, 2027 |
| Phase 4 | Feb 8 – Mar 22, 2027 |
| Phase 5 | Mar 22 – May 3, 2027 |

Priority: Phase 0 + critical-path items → **High**; tenant isolation / E2E sync → **Critical**; default → **Medium**.
