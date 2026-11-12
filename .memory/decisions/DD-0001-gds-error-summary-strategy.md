---
id: DD-0001
title: Standardize Form Validation with GDS Error Summary
component: frontend-ui
domain: accessibility
tags:
- gds
- forms
- validation
- accessibility
status: accepted
created: '2026-03-30'
updated: '2026-03-30'
---

## Context
Users submitting online forms in the digital service must receive clear, accessible, and immediate feedback when submission errors occur. Inaccessible or inconsistent error displays increase drop-off rates and violate government accessibility requirements.

## Options Considered
1. **GDS Standard Error Summary and Field-Level Validation (Selected)**: Display a prominent `govuk-error-summary` block at the top of the page, move keyboard focus to the summary on postback, and pair it with inline `govuk-error-message` spans directly above each invalid input.
2. **Client-Side Modal Dialog / Toast Notifications**: Show pop-up alerts with error messages.
3. **Pure Browser Default HTML5 Tooltips**: Rely on native browser pop-up validation bubbles.

## Evaluation
- Option 1 strictly complies with GDS guidelines and WCAG 2.2 AA accessibility requirements. Screen readers announce the error summary, and keyboard users can navigate immediately to invalid fields.
- Option 2 causes accessibility barriers for screen reader users and fails GDS pattern requirements.
- Option 3 provides inconsistent visual experiences across different browsers and cannot be styled to meet contrast or plain language criteria.

## Decision
We implement Option 1. All forms must render a `govuk-error-summary` at the top of the page linked to field identifiers via anchor links, with matching `govuk-error-message` indicators above individual input fields.

## Consequences
- **Positive**: Full compliance with GDS standards and WCAG 2.2 AA. Enhanced usability for screen reader and keyboard-only users.
- **Negative**: Requires strict coordinate naming between error summary anchor targets and input IDs in Razor views.