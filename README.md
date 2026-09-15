# Transaction Platform · Backend Scaffold

**Java 21 · Spring Boot 4.0.2 · Maven**

An early backend foundation for a transaction-management learning project.

[Portfolio](https://github.com/saranyaelavarthi/development) · [Current scope](#current-scope) · [Local setup](#local-setup) · [Roadmap](#roadmap)

## Current scope

The repository currently contains a Spring Boot entry point, Maven wrapper, application configuration, and a generated application-context test.

| Area | Status |
| --- | --- |
| Spring Boot application skeleton | Present |
| Web MVC, validation, JPA, and security dependencies | Configured in Maven |
| PostgreSQL driver | Configured in Maven |
| Transaction endpoints and persistence models | Planned |
| Custom authentication and authorization | Planned |
| Business-rule and integration tests | Planned |

The repository name describes the intended direction. Transaction processing and a custom security model have not yet been implemented.

## Local setup

Requirements: **JDK 21** and a local **PostgreSQL** instance. The database name and credentials must be configured before starting the application because the scaffold includes JPA.

1. Create an empty PostgreSQL database named `transaction_platform` using your local database tools.
2. Set these environment variables to your local configuration:

| Variable | Value |
| --- | --- |
| `SPRING_DATASOURCE_URL` | `jdbc:postgresql://localhost:5432/transaction_platform` |
| `SPRING_DATASOURCE_USERNAME` | Your local PostgreSQL username |
| `SPRING_DATASOURCE_PASSWORD` | Your local PostgreSQL password |

3. Start the application from the backend directory:

```bash
git clone https://github.com/saranyaelavarthi/secure-transaction-platform.git
cd secure-transaction-platform/backend
sh ./mvnw spring-boot:run
```

On Windows, use `.\mvnw.cmd spring-boot:run` instead.

The scaffold uses Spring Security's default configuration; there are no custom transaction routes to call yet. Starting the server is a scaffold check, not an end-to-end transaction demo.

## Repository guide

| Path | Purpose |
| --- | --- |
| [backend/pom.xml](backend/pom.xml) | Dependencies and Java version |
| [backend/src/main/java](backend/src/main/java) | Application entry point |
| [backend/src/main/resources/application.properties](backend/src/main/resources/application.properties) | Application name; connection settings come from the environment |
| [backend/src/test/java](backend/src/test/java) | Generated application-context test |

Run `sh ./mvnw test` from `backend/` with the database environment configured. Windows: `.\mvnw.cmd test`. The existing test checks context loading; it does not validate transaction behavior.

## Roadmap

- [ ] Define transaction entities and versioned database migrations.
- [ ] Build validated REST endpoints with consistent error responses.
- [ ] Implement and test authentication and role-based permissions.
- [ ] Add idempotency and concurrent-update handling.
- [ ] Cover business rules and database behavior with automated tests.
- [ ] Add a reproducible local deployment and CI workflow.
