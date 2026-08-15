# Architecture Diagram

The following Mermaid diagram can be rendered directly by GitHub Markdown:

```mermaid
flowchart TB
    C[Client]

    C --> A[Auth Service]
    C --> S[Socket Service]
    C --> L[Location Service]
    C --> R[Review Service]

    D[Service Discovery]

    A --> D
    S --> D
    L --> D
    R --> D

    K[(Kafka / Event Bus)]

    A <--> K
    S <--> K
    L <--> K
    R <--> K
```

## Reading the diagram

- The client interacts with the services required for its operation.
- Service Discovery allows services to locate registered instances.
- Kafka can carry asynchronous domain events.
- Each service maintains a focused responsibility.
