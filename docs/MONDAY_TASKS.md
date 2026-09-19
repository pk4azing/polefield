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
| Priority | status (Critical / High / Medium / Low) |
| Phase | dropdown |
| Owner | people |
| Due date | date |
| GitHub | link |
| Notes | long text |

## Tasks

### Phase 0 — Discovery

1. Stakeholder interviews — utility, contractor, telecom OSP
2. Select primary workflow — inspection vs survey vs joint-use
3. Document compliance requirements (retention, audit)
4. Fulcrum gap analysis — features to match vs differentiate
5. Sign off SLOs and reliability targets
6. Write PRD and mobile/web wireframes

### Phase 1 — Platform foundation

7. Django + DRF scaffold with Docker Compose
8. Multi-tenant org model and JWT authentication
9. Form schema engine (JSON) with admin publish
10. Record CRUD API with PostGIS geometry
11. S3 presigned media upload pipeline
12. Web portal — projects, record table, map view
13. CI — lint, test, compose config validate

### Phase 2 — Offline mobile

14. React Native app shell and auth flow
15. WatermelonDB local schema
16. Dynamic form renderer from schema JSON
17. Sync push endpoint — idempotent mutations
18. Sync pull endpoint — sequence cursor + bbox
19. Offline photo capture and background upload
20. GPS capture with optional Bluetooth GPS
21. E2E offline test — 50 records, zero duplicates

### Phase 3 — Pole domain

22. Seed choice lists — owners, materials, attachments
23. Pole inspection app template
24. Pole survey / MRE template with repeatable attachments
25. Joint-use attachment app template
26. Laser measurement CSV import
27. Conflict resolution UI in web portal
28. Pilot — 500 poles with one contractor

### Phase 4 — GIS & integrations

29. GeoJSON / CSV / KML export
30. Query API — read-only SQL subset
31. Webhooks on record submit
32. ArcGIS Feature Service integration
33. PDF report generation per project

### Phase 5 — Reliability & scale

34. Load test — 500 concurrent sync clients
35. Postgres read replica for exports
36. Monitoring and SLO dashboard
37. Backup and restore drill
38. Tenant isolation security audit

## Links

- GitHub repo: `https://github.com/pk4azing/polefield`
- Architecture: `docs/ARCHITECTURE.md`
- Sync protocol: `docs/SYNC_PROTOCOL.md`
