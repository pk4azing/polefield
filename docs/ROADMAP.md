# Roadmap

## Phase 0 — Discovery (2 weeks)

- [ ] Stakeholder interviews: utility vs contractor vs telecom OSP
- [ ] Pole workflow selection: inspection vs survey vs joint-use
- [ ] Compliance requirements (NERC, joint-use agreements, photo retention)
- [ ] Competitive gap analysis vs Fulcrum
- [ ] SLO sign-off

**Exit:** PRD + wireframes for mobile capture + web review

## Phase 1 — Platform foundation (6 weeks)

- [ ] Django project scaffold, Docker Compose, health checks
- [ ] Multi-tenant org model + JWT auth
- [ ] Form schema engine (JSON) + admin publish
- [ ] Record CRUD API (online only first)
- [ ] PostGIS geometry on records
- [ ] S3 presigned media upload
- [ ] Web portal: project list, record table, map view

**Exit:** Create pole inspection form in admin; submit records from web

## Phase 2 — Offline mobile (8 weeks)

- [ ] React Native app shell + auth
- [ ] WatermelonDB local schema mirroring server
- [ ] Dynamic form renderer from schema JSON
- [ ] Outbox sync push/pull (see SYNC_PROTOCOL.md)
- [ ] Offline photo capture + background upload
- [ ] GPS point capture + Bluetooth GPS optional

**Exit:** Field user completes 20 pole records offline; syncs on reconnect

## Phase 3 — Pole domain templates (4 weeks)

- [ ] Seed choice lists (owners, materials, attachment types)
- [ ] Pole inspection app template
- [ ] Pole survey / MRE app template (repeatable attachments)
- [ ] Joint-use attachment app template
- [ ] CSV import for laser measurement exports
- [ ] Conflict resolution UI in web portal

**Exit:** Pilot with 1 contractor on 500-pole project

## Phase 4 — GIS & integrations (6 weeks)

- [ ] GeoJSON / CSV / KML export
- [ ] Query API (read-only SQL subset)
- [ ] Webhooks on record submit
- [ ] ArcGIS Feature Service push (bidirectional optional)
- [ ] Report PDF generation per project

**Exit:** Engineering team consumes export for make-ready

## Phase 5 — Reliability & scale (ongoing)

- [ ] Load test: 500 concurrent sync clients
- [ ] Postgres read replica for exports
- [ ] Monitoring + alerting (SLO dashboard)
- [ ] Backup restore drill
- [ ] Pen test + tenant isolation audit

**Exit:** 99.9% availability demonstrated over 30 days

## Out of scope (later)

- Native laser SDK integration
- LiDAR / photogrammetry pipeline
- In-app MRE engineering calculations
- Public form marketplace
