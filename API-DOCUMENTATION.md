# API Documentation

This repository should document the APIs that actually exist in the source repositories.

For each endpoint, use this format:

## Endpoint template

### `METHOD /path`

**Purpose:** What the endpoint does.

**Authentication:** Required / Not required.

**Request:**

```json
{
  "example": "value"
}
```

**Response:**

```json
{
  "success": true
}
```

**Possible errors:**

- `400 Bad Request`
- `401 Unauthorized`
- `403 Forbidden`
- `404 Not Found`
- `500 Internal Server Error`

## Recommended additions

Add OpenAPI/Swagger documentation to each service where appropriate. This makes the architecture easier to understand and provides a machine-readable API contract.
