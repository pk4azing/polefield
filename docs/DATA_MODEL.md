# Data model

Core entities: Organization → Projects → Forms (versioned schema) → Records (jsonb + PostGIS geom) → RecordMedia.

Records use client-supplied UUIDs for idempotent sync. Child records model attachment inventories under parent poles.

See planning session for full table definitions and pole-specific choice list catalogs.
