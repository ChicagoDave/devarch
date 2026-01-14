# ADR-001: Use PostgreSQL for Primary Database

## Status

Accepted

## Date

2025-01-15

## Context

We need a database for our new application. Requirements:

- Strong consistency for financial transactions
- Complex queries with joins
- ACID compliance
- Team familiarity

We're a small team (3 developers) with PostgreSQL experience.
Expected data volume: ~10GB in year 1, ~100GB by year 3.

## Decision

We will use PostgreSQL as our primary database.

We will use Prisma as our ORM for type-safe database access.

## Consequences

### Positive

- Team already knows PostgreSQL; no learning curve
- Excellent tooling (pgAdmin, psql, etc.)
- Strong ecosystem for backups, replication
- Prisma provides type safety and migrations

### Negative

- Vertical scaling limits (acceptable for our scale)
- Self-managed or managed service cost
- Schema migrations require careful planning

### Neutral

- Need to set up connection pooling for serverless

## Alternatives Considered

### MongoDB

- **Pros:** Flexible schema, easy horizontal scaling
- **Cons:** Eventual consistency issues for financial data, team unfamiliar
- **Rejected:** Consistency requirements outweigh flexibility benefits

### DynamoDB

- **Pros:** Serverless, auto-scaling, AWS-native
- **Cons:** Complex query patterns, learning curve for single-table design
- **Rejected:** Our query patterns are relational; DynamoDB would require extensive denormalization
