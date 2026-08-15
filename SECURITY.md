# Security

## Authentication

Authentication should be centralized in the Auth Service.

Other services should validate the authentication context before processing protected operations.

## Important security practices

- Hash passwords using a strong password hashing algorithm
- Never store plaintext passwords
- Keep JWT secrets/keys outside source control
- Validate request payloads
- Apply authorization, not only authentication
- Use HTTPS in production
- Protect internal service endpoints
- Configure CORS deliberately
- Add rate limiting to sensitive public endpoints
- Never commit `.env` files or credentials

## Secrets

Do not commit:

```text
JWT_SECRET=...
DATABASE_PASSWORD=...
KAFKA_PASSWORD=...
API_KEY=...
```

Use environment variables or a secret manager.

## Principle of least privilege

A service should have only the permissions it needs.
