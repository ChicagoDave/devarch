# Architecture Decision Records

This folder contains Architecture Decision Records (ADRs) that document significant design decisions.

See the [ADR Guide](../../architecture-decision-records-guide.md) for how to write and use ADRs.

## Index

| ADR | Title | Status | Date |
|-----|-------|--------|------|
| [001](adr-001-database.md) | Use PostgreSQL for Primary Database | Accepted | 2025-01-15 |
| [007](adr-007-monetary-values.md) | Store Monetary Values as Integers | Accepted | 2025-02-01 |
| [012](adr-012-rest-api.md) | Use REST API for All Endpoints | Superseded | 2025-03-15 |

## By Category

### Data Storage
- [ADR-001](adr-001-database.md): Use PostgreSQL for Primary Database

### Data Modeling
- [ADR-007](adr-007-monetary-values.md): Store Monetary Values as Integers (Cents)

### API Design
- [ADR-012](adr-012-rest-api.md): Use REST API (Superseded by ADR-034)

---

## Adding New ADRs

1. Copy the template from the [ADR Guide](../../architecture-decision-records-guide.md#adr-template)
2. Use the next available number (currently: ADR-013)
3. Add an entry to the index table above
4. Add to the appropriate category section
