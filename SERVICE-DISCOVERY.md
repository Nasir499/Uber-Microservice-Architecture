# Service Discovery

## Problem

In a distributed system, service instances may change address or number.

Hard-coding addresses creates operational problems.

## Discovery model

```text
Service A ----register----> Discovery Server
Service B ----register----> Discovery Server

Service A ----lookup------> Discovery Server
Discovery Server ----------> Service B instance
```

## Benefits

- Dynamic registration
- Dynamic lookup
- Easier horizontal scaling
- Reduced hard-coded network configuration

## Failure considerations

A production system should consider:

- Discovery server availability
- Health checks
- Stale registrations
- Timeouts
- Retries
- Circuit breakers
- Load balancing

Service discovery solves **where** a service is. It does not by itself solve retries, resilience, authentication, or business-level failure handling.
