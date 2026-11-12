---
id: ADR-0003
title: Adopt GOV.UK Design System for User Interface
component: frontend-ui
domain: user-experience
tags:
- gds
- accessibility
- design-system
status: accepted
created: '2026-03-30'
updated: '2026-03-30'
---

# ADR-0003: Adoption of GOV.UK Design System (GDS)

## Context
The Hippo Digital Service must provide an accessible, trustworthy, and consistent user interface that conforms to public sector digital guidelines and WCAG 2.2 Level AA accessibility standards.

## Decision
We adopt the GOV.UK Design System (GDS) styles, layout patterns, and component conventions for all user-facing pages.
All UI pages will use GDS markup conventions (`govuk-width-container`, `govuk-main-wrapper`, `govuk-heading-*`, GDS form components) and functional colour tokens.

## Options Considered
- **GOV.UK Design System (Adopted)**: Proven accessibility, user familiarity, clear guidance, built-in compliance with UK service standards.
- **Custom UI Library with Tailwind CSS**: Flexible, but requires significant effort to build, test, and verify WCAG 2.2 AA accessibility and standard government design patterns.
- **Bootstrap**: Fast initial prototyping, but does not comply natively with UK public service expectations and requires extensive overrides.

## Consequences
- **Positive**: High baseline accessibility, accelerated UI development, familiar layout for UK users.
- **Negative**: Strict adherence required; custom visual styling is limited by design standards.