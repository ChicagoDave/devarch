# ADR-007: Store Monetary Values as Integers (Cents)

## Status

Accepted

## Date

2025-02-01

## Context

We're building a financial application that handles money. Floating-point arithmetic causes precision errors:

```javascript
0.1 + 0.2 === 0.30000000000000004  // true, but wrong
```

We need a representation that:

- Avoids floating-point errors
- Works across languages (JavaScript, Python, database)
- Is simple to understand and debug

## Decision

We will store all monetary values as integers representing cents.

| Display | Storage |
|---------|---------|
| $10.00 | 1000 |
| $0.01 | 1 |
| $123.45 | 12345 |

Display formatting happens only at the UI layer.

All APIs accept and return cents as integers.

## Consequences

### Positive

- No floating-point precision issues
- Integer arithmetic is exact
- Easy to validate (must be positive integer)
- Consistent across all languages and storage

### Negative

- Must remember to convert for display
- Off-by-100x bugs if someone forgets the format
- Need helper functions for formatting

### Neutral

- Database column type: INTEGER or BIGINT (not DECIMAL)

## Alternatives Considered

### Use Decimal/Numeric Types

- **Pros:** More intuitive, database handles precision
- **Cons:** JavaScript has no native Decimal; serialization is inconsistent across languages
- **Rejected:** Cross-language consistency is more important

### Use String Representation

- **Pros:** Exact representation, no precision loss
- **Cons:** Can't do arithmetic without parsing, validation is harder
- **Rejected:** Too cumbersome for calculations

## Implementation Notes

### Helper Functions

```typescript
// Convert cents to display string
function formatCents(cents: number): string {
  return (cents / 100).toFixed(2);
}

// Convert dollars to cents (for user input)
function toCents(dollars: number): number {
  return Math.round(dollars * 100);
}
```

### Validation

```typescript
function isValidCents(value: unknown): value is number {
  return typeof value === 'number'
    && Number.isInteger(value)
    && value >= 0;
}
```
