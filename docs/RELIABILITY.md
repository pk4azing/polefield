# Reliability

SLOs: 99.9% API availability · 99.95% sync push success · RPO ≤ 15 min · RTO ≤ 1 hr.

Mitigations: client outbox, presigned resumable media, Postgres PITR, health checks, structured logging.

Scale targets: Pilot 50k records → Year 1 2M → Year 3 20M with read replica at Year 1.
