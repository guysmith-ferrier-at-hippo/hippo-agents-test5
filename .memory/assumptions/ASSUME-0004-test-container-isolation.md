---
id: ASSUME-0004
title: Integration tests execute against containerized mocks without external dependencies
component: test-suite
domain: testing
tags:
- testing
- testcontainers
- ci-cd
status: unresolved
created: '2026-03-30'
updated: '2026-03-30'
---

## Assumption Description
Automated integration and end-to-end test suites run against containerized database instances using Testcontainers and mock HTTP servers (such as WireMock.Net) in CI environments without external network dependencies.

## Context & Rationale
Running integration tests against isolated containers prevents network flakiness, credential leakages, and external API rate limit constraints.

## Impact If Wrong
If real external staging services must be contacted during CI runs, tests will experience network flakiness, high latency, and intermittent test failures.

## Validation Method
Execute the integration test suite in GitHub Actions without external network ingress/egress dependencies.