---
id: KB-0001
title: Clean Architecture Dependency and Inversion Rules
component: architecture
domain: clean-architecture
tags:
- dotnet
- clean-architecture
- dependency-injection
status: validated
created: '2026-03-30'
updated: '2026-03-30'
---

## Clean Architecture Dependency Rule in .NET

### What Happened & Core Rule
The project enforces strict inward dependency flow following Clean Architecture:
- `Domain` has no dependencies on any external framework or layer.
- `Application` depends only on `Domain`. Interfaces for external services (repositories, notifications, identity) are defined in `Application`.
- `Infrastructure` implements interfaces defined in `Application` and references `Domain` and `Application`.
- `Web` (Presentation) depends on `Application` and `Infrastructure` (solely for dependency injection wiring in `Program.cs`).

### Why It Matters
Violating this rule by referencing `Infrastructure` or EF Core types directly within `Domain` or `Application` use cases compromises testability and causes tight coupling to database mechanisms.

### Applicability & Verification
All developers and coding agents must maintain this separation. Unit tests for `Domain` and `Application` layers must not require database connections or external services.