# Portfolio Projects

Detailed guides for each portfolio project from the roadmap.

---

## Project 1: TaskFlow API
**Step:** 1-3 | **Difficulty:** Beginner

A task management API. CRUD operations, database, validation, error handling, logging.

### Getting Started
1. Create a new ASP.NET Core Web API project
2. Use the templates from `/templates` as your starting point
3. Follow Steps 1-3 in the roadmap

### Core Features
- Create, read, update, delete tasks
- Categories and tags
- Due dates and completion tracking
- User-specific task lists (after Step 4)

### Extension Ideas (Senior Level)
- Audit trail (track all changes with timestamps and user)
- Soft deletes with recovery
- Task prioritization with drag-and-drop ordering
- Recurring tasks with scheduling rules
- Export tasks to CSV/PDF

---

## Project 2: AuthGuard
**Step:** 4 | **Difficulty:** Beginner-Intermediate

A standalone authentication service with JWT, refresh tokens, and role management.

### Core Features
- User registration with password hashing (BCrypt)
- Login with JWT token generation
- Refresh token rotation
- Role-based access (Admin, User)

### Extension Ideas (Senior Level)
- Two-factor authentication (TOTP with QR code)
- Account lockout after N failed attempts
- OAuth2 integration (Google, GitHub login)
- API key management for service accounts
- Password reset flow with email verification

---

## Project 3: ShipReady
**Step:** 5 | **Difficulty:** Intermediate

A production-ready API template with all the infrastructure pieces.

### Core Features
- Multi-stage Dockerfile
- docker-compose with PostgreSQL, Redis, Seq
- Health checks
- Configuration management
- GitHub Actions CI/CD

### Extension Ideas (Senior Level)
- OpenTelemetry tracing
- Prometheus metrics endpoint
- Terraform for cloud deployment
- Multi-environment deployment (staging → production)
- Security scanning in CI (Trivy, dotnet-security)

---

## Project 4: NotifyMe
**Step:** 6 | **Difficulty:** Intermediate

A notification service that sends emails/SMS based on events or schedules.

### Core Features
- Background service for processing notifications
- Scheduled jobs with Hangfire
- Email sending (SMTP or SendGrid)
- RabbitMQ consumer for event-triggered notifications

### Extension Ideas (Senior Level)
- Multi-channel delivery (email, SMS, push notification)
- User notification preferences
- Delivery tracking and read receipts
- Template engine for notification content
- Dead-letter queue handling with admin dashboard

---

## Project 5: SpeedShop
**Step:** 7 | **Difficulty:** Intermediate-Advanced

An e-commerce API with product catalog, search, and cart — focused on performance.

### Core Features
- Product CRUD with categories
- Search and filtering
- Shopping cart
- Redis caching for product catalog
- Cursor-based pagination
- Rate limiting

### Extension Ideas (Senior Level)
- Full-text search with PostgreSQL
- Inventory management with optimistic concurrency
- Webhook system for order events
- Performance benchmarks with BenchmarkDotNet
- API versioning with backward compatibility

---

## Project 6: TestCraft
**Step:** 8 | **Difficulty:** Intermediate

A project specifically designed to showcase comprehensive testing skills.

### Core Features
- Unit tests for business logic (xUnit)
- Integration tests with WebApplicationFactory
- Database tests with Testcontainers
- Mocking external services with NSubstitute
- Test data builders

### Extension Ideas (Senior Level)
- Architecture tests with NetArchTest
- Contract testing for API consumers
- Mutation testing
- Test coverage reports in CI
- Load testing with k6 or NBomber

---

## Project 7: ModularHub
**Step:** All | **Difficulty:** Advanced

A modular monolith combining everything you've learned. Multiple modules (Users, Tasks, Notifications) with clean boundaries.

### Core Features
- Module-based project structure
- Each module has its own DbContext
- Inter-module communication via events
- Shared kernel for common types
- Everything from Steps 1-8

### Extension Ideas (Senior Level)
- Extract a module into a separate service (microservice migration)
- Feature flags per module
- Module-level health checks
- Architectural Decision Records (ADRs)
- API gateway pattern for module routing

---

## How to Present These on GitHub

1. **Each project gets its own repository**
2. **Write a clear README** with:
   - What the project does
   - How to run it (`docker-compose up`)
   - API documentation (Swagger link)
   - Architecture diagram (simple)
3. **Include tests** — this is what hiring managers look for
4. **Use conventional commits** — shows professionalism
5. **Add a CI badge** — shows the project builds and tests pass

### Example README Badge Section
```markdown
![Build Status](https://github.com/yourusername/taskflow-api/actions/workflows/ci.yml/badge.svg)
![.NET](https://img.shields.io/badge/.NET-9.0-purple)
![License](https://img.shields.io/badge/license-MIT-blue)
```
