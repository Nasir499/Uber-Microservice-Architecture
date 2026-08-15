# Services

## 1. Authentication Service

Repository: `UberProject-AuthService`

### Responsibility

The authentication service is responsible for identity-related operations.

Typical responsibilities include:

- User registration
- Login
- Credential verification
- Token generation
- Authentication-related validation

### Why separate it?

Authentication is a cross-cutting concern. Isolating it allows other services to focus on their own business domains instead of implementing authentication independently.

---

## 2. Service Discovery

Repository: `UberProject-ServiceDiscovery`

### Responsibility

The discovery service maintains information about available service instances.

Instead of hard-coding:

```text
http://localhost:8081
http://localhost:8082
http://localhost:8083
```

services can discover one another through a registry.

### Benefits

- Dynamic service locations
- Easier scaling
- Reduced configuration coupling
- Better support for multiple service instances

---

## 3. Location Service

Repository: `UberProject-LocationService`

### Responsibility

The location service handles location-related functionality.

A ride-hailing platform needs location information for:

- Driver position
- Rider position
- Location lookup
- Distance-related operations
- Future driver matching

The exact responsibilities should remain aligned with the implemented endpoints rather than assuming functionality that is not present in the code.

---

## 4. Socket Service

Repository: `UberSocketService`

### Responsibility

The socket service provides a real-time communication layer.

This is useful for:

- Live location updates
- Driver/rider status updates
- Ride state changes
- Real-time notifications

A persistent socket connection avoids repeatedly polling the server for every small state change.

---

## 5. Review Service

Repository: `UberProject-reviewService`

### Responsibility

The review service handles review/rating-related operations.

Typical domain operations:

```text
Create Review
      |
      v
Validate Request
      |
      v
Persist Review
      |
      v
Return Result
```

Keeping reviews separate means review-related schema and business rules do not have to be embedded into authentication or location services.
