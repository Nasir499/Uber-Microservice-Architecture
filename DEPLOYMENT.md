# Deployment

## Local development

A practical local setup can run the services independently.

Typical startup order:

```text
1. Infrastructure
2. Service Discovery
3. Authentication Service
4. Location Service
5. Socket Service
6. Review Service
```

The exact order depends on the current configuration.

## Production architecture

```text
                    Internet
                       |
                 Load Balancer
                       |
                  API Gateway
                       |
       +---------------+---------------+
       |               |               |
    Auth Service   Location Service  Review Service
       |               |               |
       +---------------+---------------+
                       |
                Event Infrastructure
                       |
                  Observability
```

## Production checklist

- [ ] Containerize each service
- [ ] Externalize configuration
- [ ] Add health checks
- [ ] Add centralized logging
- [ ] Add metrics
- [ ] Add distributed tracing
- [ ] Add CI/CD
- [ ] Use managed databases where appropriate
- [ ] Configure TLS
- [ ] Configure secrets management
- [ ] Configure autoscaling
- [ ] Add graceful shutdown
