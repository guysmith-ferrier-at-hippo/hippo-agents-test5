---
id: ADR-0002
title: Use PostgreSQL and Entity Framework Core for Data Persistence
component: database
domain: data-persistence
tags:
- postgresql
- efcore
- database
status: accepted
created: '2026-03-30'
updated: '2026-03-30'
---

# ADR-0002: PostgreSQL with Entity Framework Core for Data Persistence

## Context
The application needs a reliable, relational database management system capable of supporting transactional integrity, structured queries, schema migrations, and enterprise data security.

## Decision
We select PostgreSQL as the primary relational database and Entity Framework Core (EF Core) as the Object-Relational Mapper (ORM) using the `Npgsql.EntityFrameworkCore.PostgreSQL` provider.

Database migrations will be managed via EF Core Code-First migrations and executed in CI/CD deployment pipelines.

## Options Considered
- **PostgreSQL with EF Core (Adopted)**: Robust open-source relational engine, rich features (JSONB, full text, ACID compliance), native .NET support, strong community.
- **SQL Server with EF Core**: Fully featured, but higher licensing costs and vendor lock-in risk.
- **MongoDB / NoSQL**: Flexible schemas, but lacks native relational constraints and complex ACID transaction handling needed for structured applications and audit requirements.

## Consequences
- **Positive**: Standardized schema migration tooling, strong relational integrity, container-friendly testing using Testcontainers.
- **Negative**: Developers must ensure LINQ queries are optimized and avoid N+1 query patterns.