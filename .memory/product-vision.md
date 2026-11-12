# 🧭 Product Vision Document

## 1. Product Overview

**Product Name:**  
Hippo Digital Service (`hippo-agents-test5`)

**Author / Owner:**  
Project Lead and Technical Architecture Team

---

## 2. Vision Statement

Provide a reliable, accessible, and secure digital service that lets users manage accounts and submit applications with clarity and confidence.

---

## 3. Problem Statement

Manual application procedures and non-standard web interfaces cause delays, input errors, and high operational costs.

- **Who experiences the problem?** Citizens, business operators, and administrative staff.
- **What is the impact of the problem today?** Users submit incomplete forms. Support agents spend excessive time on manual reviews. Users experience long turnaround times.
- **Why does solving this matter?** A standardized digital service decreases submission errors, accelerates processing, and complies with government accessibility mandates.

---

## 4. Target Users / Audiences

| Persona | Description | Key Needs / Goals |
|---|---|---|
| Applicant | Public user submitting account requests or service applications | Needs clear guidance, simple steps, save-and-return capability, and fast feedback |
| Case Officer | Internal administrator reviewing and verifying submissions | Needs clear summary views, structured data, audit logs, and approval actions |
| Service Manager | Operational owner monitoring service health and volumes | Needs completion analytics, operational metrics, and error rates |

---

## 5. Product Goals & Outcomes

| Goal | Metric / KPI | Desired Outcome |
|---|---|---|
| Increase digital adoption | Digital submission rate | More than 85% of all applications completed through the digital service |
| Decrease submission errors | First-time validation pass rate | More than 90% of forms submitted without validation failures |
| Ensure full accessibility | WCAG 2.2 Level AA compliance | Zero outstanding accessibility non-conformance defects |
| Reduce turnaround duration | Average processing time | Application decision latency decreased by 50% |

---

## 6. Key Features / Capabilities

- **User Authentication**: Secure sign-in and session management.
- **Guided Form Journeys**: Step-by-step application workflow with inline validation following GDS patterns.
- **Save and Return**: Ability to store draft progress and resume safely.
- **Admin Review Dashboard**: Structured views for staff to inspect, approve, or reject applications.
- **Audit Logging**: Comprehensive traceability for application status transitions.
- **Automated Notifications**: Status updates sent to applicants upon milestone events.

---

## 7. Value Proposition

| For (user type) | Who want to (need) | Our product (solution) | Unlike (alternative) |
|---|---|---|---|
| Applicants | Submit applications quickly without errors | A responsive GDS-compliant digital service | Slow paper forms or confusing legacy portals |
| Case Officers | Process and review submissions efficiently | A structured dashboard with automated validation | Disjointed spreadsheets and manual email trails |
| Service Leadership | Maintain high compliance and security standards | A robust, auditable modern .NET web service | Fragile legacy platforms with high maintenance costs |

---

## 8. Constraints / Assumptions

- **Constraints**:
  - The frontend must comply with WCAG 2.2 Level AA accessibility standards.
  - The service must follow Government Design System (GDS) patterns and guidelines.
  - The backend runtime must use modern supported .NET LTS releases (.NET 8).
  - All sensitive user data must be encrypted at rest and in transit.
- **Assumptions**:
  - [ASSUME-0001](assumptions/ASSUME-0001-browser-based-access.md): Users access the service through modern web browsers on mobile and desktop devices.
  - [ASSUME-0002](assumptions/ASSUME-0002-external-identity-provider.md): User authentication delegates to an external OIDC-compliant identity provider.

---

## 9. Success Metrics

- **Primary metric(s)**:
  - 85% end-to-end digital completion rate.
  - 90% first-time submission accuracy.
- **Secondary metric(s)**:
  - System availability equal to or greater than 99.9%.
  - Page load response time under 1.0 second on standard broadband and 4G connections.
- **Qualitative indicators**:
  - User satisfaction score above 80% on post-submission feedback surveys.
  - Clean audit sign-off by security and accessibility assessors.

---

## 10. Stakeholders

| Role | Name / Team | Interest / Contribution |
|---|---|---|
| Product Manager | Product Team | Service vision, roadmap priorities, and stakeholder alignment |
| Technical Architect | Architecture Team | System design, technical standards, security, and scalability |
| Lead Developer | Engineering Team | Implementation, unit and integration test quality, CI/CD pipeline |
| Interaction Designer / Content Designer | Design Team | User journey flows, GDS component adherence, plain English copy |
| Quality Assurance Lead | Test Team | Test automation strategy, performance validation, accessibility auditing |

---

## 11. Risks & Open Questions

- **Risks**:
  - Delays in external identity provider integration may block early end-to-end testing.
  - Incomplete user research during initial development may require form flow revisions.
- **Open Questions**:
  - Which specific OIDC identity provider will serve production environments?
  - What are the peak concurrent submission volumes expected during peak operational periods?

---

## 12. References

- [GOV.UK Design System Documentation](https://design-system.service.gov.uk)
- [WCAG 2.2 Level AA Guidelines](https://www.w3.org/WAI/standards-guidelines/wcag/)
- [ASSUME-0001: Browser-based access](assumptions/ASSUME-0001-browser-based-access.md)
- [ASSUME-0002: External OIDC identity provider](assumptions/ASSUME-0002-external-identity-provider.md)

## 13. Value Rule Set

> _The criteria or rules used to evaluate whether features should proceed to development._

- **Primary Value Driver(s)**: Operational reliability, user adoption, and strict compliance.
- **Strategic Goals Alignment**: Aligns with ensuring secure, reliable, and accessible public services.

| Rule / Criterion | Description | Minimum Threshold for Go |
|------------------|-------------|--------------------------|
| Operational Reliability | Impact on system observability and testing | Enhances monitoring or provides technical validation |
| User Value | Impact on user completion rates or satisfaction | No degradation to user experience |
| Compliance | Adherence to GDS, WCAG 2.2, and security | 100% compliance |
