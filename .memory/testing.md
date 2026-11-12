# Hippo Digital Service — Test Strategy

## Overview

This test strategy defines the verification process for the Hippo Digital Service. The goal is to ensure high reliability, fast feedback during development, complete WCAG 2.2 Level AA accessibility compliance, and zero critical vulnerabilities before production releases.

## Test Environments & Access

- **Environments**:
  - `Local`: Developer workstations running .NET 8 SDK and Docker Desktop.
  - `CI (GitHub Actions)`: Ephemeral container runners executing unit, integration, and security scans on every pull request.
  - `Staging`: Cloud container environment mirror of production for manual testing and end-to-end verification.
  - `Production`: Live environment with continuous health monitoring.
- **Access Needs**:
  - CI pipeline runners require access to GitHub Secrets (container registry credentials, code scanning tokens).
  - Staging access uses test credentials provided by the identity provider sandbox.
- **Data Management**:
  - Integration tests initialize fresh database schemas using Testcontainers for PostgreSQL.
  - Test suites execute within transaction scopes or roll back data to ensure test isolation.
- **CI/CD Integration**:
  - Every pull request runs unit tests, integration tests, accessibility scans, and static code analysis.
  - Merges to the main branch trigger container image builds and automated deployment to Staging.

## Testing Approach

| Level | Scope / Objective | Tools / Frameworks | Success Criteria | Responsibilities |
|---|---|---|---|---|
| **Unit** | Individual domain entities, business logic, and application use cases in isolation. | xUnit, FluentAssertions, Moq | Minimum 80% line coverage; 100% pass rate; execute under 30 seconds. | Developers |
| **Component (Web)** | Razor view rendering, GDS tag helpers, and form input component behavior. | Microsoft.AspNetCore.Mvc.Testing, Bunit / AngleSharp | Components render correct GDS HTML classes and accessibility attributes. | Developers |
| **Contract** | API interactions between application layers and external notification/identity systems. | Pact.Net | Verified contracts against mock provider specifications. | Developers, QA |
| **Integration (Mocked)** | ASP.NET Core endpoints, database operations, and repository queries using containers. | WebApplicationFactory, Testcontainers (PostgreSQL), WireMock.Net | All endpoint routes pass; database migrations run cleanly. | Developers, QA |
| **Integration (API / Events)** | Service deployment health checks and database connectivity verification. | Postman CLI / REST Client, curl | HTTP 200 on `/health` endpoint after container deployment. | DevOps, Developers |
| **Acceptance (Functional)** | Feature verification against user stories and GDS journey paths. | Playwright for .NET | All business acceptance criteria satisfied across happy and alternative paths. | QA, Developers |
| **End-to-End (E2E)** | Complete user journeys from browser submission to database verification. | Playwright for .NET | Critical user journeys pass across Chromium, Firefox, and WebKit in CI. | QA, Developers |
| **Performance (API)** | Load, latency, and throughput testing of API endpoints under expected peak traffic. | k6 | Latency p95 < 200ms at 500 requests per second; 0% HTTP 5xx errors. | QA, DevOps |
| **Performance (Web)** | Client-side page load speed, Core Web Vitals, and asset payload budgets. | Google Lighthouse, Playwright trace | Largest Contentful Paint (LCP) < 2.5s; Total Blocking Time (TBT) < 200ms. | Developers, QA |
| **Security** | Static code analysis, dependency vulnerability scanning, and secret detection. | Snyk, GitHub Dependabot, OWASP ZAP | Zero Critical and High severity vulnerabilities; zero secrets committed. | Security, Developers |
| **Accessibility** | Automated and manual audit for WCAG 2.2 Level AA conformance. | axe-core (via Playwright / Axe.Windows), Screen Readers | 100% automated axe audit pass; full keyboard navigability; clear focus rings. | QA, UX, Developers |

## Risk & Mitigation

| Risk | Mitigation |
|---|---|
| E2E test flakiness (async state and network latency) | Use state-based expectations (for example `Expect(locator).ToBeVisibleAsync()`), avoid fixed sleep calls. |
| Third-party API availability in CI | Virtualize external HTTP calls using WireMock.Net (see [ASSUME-0004](assumptions/ASSUME-0004-test-container-isolation.md)). |
| Database test data contamination | Launch fresh PostgreSQL containers per test fixture using Testcontainers with automatic disposal. |
| Accessibility regressions during rapid UI updates | Run automated axe-core accessibility checks in the CI test pipeline on every UI page route. |

## Assumptions

- [ASSUME-0004](assumptions/ASSUME-0004-test-container-isolation.md): Integration tests execute against containerized mocks without external network dependencies.

## Reviewed by

| Name | Role | Approved | Date |
|---|---|---|---|
| Lead Developer | Tech Lead | [x] | 2026-03-30 |
| QA Specialist | Test Lead | [x] | 2026-03-30 |
| Product Owner | Product Manager | [x] | 2026-03-30 |
