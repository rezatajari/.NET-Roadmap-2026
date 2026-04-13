# Practical .NET Roadmap for 2026

**The only guide you need to go from zero to job-ready .NET developer.**

---

## Introduction: Why Most Developers Fail

Let's be honest. Most aspiring .NET developers fail not because they're not smart enough, but because they learn the wrong things in the wrong order.

Here's the typical pattern:

1. Watch a 40-hour C# course
2. Jump into microservices and Clean Architecture
3. Try to learn Docker, Kubernetes, RabbitMQ, and gRPC all at once
4. Build zero real projects
5. Can't pass a technical interview

**The problem isn't lack of effort. It's lack of direction.**

Random YouTube videos and "complete" courses teach you *about* technologies. They don't teach you how to *build things* that companies actually need.

### What This Roadmap Does Differently

This roadmap is built around one idea: **learn by building, in the right order.**

Every step mirrors what real .NET developers do at real companies. You won't learn Redis because it's on a fancy diagram — you'll learn it when your API is slow and you need caching.

No fluff. No "learn everything." Just the path that gets you hired.

---

## The Real .NET Developer Journey

This is the core of the roadmap. Follow these steps **in order**. Don't skip ahead.

---

### Step 1: Build Your First API

**What you're building:** A simple REST API for a task management app. Users can create, read, update, and delete tasks.

**What you need to learn:**
- C# fundamentals (classes, interfaces, async/await, LINQ)
- ASP.NET Core Minimal APIs or Controllers
- HTTP methods (GET, POST, PUT, DELETE) and status codes
- Routing and model binding
- JSON serialization
- How to use Swagger/OpenAPI for testing

**What to ignore for now:**
- Authentication
- Databases (use an in-memory list)
- Docker
- Any design pattern beyond basic separation
- Frontend frameworks

**Real-world example:** Every company has internal tools with CRUD APIs. Your first job will involve building or maintaining endpoints exactly like this.

**Common beginner mistakes:**
- Overcomplicating the project structure before you understand the basics
- Trying to implement "Clean Architecture" on day one
- Not learning HTTP status codes properly (returning 200 for everything)
- Skipping async/await because it "works without it"

**You're ready to move on when:**
- You can create a full CRUD API from scratch without a tutorial
- You understand the request/response cycle
- You can explain what middleware is
- You're comfortable with dependency injection basics

**Classification:**
| Topic | Priority |
|---|---|
| C# fundamentals | MUST LEARN |
| ASP.NET Core Web API | MUST LEARN |
| Minimal APIs | MUST LEARN |
| Controllers | MUST LEARN |
| Swagger/OpenAPI | MUST LEARN |

---

### Step 2: Add a Database

**What you're building:** Take your task API and persist data to a real database. Add a PostgreSQL (or SQL Server) database with proper migrations.

**What you need to learn:**
- Entity Framework Core (Code First)
- DbContext and entity configuration
- Migrations (create, apply, rollback)
- Basic SQL concepts (even if EF abstracts them)
- Repository pattern (simple version, not over-engineered)
- Connection strings and configuration (appsettings.json)

**What to ignore for now:**
- NoSQL databases
- Dapper (learn it later as an alternative)
- Database sharding or replication
- CQRS

**Real-world example:** Every production app uses a relational database. Most .NET shops use SQL Server or PostgreSQL with EF Core. This is non-negotiable knowledge.

**Common beginner mistakes:**
- Not learning raw SQL basics — EF Core is a tool, not a replacement for understanding databases
- Creating a generic repository that wraps DbContext (adds complexity, zero value)
- Forgetting to use migrations in a team workflow
- Using `Include()` everywhere without understanding the SQL it generates

**You're ready to move on when:**
- You can set up EF Core from scratch
- You can create and run migrations
- You understand lazy vs eager loading
- You can look at a generated SQL query and understand what it does

**Classification:**
| Topic | Priority |
|---|---|
| EF Core | MUST LEARN |
| SQL basics | MUST LEARN |
| PostgreSQL or SQL Server | MUST LEARN |
| Migrations | MUST LEARN |
| Dapper | USE WHEN NEEDED |
| NoSQL / MongoDB | OPTIONAL / SPECIALIZED |

---

### Step 3: Add Validation, Error Handling & Logging

**What you're building:** Make your API production-quality. Add input validation, structured error responses, and logging.

**What you need to learn:**
- FluentValidation (or Data Annotations for simple cases)
- ProblemDetails for error responses (RFC 9457)
- Global exception handling middleware
- Structured logging with Serilog (or built-in ILogger)
- `Result` pattern for service-layer errors vs exceptions

**What to ignore for now:**
- Distributed tracing
- ELK/Grafana stack setup
- Custom exception hierarchies with 15 exception types

**Real-world example:** When a production API returns `500 Internal Server Error` with no details, the on-call developer can't debug it. Companies need APIs that log properly and return meaningful error responses. This is what separates junior code from production code.

**Common beginner mistakes:**
- Using exceptions for control flow (e.g., throwing `NotFoundException` instead of returning a result)
- Not validating input at the API boundary
- Logging sensitive data (passwords, tokens)
- Returning raw exception messages to the client

**You're ready to move on when:**
- Your API returns proper ProblemDetails for all error cases
- You have structured logs that you can actually search
- Validation errors return 400 with clear messages
- You have a global exception handler that catches unhandled errors

**Classification:**
| Topic | Priority |
|---|---|
| FluentValidation | MUST LEARN |
| ProblemDetails | MUST LEARN |
| Serilog / ILogger | MUST LEARN |
| Global exception handling | MUST LEARN |
| Result pattern | USE WHEN NEEDED |

---

### Step 4: Add Authentication & Authorization

**What you're building:** Secure your API. Only authenticated users can access their own tasks. Add JWT authentication and role-based access.

**What you need to learn:**
- JWT (JSON Web Tokens) — how they work, not just copy-paste
- ASP.NET Core Identity (basics)
- Authentication middleware
- Authorization policies and `[Authorize]` attribute
- Claims-based identity
- Refresh tokens

**What to ignore for now:**
- OAuth2 flows in depth (unless you're integrating with external providers)
- Building your own identity server
- OpenID Connect protocol details
- Multi-tenancy

**Real-world example:** Almost every SaaS product has user authentication. Companies use either JWT-based auth or an identity provider like Auth0/Keycloak. You need to understand how tokens work at a fundamental level.

**Common beginner mistakes:**
- Storing JWTs in localStorage (use HttpOnly cookies for web apps)
- Not validating token expiration properly
- Hardcoding secrets in source code
- Making the token lifetime too long (hours, not days)
- Not implementing refresh tokens

**You're ready to move on when:**
- You can implement JWT auth from scratch
- You understand the difference between authentication and authorization
- You can protect endpoints with policies
- You know where tokens are stored and why it matters

**Classification:**
| Topic | Priority |
|---|---|
| JWT authentication | MUST LEARN |
| ASP.NET Core Identity | MUST LEARN |
| Authorization policies | MUST LEARN |
| Refresh tokens | MUST LEARN |
| OAuth2 / OpenID Connect | USE WHEN NEEDED |
| Keycloak / Auth0 | OPTIONAL / SPECIALIZED |

---

### Step 5: Make It Production-Ready

**What you're building:** Take your API and prepare it for real deployment. Add health checks, configuration management, Docker support, and CI/CD basics.

**What you need to learn:**
- Health checks (`/health` endpoint)
- Configuration per environment (Development, Staging, Production)
- Options pattern for strongly typed config
- Docker basics (Dockerfile, docker-compose)
- Basic CI/CD (GitHub Actions)
- HTTPS and CORS configuration

**What to ignore for now:**
- Kubernetes
- Terraform / Infrastructure as Code
- Multi-region deployments
- Service mesh

**Real-world example:** When a company deploys your API, the load balancer pings `/health` to know if your service is alive. If you don't have health checks, your service could be silently broken. Docker is how 90% of .NET services are deployed in 2026.

**Common beginner mistakes:**
- Hardcoding configuration values
- Not having different configs per environment
- Creating a Dockerfile that's 2GB because it includes the SDK
- Skipping Docker entirely ("I'll learn it later")
- Not setting up HTTPS properly

**You're ready to move on when:**
- Your API runs in a Docker container
- You have health checks that verify DB connectivity
- Configuration works across environments without code changes
- You have a basic CI pipeline that builds and tests your code

**Classification:**
| Topic | Priority |
|---|---|
| Health checks | MUST LEARN |
| Options pattern | MUST LEARN |
| Docker | MUST LEARN |
| docker-compose | MUST LEARN |
| GitHub Actions CI/CD | MUST LEARN |
| CORS | MUST LEARN |
| Kubernetes | USE WHEN NEEDED |
| Terraform | OPTIONAL / SPECIALIZED |

---

### Step 6: Add Background Jobs & Messaging

**What you're building:** Your task app now sends email notifications when a task is due. You need background processing and eventually messaging.

**What you need to learn:**
- Background services (`IHostedService`, `BackgroundService`)
- Channels or simple in-process queues
- Hangfire or Quartz.NET for scheduled jobs
- MassTransit with RabbitMQ (when you need service-to-service messaging)

**What to ignore for now:**
- Kafka
- Event sourcing
- Building your own message bus
- Complex saga patterns

**Real-world example:** Every production system has background work — sending emails, processing payments, generating reports. Companies use background services for simple tasks and message queues when services need to communicate.

**Common beginner mistakes:**
- Using `Task.Run()` inside a controller (fire and forget = data loss)
- Not handling failures in background jobs
- Jumping straight to RabbitMQ when `BackgroundService` is enough
- Not making background jobs idempotent

**You're ready to move on when:**
- You can create a background service that processes a queue
- You understand why fire-and-forget is dangerous
- You can set up a basic RabbitMQ consumer/producer
- You know when to use in-process vs distributed messaging

**Classification:**
| Topic | Priority |
|---|---|
| BackgroundService | MUST LEARN |
| Hangfire / Quartz.NET | USE WHEN NEEDED |
| RabbitMQ + MassTransit | USE WHEN NEEDED |
| Kafka | OPTIONAL / SPECIALIZED |
| Event sourcing | OPTIONAL / SPECIALIZED |

---

### Step 7: Scale and Optimize

**What you're building:** Your API is getting popular. Responses are slow. You need caching, better query performance, and rate limiting.

**What you need to learn:**
- Output caching (built-in ASP.NET Core)
- Distributed caching with Redis
- Rate limiting (built-in ASP.NET Core)
- API versioning
- Pagination (cursor-based or offset)
- EF Core query optimization (projections, split queries, compiled queries)
- Resilience with Polly (retry, circuit breaker, timeout)

**What to ignore for now:**
- Building your own distributed cache
- GraphQL (unless specifically needed)
- Premature microservices decomposition

**Real-world example:** When your API handles 10,000 requests/minute, you can't hit the database for every request. Redis caching and proper query optimization are what keep production systems fast. Rate limiting prevents abuse.

**Common beginner mistakes:**
- Caching without invalidation strategy (stale data everywhere)
- Not adding pagination (returning 10,000 records in one response)
- Optimizing before measuring (profile first, optimize second)
- Not using `AsNoTracking()` for read-only queries

**You're ready to move on when:**
- You can identify slow queries and optimize them
- You've implemented Redis caching with proper expiration
- Your API has rate limiting and pagination
- You understand retry and circuit breaker patterns

**Classification:**
| Topic | Priority |
|---|---|
| Output caching | MUST LEARN |
| Redis | USE WHEN NEEDED |
| Rate limiting | MUST LEARN |
| API versioning | MUST LEARN |
| Pagination | MUST LEARN |
| Polly resilience | USE WHEN NEEDED |
| GraphQL | OPTIONAL / SPECIALIZED |

---

### Step 8: Testing

**What you're building:** You need to prove your code works and doesn't break when you change things.

**What you need to learn:**
- Unit testing with xUnit
- Mocking with NSubstitute (or Moq)
- Integration testing with `WebApplicationFactory`
- Testing database interactions with Testcontainers
- What to test and what NOT to test

**What to ignore for now:**
- 100% code coverage
- UI testing
- Performance testing frameworks
- BDD frameworks

**Real-world example:** In any professional team, you'll need to write tests. Not because someone forces you, but because deploying untested code at 4 PM on a Friday is how you ruin your weekend. Integration tests with `WebApplicationFactory` are the highest-value tests for API developers.

**Common beginner mistakes:**
- Testing implementation details instead of behavior
- Mocking everything (including the thing you're testing)
- Writing tests after the code is "done" (it's harder that way)
- Chasing 100% coverage instead of testing critical paths

**You're ready to move on when:**
- You can write unit tests for your services
- You can write integration tests that hit your real API
- You use Testcontainers for database tests
- You know what's worth testing and what isn't

**Classification:**
| Topic | Priority |
|---|---|
| xUnit | MUST LEARN |
| Integration testing | MUST LEARN |
| WebApplicationFactory | MUST LEARN |
| Testcontainers | USE WHEN NEEDED |
| NSubstitute / Moq | MUST LEARN |
| BDD / SpecFlow | OPTIONAL / SPECIALIZED |

---

## What NOT to Learn (What Most .NET Developers Waste Time On)

This section might save you 6 months. Seriously.

### 1. Microservices (Too Early)

Stop. You don't need microservices. You need a well-structured **modular monolith** first.

Most companies run monoliths. Most that run microservices wish they hadn't started with them. Learn to build a clean monolith with clear module boundaries, and you'll know when (and if) to split later.

**Learn microservices when:** You have a monolith that actually needs to scale independently, and your team is large enough to support multiple services.

### 2. Overengineering Design Patterns

You don't need:
- A generic repository wrapping EF Core's DbContext (DbContext IS a repository + unit of work)
- Specification pattern for simple CRUD
- 17 layers of abstraction for a TODO app
- MediatR for every single action (use it when it adds value, not by default)

**Keep it simple.** A controller that calls a service that calls DbContext is fine for 80% of applications.

### 3. Learning Every ORM / Database

Pick **one**: EF Core for most cases, Dapper when you need raw performance. You don't need to learn both plus NHibernate, RepoDb, and LLBLGen.

### 4. Framework-Hopping

ASP.NET Core is your framework. You don't need to also learn:
- Blazor (unless you want full-stack, but this roadmap is for backend)
- MAUI
- WPF/WinForms (legacy, not where jobs are growing)

Focus. Depth beats breadth.

### 5. Bleeding-Edge Features

That preview feature in .NET 10? It's cool. But don't learn it instead of mastering the fundamentals. When a new feature is stable and widely adopted, you'll learn it naturally.

### 6. Certificate Chasing

Microsoft certifications are fine for compliance-driven companies. But no startup or product company will care. Build projects instead. A GitHub profile with 3 well-built APIs beats any certificate.

---

## Real-World Architecture Thinking

Forget complex architecture diagrams. Here's how a real API works:

```
Client Request
     │
     ▼
┌─────────────┐
│  Middleware  │ ← Logging, Auth, CORS, Exception Handling
└──────┬──────┘
       │
       ▼
┌─────────────┐
│  Controller  │ ← Route to the right action, validate input
│  / Endpoint  │
└──────┬──────┘
       │
       ▼
┌─────────────┐
│   Service    │ ← Business logic lives here
│    Layer     │
└──────┬──────┘
       │
       ▼
┌─────────────┐
│  Repository  │ ← Data access (EF Core / Dapper)
│  / DbContext │
└──────┬──────┘
       │
       ▼
┌─────────────┐
│  Database    │ ← PostgreSQL / SQL Server
└─────────────┘
```

### Where Things Happen

**Validation:** At the API boundary (controller/endpoint level). Use FluentValidation. Don't let bad data reach your service layer.

**Authentication/Authorization:** In middleware. ASP.NET Core handles this via `UseAuthentication()` and `UseAuthorization()`. Your controllers just use `[Authorize]`.

**Logging:** Everywhere, but structured. Log at the service layer for business events, middleware for request/response, and let the global exception handler log unhandled errors.

**Caching:** Between your service and the database. Check cache first, fall back to DB, update cache. Use Redis for distributed, in-memory for single-instance.

```
Service → Check Cache → Cache Hit? → Return
                           │ No
                           ▼
                     Query Database → Store in Cache → Return
```

**Error Handling:** Two layers:
1. **Expected errors** (user not found, validation failed) → Handle in service, return Result objects, map to ProblemDetails in controller
2. **Unexpected errors** (DB connection lost, null reference) → Caught by global exception handler middleware, logged, returns generic ProblemDetails

**Configuration:** Loaded at startup from `appsettings.json` → environment-specific overrides → environment variables → user secrets (dev only). Use the Options pattern to inject strongly-typed config.

### The Rule of Thumb

If you're unsure where something goes, ask: *"Would a new developer on the team know where to find this?"*

If the answer is no, your architecture is too clever.

---

## Portfolio Projects

These are not toy projects. Each one solves a real problem and teaches real skills.

---

### Project 1: TaskFlow API
**Roadmap Step:** 1-3
**Problem it solves:** Personal task management — creating, assigning, tracking, and completing tasks.

**What it teaches:**
- CRUD operations
- REST API design
- EF Core with migrations
- Input validation
- Error handling with ProblemDetails
- Structured logging

**How to make it senior-level:**
- Add task prioritization with sorting algorithms
- Implement soft deletes
- Add audit logging (who changed what, when)
- Create a proper API versioning strategy

---

### Project 2: AuthGuard — Authentication Service
**Roadmap Step:** 4
**Problem it solves:** User registration, login, and token management.

**What it teaches:**
- JWT authentication
- Password hashing
- Refresh tokens
- Role-based authorization
- Secure configuration

**How to make it senior-level:**
- Add two-factor authentication (TOTP)
- Implement account lockout after failed attempts
- Add OAuth2 integration (Google login)
- Create an API key system for service-to-service auth

---

### Project 3: ShipReady — Deployment-Ready API Template
**Roadmap Step:** 5
**Problem it solves:** A production-ready API template with health checks, Docker, and CI/CD.

**What it teaches:**
- Docker and docker-compose
- Health checks
- Configuration management
- GitHub Actions CI/CD
- Environment-specific settings

**How to make it senior-level:**
- Add a multi-stage Dockerfile with security scanning
- Implement structured logging that ships to Seq
- Add OpenTelemetry basics
- Create a `Makefile` or PowerShell scripts for common tasks

---

### Project 4: NotifyMe — Notification Service
**Roadmap Step:** 6
**Problem it solves:** Send email/SMS notifications based on events (scheduled or triggered).

**What it teaches:**
- Background services
- Hangfire for scheduled jobs
- RabbitMQ with MassTransit
- Retry logic
- Idempotent processing

**How to make it senior-level:**
- Add multiple notification channels (email, SMS, push)
- Implement notification preferences per user
- Add dead-letter queue handling
- Create a notification audit trail

---

### Project 5: SpeedShop — E-Commerce API with Caching
**Roadmap Step:** 7
**Problem it solves:** Product catalog with search, filtering, and a shopping cart.

**What it teaches:**
- Redis caching
- Pagination (cursor-based)
- Rate limiting
- Query optimization
- API versioning

**How to make it senior-level:**
- Add full-text search
- Implement inventory management with concurrency handling
- Add a webhook system for order events
- Create performance benchmarks with BenchmarkDotNet

---

### Project 6: TestCraft — Fully Tested API
**Roadmap Step:** 8
**Problem it solves:** A project specifically designed to demonstrate comprehensive testing skills.

**What it teaches:**
- Unit testing with xUnit
- Integration testing with WebApplicationFactory
- Testcontainers for database tests
- Test data builders
- Mocking external dependencies

**How to make it senior-level:**
- Add contract testing
- Implement mutation testing
- Create a test coverage report in CI
- Add architecture tests (NetArchTest)

---

### Project 7: ModularHub — Modular Monolith
**Roadmap Step:** All steps combined
**Problem it solves:** A multi-module application (users, orders, notifications) with clean boundaries.

**What it teaches:**
- Modular monolith architecture
- Module-to-module communication
- Shared kernel patterns
- Database-per-module vs shared database
- Everything from Steps 1-8 combined

**How to make it senior-level:**
- Add module-level integration tests
- Implement event-driven communication between modules
- Create a module discovery system
- Add feature flags per module
- Document architectural decision records (ADRs)

---

## Production Mindset

This is what separates juniors from developers companies actually want to hire.

### Logging — Because "It Works on My Machine" Isn't Debugging

Use **Serilog** with structured logging. Every log entry should be searchable.

```csharp
// BAD
_logger.LogInformation("User logged in");

// GOOD
_logger.LogInformation("User {UserId} logged in from {IpAddress}", userId, ipAddress);
```

**Why it matters:** When your API crashes at 2 AM, logs are the only thing standing between you and a long night. Structured logs let you filter by UserId, find the exact request that failed, and understand what happened.

### Health Checks — Because Load Balancers Need to Know

Every production API needs a `/health` endpoint. At minimum, check:
- Database connectivity
- External service availability
- Disk space (if applicable)

**Why it matters:** Kubernetes, Azure App Service, AWS ELB — they all use health checks to route traffic. No health check = your broken instance keeps receiving requests.

### Configuration — Because Hardcoding Gets You Fired

Use the **Options pattern** with `appsettings.json`:
- `appsettings.json` → defaults
- `appsettings.Development.json` → local settings
- `appsettings.Production.json` → production settings
- Environment variables → secrets and overrides

**Never commit secrets. Use User Secrets locally, environment variables or a vault in production.**

### Observability — Because You Can't Fix What You Can't See

Start with the basics:
- **Logs** → What happened (Serilog → Seq or console in JSON format)
- **Metrics** → How much is happening (request count, response times)
- **Traces** → The path of a request through your system

In 2026, OpenTelemetry is the standard. But start with good logging and health checks — you can add tracing later.

### Error Handling with ProblemDetails — Because Users Deserve Good Errors

RFC 9457 defines a standard error format. ASP.NET Core supports it natively.

```json
{
  "type": "https://tools.ietf.org/html/rfc9110#section-15.5.5",
  "title": "Not Found",
  "status": 404,
  "detail": "Task with ID 42 was not found.",
  "instance": "/api/tasks/42"
}
```

**Why it matters:** Consistent error responses make your API predictable. Frontend developers will thank you. Your future self will thank you.

---

## 12-Week Plan

This plan assumes you can dedicate 2-3 hours per day. Adjust based on your schedule and prior experience.

### Week 1-2: C# & Your First API

**Learn:**
- C# fundamentals (classes, interfaces, async/await, LINQ)
- ASP.NET Core Minimal API basics
- HTTP methods and status codes

**Build:**
- TaskFlow API v1 (in-memory, no database)
- 5 endpoints: Create, Read (single + all), Update, Delete

**Practice:**
- Create 3 different CRUD APIs from scratch without tutorials
- Use Swagger to test every endpoint

---

### Week 3-4: Database Integration

**Learn:**
- EF Core Code First
- Migrations
- Basic SQL (SELECT, JOIN, WHERE, INDEX)

**Build:**
- TaskFlow API v2 (PostgreSQL with EF Core)
- Add categories/tags to tasks (one-to-many, many-to-many)

**Practice:**
- Look at the generated SQL queries
- Try writing the same query in raw SQL
- Create and rollback a migration

---

### Week 5-6: Validation, Errors & Logging

**Learn:**
- FluentValidation
- ProblemDetails
- Serilog structured logging
- Global exception handling

**Build:**
- TaskFlow API v3 (production-quality error handling)
- AuthGuard project (start)

**Practice:**
- Try breaking your API with bad input — does it respond correctly?
- Read your logs — can you find specific events?

---

### Week 7-8: Authentication & Authorization

**Learn:**
- JWT tokens
- ASP.NET Core Identity
- Claims and policies

**Build:**
- AuthGuard project (complete)
- Add auth to TaskFlow API

**Practice:**
- Inspect a JWT token (jwt.io)
- Try accessing protected endpoints without a token
- Implement role-based access (admin vs regular user)

---

### Week 9-10: Production Readiness

**Learn:**
- Docker (Dockerfile, docker-compose)
- Health checks
- Options pattern
- GitHub Actions basics

**Build:**
- ShipReady template
- Dockerize TaskFlow API
- Create a CI pipeline

**Practice:**
- Run your API in Docker
- Change config without rebuilding
- Break a health check and see what happens

---

### Week 11-12: Caching, Background Jobs & Testing

**Learn:**
- Redis caching
- BackgroundService
- xUnit + WebApplicationFactory
- Integration testing

**Build:**
- Add caching to TaskFlow API
- Add a background job (send notifications for due tasks)
- Write integration tests for all endpoints

**Practice:**
- Measure response times before and after caching
- Write a test that fails, then make it pass
- Run your full test suite in CI

---

### After Week 12: What's Next

You now have:
- A solid foundation in .NET backend development
- 3+ portfolio projects
- Real production skills (Docker, CI/CD, testing, logging)

Next steps:
1. Build Project 5 (SpeedShop) or Project 7 (ModularHub)
2. Start contributing to open-source .NET projects
3. Apply for jobs — you're ready for junior/mid-level .NET positions

---

## What NOT to Learn First (MUST vs OPTIONAL Summary)

### MUST LEARN (Core for 80% of jobs)
- C# (async/await, LINQ, generics, interfaces)
- ASP.NET Core Web API
- EF Core
- SQL basics
- FluentValidation
- ProblemDetails
- JWT authentication
- Docker
- xUnit + integration testing
- Serilog / structured logging
- Health checks
- Git

### USE WHEN NEEDED (Advanced but not required to start)
- Redis
- RabbitMQ + MassTransit
- Polly (resilience)
- Dapper
- Hangfire / Quartz.NET
- MediatR
- CQRS
- Testcontainers
- OpenTelemetry
- API versioning (built-in)
- gRPC

### OPTIONAL / SPECIALIZED (Don't learn unless your job requires it)
- Microservices architecture
- Kubernetes
- Kafka
- Event sourcing
- GraphQL
- Blazor / MAUI
- Terraform
- Service mesh (Istio, Linkerd)
- SignalR (unless you need real-time)
- MongoDB (unless your project uses it)

---

## If I Were Starting .NET in 2026

Here's what I'd do. No sugar-coating.

**Month 1:** I'd learn C# properly. Not by reading a book — by writing code every single day. I'd build a CRUD API in the first week and a more complex one by week 3. I'd use ASP.NET Core Minimal APIs because they're simpler, and I'd switch to controllers when I need them.

**Month 2:** I'd add a real database with EF Core, learn JWT auth, and make my API production-quality with proper error handling and logging. I'd Dockerize everything.

**Month 3:** I'd add caching, a background service, and write integration tests. By the end of this month, I'd have 3-4 real projects on GitHub that actually demonstrate I can build things.

**What I would NOT do:**
- I wouldn't watch 100 hours of video courses. I'd watch specific videos when I'm stuck on a specific problem.
- I wouldn't learn microservices. Not because they're bad, but because they're the wrong tool for someone who hasn't built a solid monolith yet.
- I wouldn't chase certifications. I'd build projects.
- I wouldn't try to learn everything. I'd get dangerously good at building APIs.
- I wouldn't use Clean Architecture templates I don't understand. I'd keep my structure simple until I felt the pain that architecture solves.

**The uncomfortable truth:** Most developers spend 6 months "learning" and have nothing to show for it. You can spend 3 months building real things and have a portfolio that gets you interviews.

The difference isn't talent. It's focus.

**Pick one thing. Build it. Ship it. Repeat.**

That's the entire roadmap.
