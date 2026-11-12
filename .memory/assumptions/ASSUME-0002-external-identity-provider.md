---
id: ASSUME-0002
title: User authentication delegates to external OIDC provider
component: auth-service
domain: security
tags:
- authentication
- oidc
- identity
status: unresolved
created: '2026-03-30'
updated: '2026-03-30'
---

## Assumption Description
The digital service delegates user authentication to an OpenID Connect (OIDC) identity provider rather than managing internal username and password stores.

## Context & Rationale
Delegating authentication to a standards-compliant identity provider improves security posture and complies with enterprise identity standards.

## Impact If Wrong
If an external identity provider is not available, the service team must build local identity management, credential reset workflows, and MFA support.

## Validation Method
Confirm identity provider specifications and sandbox availability with technical stakeholders during Discovery/Alpha.