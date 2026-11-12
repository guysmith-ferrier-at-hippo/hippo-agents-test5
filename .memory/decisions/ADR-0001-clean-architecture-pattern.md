---
id: ADR-0001
title: Adopt Clean Architecture Pattern for Service Structure
component: backend-architecture
domain: architecture
tags:
- clean-architecture
- dotnet8
- patterns
status: accepted
created: '2026-03-30'
updated: '2026-03-30'
---

# ADR-0001: Clean Architecture Pattern

## Context
The Hippo Digital Service requires clear separation between business logic, presentation logic, and external infrastructure integrations. Coupling business rules with database access or web delivery mechanisms increases technical debt, degrades testability, and slows future evolution.

## Decision
We adopt Clean Architecture principles for the service solution layout.
The solution organizes into four distinct layers:
1. **Domain**: Pure business entities, value objects, domain exceptions, and domain logic. No external dependencies.
2. **Application**: Use cases, commands, queries, interfaces for external dependencies, and DTOs.
3. **Infrastructure**: Database persistence (EF Core), external API clients, message publishers, and identity integrations.
4. **Web / Presentation**: ASP.NET Core controllers, Razor Pages or API endpoints, GDS UI components, and HTTP middleware.

Dependencies point inward toward the Domain.

## Options Considered
- **Clean Architecture (Adopted)**: High testability, decoupled dependencies, clear boundaries.
- **Traditional 3-Tier Layered Architecture**: Simpler initial setup, but often leads to tight coupling between business logic and database persistence models.
- **Microservices Architecture**: Extreme decoupling, but unnecessary complexity and operational overhead for the current maturity stage.

## Consequences
- **Positive**: Domain logic remains completely testable without external databases or frameworks. Easy mocking of infrastructure.
- **Negative**: Additional project files and mapping layers between Domain and Presentation entities. Small initial development overhead.