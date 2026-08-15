# Request Flows

## Authentication flow

```mermaid
sequenceDiagram
    participant C as Client
    participant A as Auth Service
    participant D as Service Discovery

    C->>A: Login / Register
    A->>D: Resolve required service information
    D-->>A: Service information
    A-->>C: Authentication result / token
```

## Real-time communication flow

```mermaid
sequenceDiagram
    participant C as Client
    participant S as Socket Service
    participant L as Location Service

    C->>S: Establish socket connection
    C->>S: Send real-time update
    S->>L: Forward/process location-related data
    L-->>S: Updated state
    S-->>C: Push real-time update
```

## Review flow

```mermaid
sequenceDiagram
    participant C as Client
    participant R as Review Service

    C->>R: Submit review
    R->>R: Validate request
    R->>R: Persist review
    R-->>C: Review response
```

## Important interview point

The exact request flow should always be derived from the current implementation. Documentation should not claim that a service performs matching, payment, trip management, or notification delivery unless those components actually exist.
