---
name: risk-assessor
description: Scores a product initiative across 8 risk dimensions (Idea Origin, Market, Effort, Rollback, Data, Financial/Legal/Reputation, Clinical, Customer Change) to produce an overall risk level. Clinical Risk is a veto dimension. Trigger on: 'is this risky?', 'what could go wrong?', 'I'm worried about the clinical impact', 'this touches care records', 'could this affect compliance?', 'how hard would it be to roll back?', 'is this a big change for customers?', 'could we get in trouble if this goes wrong?', 'rate the risk', 'clinical risk', 'risk assessment', 'rollback'. Don't wait for someone to explicitly ask for a risk score — if they're describing a feature and risk is relevant, run this.
---

# Risk Assessor

Produces a risk score across 8 dimensions for any product initiative. Each dimension is rated Low / Medium / High. The overall risk level is the highest score across dimensions (not an average), with clinical risk acting as a veto.

## Inputs

- Initiative name and one-paragraph description
- Idea origin (who raised it and why)
- Any known concerns or constraints

## Risk Dimensions

Quick reference:

| # | Dimension | Low | High |
|---|-----------|-----|------|
| 1 | Idea Origin | Validated user need or data-driven | Internal/exec idea with no user evidence |
| 2 | Market Risk | Established use case; market pull exists | New segment or unproven demand |
| 3 | Effort | Small, bounded; 1–2 sprints | Large scope; quarter+; architecture unknowns |
| 4 | Rollback Risk | Feature-flagged; easily reversible | Hard to undo; data migration or contractual |
| 5 | Data Risk | No sensitive data | Personal/health data (GDPR Art. 9) |
| 6 | Financial/Legal/Reputation | Minimal exposure | Significant financial, legal, or brand risk |
| 7 | Clinical Risk | No direct patient care impact | Directly affects care delivery, records, or medication |
| 8 | Customer Change | Minor workflow change | Major process change; high training burden |

## Scoring Rules

1. Rate each dimension Low / Medium / High.
2. **Clinical Risk is a veto dimension.** If Clinical Risk = High, overall risk = High regardless of all other scores.
3. Overall risk = highest score across all 8 dimensions.
4. Flag every dimension rated High — these drive the discovery approach and must be addressed before committing to build.

## Output: Risk Score

```markdown
## Risk Assessment: [Initiative Name]

| Dimension | Score | Notes |
|-----------|-------|-------|
| Idea Origin | [L/M/H] | [brief rationale] |
| Market Risk | [L/M/H] | |
| Effort | [L/M/H] | |
| Rollback Risk | [L/M/H] | |
| Data Risk | [L/M/H] | |
| Financial/Legal/Reputation | [L/M/H] | |
| Clinical Risk | [L/M/H] | |
| Customer Change | [L/M/H] | |

**Overall risk: [Low / Medium / High]**
**Key drivers:** [The 1–3 dimensions most driving the score]
```
