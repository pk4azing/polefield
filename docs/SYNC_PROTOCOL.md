# Sync protocol

Offline-first outbox/inbox model:

- `POST /api/v1/sync/push` — batch idempotent mutations
- `GET /api/v1/sync/pull` — incremental by `since_sequence` + optional bbox
- Client-generated record UUIDs; server monotonic sequence per org
- Conflict policy: last-write-wins with manager review flag

Testing: airplane mode E2E, duplicate push dedup, concurrent edit conflicts.
