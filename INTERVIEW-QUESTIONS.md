# Interview Questions

## Architecture

### Why did you choose microservices?

Because the project contains distinct business capabilities that can be independently developed and scaled. The architecture also provides clear service boundaries.

### Why is service discovery needed?

Because service instances can change location or scale horizontally. Discovery removes the need for every service to hard-code the network location of every other service.

### Why use sockets?

For low-latency server-to-client updates such as real-time location and ride-state changes.

### Why use Kafka?

For asynchronous, event-driven communication where producers and consumers should be loosely coupled.

## Resilience

### What happens if a downstream service is unavailable?

The caller should use appropriate timeouts, retries where safe, circuit breaking where appropriate, and graceful error responses. Asynchronous workflows can use durable events and retries.

### How do you prevent duplicate Kafka processing?

Use idempotent consumers and an event identifier or equivalent deduplication strategy.

## Scaling

### How would you scale the Socket Service?

Run multiple instances behind a load balancer and use a shared event/backplane mechanism so events can reach clients regardless of which instance holds their connection.

### How would you scale Location Service?

Separate ingestion from querying if necessary, optimize geospatial queries, cache hot data, and partition/scale the storage layer according to traffic.

## Security

### Where should authentication happen?

Authentication/identity operations belong in the Auth Service, while downstream services should enforce authorization for protected resources.

## Future system design

Be prepared to explain how you would add:

- API Gateway
- Ride Service
- Driver Service
- Matching Service
- Pricing Service
- Payment Service
- Notification Service
- Observability
