# Database Design

This document describes how to reason about database ownership in the project.

## Database-per-service principle

Each microservice should ideally own its persistence model.

```text
Auth Service       -> Auth/User data
Location Service   -> Location data
Review Service     -> Review data
```

A service should access another service's business data through an API/event rather than directly querying another service's database.

## Why?

This preserves service autonomy and prevents tight coupling between schemas.

### Bad pattern

```text
Review Service
      |
      +----> Auth Database
```

### Better pattern

```text
Review Service ---> Auth Service ---> Auth Database
```

or, for asynchronous use cases:

```text
Auth Service ---> Kafka ---> Review Service
```

## Recommended production improvements

- Index frequently queried fields
- Add created/updated timestamps
- Use database migrations
- Add unique constraints where required
- Add foreign identifiers without creating cross-service database dependencies
- Back up production databases
- Monitor query latency
