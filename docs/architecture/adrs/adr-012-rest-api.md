# ADR-012: Use REST API for All Endpoints

## Status

Superseded by ADR-034

## Date

2025-03-15

## Context

We needed to choose an API style for our backend. At the time:

- Team had REST experience
- Simple CRUD operations were the primary use case
- No real-time requirements identified yet
- Mobile app was not yet planned

## Decision

We will use REST for all API endpoints.

Standard conventions:
- `GET /resources` — List
- `GET /resources/:id` — Read
- `POST /resources` — Create
- `PUT /resources/:id` — Update
- `DELETE /resources/:id` — Delete

## Consequences

### Positive

- Team familiarity with REST patterns
- Excellent tooling (Postman, curl, OpenAPI)
- Cacheable responses with standard HTTP headers
- Clear resource-based mental model

### Negative

- Over-fetching: clients get all fields even when they need few
- Under-fetching: complex views require multiple requests
- No built-in real-time support

### Neutral

- Need to version API (we chose URL versioning: `/v1/resources`)

## Alternatives Considered

### GraphQL

- **Pros:** Flexible queries, single endpoint, built-in schema
- **Cons:** Learning curve, caching complexity
- **Rejected at the time:** Team unfamiliar, seemed like overkill for CRUD

### gRPC

- **Pros:** High performance, strong typing, streaming
- **Cons:** Browser support limited, debugging harder
- **Rejected:** Web client is primary consumer

---

## Superseded

**Date:** 2025-08-01

**Superseded by:** ADR-034 (GraphQL Migration)

### Why This Decision Changed

After 5 months in production, we discovered:

1. **Real-time features became essential** — Activity feeds, notifications, and live updates required WebSocket connections alongside REST
2. **Mobile app launched** — Mobile clients needed to minimize requests; REST was too chatty over cellular
3. **N+1 query problem** — List views required multiple round-trips (list orders → get customer for each → get items for each)
4. **Team learned GraphQL** — Initial unfamiliarity is no longer a blocker

### Migration Path

See ADR-034 for:
- Gradual migration strategy (REST and GraphQL running in parallel)
- Which endpoints to migrate first
- Timeline and rollback plan

### Lessons Learned

- "Simple CRUD" rarely stays simple
- Real-time requirements often emerge after launch
- Initial team familiarity is a valid factor, but shouldn't be the only one
