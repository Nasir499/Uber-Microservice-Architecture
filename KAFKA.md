# Kafka / Event Communication

Kafka is useful when services need to communicate through events without being directly coupled.

## Basic model

```text
Producer
   |
   v
Kafka Topic
   |
   +----> Consumer A
   |
   +----> Consumer B
```

## Example ride-domain events

Possible future events include:

```text
USER_REGISTERED
DRIVER_LOCATION_UPDATED
RIDE_REQUESTED
DRIVER_ASSIGNED
RIDE_STARTED
RIDE_COMPLETED
REVIEW_CREATED
```

These names are architectural examples; only events actually implemented in the codebase should be documented as currently active.

## Why Kafka?

- Asynchronous processing
- Loose coupling
- Durable event streams
- Multiple consumers
- Better scalability for event-driven workloads

## Important concepts for interviews

Know:

- Topic
- Partition
- Offset
- Producer
- Consumer
- Consumer group
- Ordering
- Delivery semantics
- Retry
- Dead-letter topic
- Idempotency

## Idempotency

If an event can be delivered more than once, the consumer should be designed so that processing the same event twice does not corrupt state.

For example:

```text
eventId = 12345

if eventId already processed:
    ignore
else:
    process event
    record eventId
```
