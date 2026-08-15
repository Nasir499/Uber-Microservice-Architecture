# Architecture

## Architectural style

The project follows a **microservices architecture**. Instead of putting authentication, location, reviews, and real-time communication into one application, they are separated into independently deployable services.

### Main components

1. Client
2. Authentication Service
3. Service Discovery
4. Location Service
5. Socket Service
6. Review Service
7. Event/message infrastructure where asynchronous communication is required

## Communication model

There are two useful communication categories:

### Synchronous communication

Used when the caller needs an immediate response.

Examples:

- Login/authentication request
- Fetch location information
- Submit/fetch review information

### Asynchronous communication

Used when the sender should not have to wait for downstream processing.

Kafka can be used for event-driven communication such as:

```text
Producer Service
      |
      v
Kafka Topic
      |
      v
Consumer Service
```

This reduces direct coupling between services.

## Design principle

Each service should own a clearly defined business responsibility. A service should not become a shared "utility backend" containing unrelated business logic.

## Future expansion

A production-grade ride-hailing system would typically add services such as:

- API Gateway
- Ride/Trip Service
- Driver Service
- Matching/Dispatch Service
- Pricing Service
- Payment Service
- Notification Service
- Rating/Review Service
- Observability stack

These are intentionally documented as future extensions unless they already exist in the implementation.
