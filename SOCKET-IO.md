# Socket / Real-Time Communication

The Socket Service exists to handle communication where clients need updates without repeatedly polling an HTTP endpoint.

## HTTP polling

```text
Client -> Server: Any update?
Server -> Client: No
Client -> Server: Any update?
Server -> Client: No
...
```

This creates unnecessary requests.

## Persistent connection

```text
Client <================> Socket Service
          persistent
          connection
```

The server can push an update when something changes.

## Ride-hailing use cases

Real-time communication is particularly useful for:

- Driver location
- Driver availability
- Ride status
- Driver acceptance
- Rider notifications

## Scaling considerations

When multiple Socket Service instances are deployed, a shared event/backplane mechanism may be needed so that an event received by one instance can reach clients connected to another instance.

Possible production architecture:

```text
                Load Balancer
                     |
          +----------+----------+
          |                     |
     Socket #1              Socket #2
          |                     |
          +----------+----------+
                     |
              Event Broker
```
