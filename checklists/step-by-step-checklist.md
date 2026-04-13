# Step 1 Checklist: Build Your First API

Use this checklist to track your progress. Don't move to Step 2 until everything is checked.

## C# Fundamentals
- [ ] I can create classes with properties and methods
- [ ] I understand interfaces and why they exist
- [ ] I can use async/await and know why it matters
- [ ] I can write LINQ queries (Where, Select, FirstOrDefault, Any)
- [ ] I understand null safety (nullable reference types)
- [ ] I know the difference between value types and reference types

## ASP.NET Core Basics
- [ ] I can create a new ASP.NET Core project from scratch
- [ ] I understand the request pipeline (middleware)
- [ ] I can create Minimal API endpoints
- [ ] I can create Controller-based endpoints
- [ ] I understand routing (attribute routing, route parameters)
- [ ] I can use dependency injection (register + inject services)

## REST API Concepts
- [ ] I know when to use GET, POST, PUT, DELETE
- [ ] I return correct status codes (200, 201, 204, 400, 404, 500)
- [ ] I can serialize/deserialize JSON
- [ ] I can use Swagger/OpenAPI to test my endpoints
- [ ] I understand query parameters vs route parameters

## Proof of Understanding
- [ ] I can build a complete CRUD API without following a tutorial
- [ ] I can explain what middleware is to someone else
- [ ] I can register and inject a service using DI
- [ ] I can handle basic errors (return 404 when item not found)

---

# Step 2 Checklist: Add a Database

## EF Core
- [ ] I can set up a DbContext with entity configurations
- [ ] I can create and apply migrations
- [ ] I can rollback a migration
- [ ] I understand Code First vs Database First (and chose Code First)
- [ ] I can configure relationships (one-to-many, many-to-many)
- [ ] I know the difference between Fluent API and Data Annotations

## SQL Basics
- [ ] I can write a SELECT query with WHERE and ORDER BY
- [ ] I understand JOINs (INNER, LEFT)
- [ ] I know what an INDEX is and when to create one
- [ ] I can look at EF Core's generated SQL and understand it

## Data Access Patterns
- [ ] I use DbContext directly (not wrapped in a generic repository)
- [ ] I understand when to use AsNoTracking()
- [ ] I can explain Include() and what SQL it generates
- [ ] I handle concurrent updates properly

## Proof of Understanding
- [ ] My API persists data to PostgreSQL (or SQL Server)
- [ ] I have proper migrations checked into source control
- [ ] I can add a new entity with relationships and generate a migration
- [ ] I can query related data efficiently

---

# Step 3 Checklist: Validation, Errors & Logging

## Validation
- [ ] I use FluentValidation for input validation
- [ ] Validation happens at the API boundary (endpoint level)
- [ ] Invalid requests return 400 with clear error messages
- [ ] I validate all user input (never trust the client)

## Error Handling
- [ ] I have a global exception handler middleware
- [ ] All errors return ProblemDetails format
- [ ] I never expose exception details in production
- [ ] I understand the difference between expected and unexpected errors
- [ ] 404s return ProblemDetails (not empty responses)

## Logging
- [ ] I use structured logging (Serilog or built-in ILogger)
- [ ] I log with proper levels (Information, Warning, Error)
- [ ] I use message templates, NOT string interpolation
- [ ] I never log sensitive data (passwords, tokens, PII)
- [ ] I can search my logs for specific events

## Proof of Understanding
- [ ] I can break my API with bad input and get a clear 400 response
- [ ] Unhandled exceptions return a generic 500 with ProblemDetails
- [ ] I can find a specific request in my logs by searching for a value

---

# Step 4 Checklist: Authentication & Authorization

## Authentication
- [ ] I understand how JWT tokens work (header, payload, signature)
- [ ] I can implement user registration with password hashing
- [ ] I can implement login and return JWT + refresh token
- [ ] I validate tokens properly (issuer, audience, expiration, signature)
- [ ] I use secure token storage (HttpOnly cookies for web)

## Authorization
- [ ] I can protect endpoints with [Authorize]
- [ ] I understand claims-based identity
- [ ] I can implement role-based access control
- [ ] I can create custom authorization policies
- [ ] Users can only access their own resources

## Security Basics
- [ ] Secrets are NOT in source code
- [ ] I use User Secrets for local development
- [ ] Token expiration is reasonable (not days)
- [ ] I have implemented refresh token rotation

## Proof of Understanding
- [ ] Unauthenticated requests return 401
- [ ] Unauthorized requests return 403
- [ ] I can explain the auth flow from login to protected request
- [ ] Tokens expire and refresh tokens work correctly

---

# Step 5 Checklist: Production Ready

## Docker
- [ ] I have a multi-stage Dockerfile
- [ ] My Docker image uses an Alpine base (small size)
- [ ] The app runs as a non-root user in the container
- [ ] I have a docker-compose for local development
- [ ] I can build and run my app in Docker

## Configuration
- [ ] I use appsettings.json with environment-specific overrides
- [ ] I use the Options pattern for strongly typed config
- [ ] Secrets are in environment variables (not in config files)
- [ ] I can change config without rebuilding the app

## Health Checks
- [ ] I have a /health endpoint
- [ ] Health check verifies database connectivity
- [ ] Health check verifies Redis connectivity (if used)

## CI/CD
- [ ] I have a GitHub Actions workflow that builds the project
- [ ] Tests run automatically on every PR
- [ ] Docker image is built in CI

## Proof of Understanding
- [ ] I can run my entire app stack with docker-compose up
- [ ] Config changes don't require code changes or rebuilds
- [ ] CI catches build failures and test failures automatically

---

# Step 6 Checklist: Background Jobs & Messaging

## Background Services
- [ ] I can create a BackgroundService
- [ ] I understand IHostedService lifecycle
- [ ] I know why Task.Run in a controller is dangerous
- [ ] My background jobs handle errors gracefully

## Messaging (when needed)
- [ ] I understand producer/consumer pattern
- [ ] I can set up RabbitMQ with MassTransit
- [ ] I make my consumers idempotent
- [ ] I handle poison messages / dead letters

## Proof of Understanding
- [ ] I have a background service that processes work reliably
- [ ] I can explain when to use in-process vs distributed messaging
- [ ] Failed jobs are retried and eventually dead-lettered

---

# Step 7 Checklist: Scale & Optimize

## Caching
- [ ] I use output caching for read-heavy endpoints
- [ ] I can set up Redis for distributed caching
- [ ] I have a cache invalidation strategy
- [ ] I cache the right things (not everything)

## Performance
- [ ] I use pagination on list endpoints
- [ ] I use AsNoTracking() for read-only queries
- [ ] I use projections (Select) instead of loading entire entities
- [ ] I've identified and optimized slow queries

## API Design
- [ ] I have rate limiting configured
- [ ] I have API versioning
- [ ] I use Polly for resilience (retry, circuit breaker)

## Proof of Understanding
- [ ] I can measure the performance impact of caching
- [ ] I can identify N+1 query problems
- [ ] Rate-limited requests return 429

---

# Step 8 Checklist: Testing

## Unit Tests
- [ ] I can write unit tests with xUnit
- [ ] I can mock dependencies with NSubstitute (or Moq)
- [ ] I test behavior, not implementation details
- [ ] I use the Arrange-Act-Assert pattern

## Integration Tests
- [ ] I can test my API with WebApplicationFactory
- [ ] I can test database interactions with Testcontainers
- [ ] My tests are independent (don't depend on each other)
- [ ] I test happy paths AND error paths

## Testing Strategy
- [ ] I know what's worth testing (critical business logic, edge cases)
- [ ] I don't chase 100% coverage
- [ ] My tests run in CI automatically
- [ ] I can add a test for a bug before fixing it

## Proof of Understanding
- [ ] I have unit tests for my service layer
- [ ] I have integration tests for my API endpoints
- [ ] All tests pass in CI
- [ ] I can TDD a simple feature
