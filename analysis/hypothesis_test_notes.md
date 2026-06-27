# Hypothesis Test Notes — Onboarding & Activation Campaign

## Test design (Task 6)

| Element | Specification |
|---|---|
| **Metric tested** | Paid conversion rate (`converted_to_paid` / users) — the North Star |
| **Reason for this metric** | It is the bottom-of-funnel business outcome the campaign is meant to move and the metric tied directly to revenue and the launch decision. Funnel and engagement metrics are supporting, not decisive. |
| **Null hypothesis (H0)** | p(Treatment) = p(Control) — the new campaign has no effect on paid conversion. |
| **Alternate hypothesis (H1)** | p(Treatment) ≠ p(Control) — the new campaign changes paid conversion. |
| **Tail** | Two-tailed (we test for a difference in either direction; the standard, more conservative default for an A/B decision). |
| **Significance level (α)** | 0.05 |
| **Test** | Two-proportion z-test (two independent groups, binary outcome). |
| **Interpretation logic** | If p-value < 0.05 → reject H0 and conclude the difference is statistically significant. If p ≥ 0.05 → fail to reject H0 (no significant effect). |

## Test result (Task 7)

**Inputs**

| | Control | Treatment |
|---|---|---|
| Users (n) | 690 | 710 |
| Conversions (x) | 22 | 50 |
| Conversion rate (p) | 3.19% | 7.04% |

**Output**

- Absolute uplift: **+3.85 percentage points**
- Relative uplift: **+120.9%**
- Pooled proportion: 0.0514, standard error: 0.01181
- **Z = 3.264**, **two-tailed p = 0.0011**
- **Decision: p (0.0011) < 0.05 → reject H0.** The difference is statistically significant.

## Business interpretation

The Treatment (new onboarding/activation campaign) more than doubles paid conversion versus the existing experience, and the result is highly unlikely to be due to chance (≈1 in 900). The supporting funnel metrics (landing visit, trial start, onboarding completion) and engagement score all move in the same direction, which strengthens confidence that the effect is real and driven by the campaign rather than noise.

**Caveat connected to the decision:** a significant conversion lift is necessary but not sufficient. The recommendation must also clear the guardrails — support-ticket rate and revenue-per-converted-user in particular (see `outputs/experiment_summary.xlsx` → guardrails). The hypothesis test answers "did conversion improve?"; the guardrail evaluation answers "is that improvement safe to ship?".

---
*This is a sensitive business decision; the test supports the conversion claim only. Final launch judgement is in `outputs/recommendation_memo.md`.*
