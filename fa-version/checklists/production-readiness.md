# Production Readiness Checklist

Use this before deploying ANY .NET API to production.

## Security
- [ ] No secrets in source code or config files
- [ ] HTTPS is enforced
- [ ] CORS is configured (not `AllowAll` in production)
- [ ] JWT tokens have reasonable expiration
- [ ] Input validation on all endpoints
- [ ] SQL injection prevention (parameterized queries / EF Core)
- [ ] Rate limiting is configured
- [ ] No sensitive data in logs
- [ ] Authentication and authorization are working
- [ ] API keys / secrets rotated from development values

## Reliability
- [ ] Health check endpoint exists and works (`/health`)
- [ ] Health checks verify all critical dependencies
- [ ] Global exception handler catches unhandled errors
- [ ] ProblemDetails format for all error responses
- [ ] No exception details leaked in production responses
- [ ] Retry policies on external calls (Polly)
- [ ] Circuit breaker on flaky dependencies

## Observability
- [ ] Structured logging is configured (Serilog)
- [ ] Request logging middleware is active
- [ ] Correlation IDs on requests (for tracing)
- [ ] Log levels are appropriate (not everything as Information)
- [ ] Logs are shipped to a central location
- [ ] Basic metrics are available (request count, latency)

## Performance
- [ ] Database indexes on frequently queried columns
- [ ] AsNoTracking() on read-only queries
- [ ] Pagination on list endpoints
- [ ] Caching strategy for read-heavy data
- [ ] No N+1 query problems
- [ ] Connection pooling configured

## Deployment
- [ ] Multi-stage Dockerfile (small final image)
- [ ] App runs as non-root user in container
- [ ] Environment-specific configuration works
- [ ] Database migrations run safely
- [ ] CI/CD pipeline builds, tests, and deploys
- [ ] Rollback plan exists

## Documentation
- [ ] OpenAPI/Swagger documents all endpoints
- [ ] README explains how to run the project
- [ ] Environment variables are documented
- [ ] API versioning strategy is documented
