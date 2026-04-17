# Release Documents in Software Delivery (Simplified)

## Overview

In real enterprise projects, release documentation is usually **minimal and practical**, not overly fragmented.

Instead of multiple separate documents, teams typically use:

- 1 high-level planning document
- 1 execution document per release
- (optional) 1 communication document

---

## 1. Release Plan (High-Level)

### Timing
- Before development starts
- Continuously updated

### Purpose
- Define product roadmap and planned releases

### Owner
- Product Owner (PO)
- Tech Lead

### Reader
- Stakeholders
- Dev Team
- QA

### Approver
- Product Owner
- Project Manager

### Output
- `release-plan.md`

---

## 2. Release Execution Document ⭐ Core

### Timing
- 1–3 days before release

### Purpose
- Single source of truth for release execution
- Combines scope, risks, dependencies, deployment, and rollback

### Owner
- Tech Lead
- Senior Developer

### Reader
- DevOps
- QA
- Developers

### Approver
- Tech Lead
- Project Manager (optional)

### Output
- `release-{version}.md`

---

### Recommended Structure

# Release vX.X

## 1. Scope
- Feature A
- Feature B

## 2. Dependencies
- External API ready
- Product config ready

## 3. Risks
- API instability
- Performance under load

## 4. Execution Plan
- Deploy backend
- Deploy frontend
- Run DB migration
- Smoke testing

## 5. Deployment Steps
- docker pull xxx
- kubectl apply xxx

## 6. Rollback Plan
- Rollback to previous image
- Restore DB backup if needed

## 7. Checklist
- [ ] Services healthy
- [ ] API test passed
- [ ] Monitoring normal

---

## 3. Release Notes (Optional but Common)

### Timing
- During / after release

### Purpose
- Communicate changes to users or stakeholders

### Owner
- Product Owner
- QA

### Reader
- Stakeholders
- Users
- Support Team

### Approver
- Product Owner

### Output
- `release-notes.md`

---

## Final Structure

### Minimum Required

- `release-plan.md`
- `release-{version}.md`

### Optional

- `release-notes.md`

---

## Key Takeaway

- Avoid over-documentation
- Merge related content into one execution document
- Focus on:
  - clarity
  - execution safety
  - rollback capability

> Good release documentation is not about quantity, but about enabling safe and predictable delivery.
