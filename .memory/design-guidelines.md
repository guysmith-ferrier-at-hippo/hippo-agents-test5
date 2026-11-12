# Hippo Digital Service — Design Guidelines

> This document is the canonical design reference for the Hippo Digital Service. Every engineer and AI agent must read this document before generating or modifying user interface components.

---

## 1. Design Philosophy

This service is a public digital service. Users arrive with a specific task or transaction to complete. Many users feel anxious, experience time constraints, or use mobile devices.

The restraint of the GOV.UK Design System (GDS) is a deliberate signal of authority, calm, and trustworthiness. Every design decision must support that signal. Do not add unnecessary visual complexity to solve a content problem.

---

## 2. Design System Reference

All user interface elements must use components, tokens, and patterns from these sources in priority order:

1. **GDS Design System** — https://design-system.service.gov.uk
2. **GOV.UK Component Guide** — https://components.publishing.service.gov.uk/component-guide
3. **Project Design Decisions** — Documented in `.memory/decisions/`

---

## 3. Colour

*Source: https://design-system.service.gov.uk/styles/colour/*

All colours must originate from GDS design tokens. Never write hardcoded hexadecimal values in component code.

### Functional Colour Tokens

| Token | Hex | Use |
|---|---|---|
| `text` | `#0b0c0c` | All body text |
| `secondary-text` | `#484949` | Supporting and metadata text |
| `body-background` | `#ffffff` | Page background |
| `link` | `#1a65a6` | Default hyperlink colour |
| `link-hover` | `#0f385c` | Hyperlink hover state |
| `link-visited` | `#54319f` | Visited hyperlink state |
| `focus` | `#ffdd00` | Focus ring outline only — do not use for any other purpose |
| `focus-text` | `#0b0c0c` | Text colour against focus background |
| `error` | `#d4351c` | Form and banner error states |
| `success` | `#00703c` | Success notifications and confirmations |
| `border` | `#b1b4b6` | Field borders and content dividers |

### Rules for Colour

- Always use the GDS colour palette.
- Never use colour as the only indicator of status. Always combine colour with explicit text or icons.
- The focus ring colour (`#ffdd00`) is mandatory for WCAG 2.2 compliance. Do not change or remove it.

---

## 4. Typography

*Source: https://design-system.service.gov.uk/styles/headings/*

### Heading Classes

GDS heading classes are visual modifiers and do not replace semantic HTML tags.

| Class | HTML Tag | Use |
|---|---|---|
| `govuk-heading-xl` | `h1` | Primary page title. Exactly one per page. |
| `govuk-heading-l` | `h2` | Major section within a page |
| `govuk-heading-m` | `h3` | Sub-section within an h2 |
| `govuk-heading-s` | `h4` | Minor subsection (use sparingly) |
| `govuk-caption-xl` | `span` in `h1` | Contextual category label above main page title |
| `govuk-caption-l` | `span` in `h2` | Contextual label above section title |

### Body Text Classes

| Class | Tag | Use |
|---|---|---|
| `govuk-body-l` | `p` | Lead paragraph — immediate first paragraph after `h1` |
| `govuk-body` | `p` | Standard body content |
| `govuk-body-s` | `p` | Supporting notes, metadata, and timestamps |

### Rules for Typography

- Every heading element must declare a `govuk-heading-*` class.
- Do not skip heading levels (an `h3` must only exist inside an `h2` section).
- Do not place `<strong>` or `<b>` tags inside heading elements.
- Write all headings in sentence case. Do not place full stops at the end of headings.

---

## 5. Layout & Grid

*Source: https://design-system.service.gov.uk/styles/layout/*

### Page Structure

Every page uses two wrappers:
- `govuk-width-container`: Constrains maximum content width and sets responsive margins.
- `govuk-main-wrapper`: Applies vertical padding to the `<main>` element.

### Content Column Rules

- Standard body content (headings, paragraphs, forms, lists) must use `govuk-grid-column-two-thirds` to prevent eye strain.
- Dashboard tables, card grids, or wide data sets may use `govuk-grid-column-full`.

---

## 6. Navigation

- **Header**: Use standard `govuk-header` with service name "Hippo Digital Service".
- **Service Navigation**: Use `govuk-service-navigation` for navigation across sections.
- **Breadcrumbs**: Place inside `govuk-width-container` before `govuk-main-wrapper`. Do not include current page in breadcrumb list.
- **Back Link**: Use `govuk-back-link` on transactional form pages. Do not combine back links with breadcrumbs on the same page.

---

## 7. Form Design & Component Behaviors

- **Error Summary**: All validation errors must render in a `govuk-error-summary` at the top of the form, linked to corresponding input fields (see [DD-0001](decisions/DD-0001-gds-error-summary-strategy.md)).
- **Input Labels**: Every input must have a distinct `<label>` using `govuk-label` linked by `for` and `id`.
- **Buttons**:
  - Primary call to action: `govuk-button` (one per screen).
  - Start journey: `govuk-button govuk-button--start`.
  - Secondary action: `govuk-button govuk-button--secondary`.
  - Irreversible action: `govuk-button govuk-button--warning`.

---

## 8. Content & Copy Standards

- **Tone of Voice**: Clear, direct, plain English, active voice.
- **Terminology**: Use "sign in" (not "log on"), "application" (not "submission transaction"), "check" (not "verify").
- **Numbers**: Spell out one through nine; use numerals for 10 and above.
- **Dates**: Format as "12 October 2026" (day, full month name, four-digit year).

---

## 9. Accessibility (a11y)

- **Standard**: WCAG 2.2 Level AA compliance is mandatory.
- **Contrast Ratios**: Minimum 4.5:1 for body text; minimum 3:1 for large headings and UI components.
- **Focus Indicators**: Standard yellow highlight with black outline (`#ffdd00` / `#0b0c0c`). Never set `outline: none`.
- **Keyboard Operability**: All actions must be accessible using Tab, Enter, and Spacebar keys.
- **Screen Reader Support**: Use semantic HTML elements. Use ARIA attributes only when standard HTML elements cannot provide semantic meaning.

---

## 10. Design Decisions & Assumptions

- **Design Decisions**:
  - [DD-0001](decisions/DD-0001-gds-error-summary-strategy.md): Standardize Form Validation with GDS Error Summary
- **Assumptions**:
  - [ASSUME-0001](assumptions/ASSUME-0001-browser-based-access.md): Users access the service through modern web browsers on mobile and desktop devices.
