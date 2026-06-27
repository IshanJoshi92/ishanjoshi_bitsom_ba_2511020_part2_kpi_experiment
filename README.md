# Part 2 — KPI Framework, Business Experiment Analysis & Decision Recommendation

## 1. Business context
A subscription digital-product company tested a **new onboarding & activation campaign** (Treatment) against the existing experience (Control). Users were randomly split into the two groups. Leadership must decide whether to **launch, reject, continue testing, or launch only for selected segments**. This repo frames the decision, defines the success metric, analyzes the experiment, evaluates guardrails, and makes a data-backed recommendation.

## 2. Dataset description
`data/campaign_experiment_data.xlsx` — 1,408 raw users × 16 fields (sheet `experiment_data`; a `business_context` reference sheet is included). Fields cover group assignment, signup date, segments (region, device, traffic source, plan), the funnel flags (landing → trial → onboarding → paid), revenue, support tickets, refunds, days to convert, and engagement score. After cleaning: **1,400 users (Control 690 / Treatment 710)**.

## 3. North Star metric selected
**Paid conversion rate.** It is the campaign's target outcome and the metric closest to revenue. Supporting metrics: funnel step-rates, engagement, ARPU. Optimizing it blindly is risky, which is why guardrails are evaluated.

## 4. KPI tree summary
North Star (Paid Conversion Rate) → 3 primary drivers (Landing Visit Rate, Trial Start Rate, Onboarding Completion Rate), each with 2 sub-drivers, plus 5 guardrails (refund rate, support ticket rate, revenue quality, days to convert, segment-level decline). See `outputs/kpi_tree.png`.

## 5. Experiment analysis approach
Prepared the data in `analysis/experiment_analysis.xlsx`: removed 8 exact duplicate rows; filled missing `device_type` (18) and `traffic_source` (24) as "Unknown"; left missing `engagement_score` (14) blank (excluded from averages, not imputed); confirmed missing `days_to_convert` is by-design (non-converters); found 0 invalid binary values; flagged 3 revenue outliers but kept them as genuine high-value conversions; verified group balance and funnel integrity. Metrics, segment cuts, and the test are in `outputs/experiment_summary.xlsx`.

## 6. Hypothesis test summary
Two-proportion z-test on paid conversion: Control 3.19% vs Treatment 7.04%, **Z = 3.264, two-tailed p = 0.0011 < 0.05 → reject H0**. The lift (+120.9% relative) is statistically significant. Details in `analysis/hypothesis_test_notes.md`.

## 7. Guardrail metrics considered
Refund rate (0.0% → 0.42%; 6.0% among converted), support ticket rate (14.8% → 24.8%), support tickets per user (0.22 → 0.37), ARPCU (1,630 → 770), days to convert (8.9 → 6.4), engagement (57.0 → 62.9), and segment-level decline. The material risks are **higher support load** and **lower revenue per converted user**.

## 8. Final recommendation
**Launch to all users**, conditional on (1) scaling support capacity, (2) monitoring revenue quality and refund-among-converted for 30–60 days, and (3) tracking the weaker **West** region. Rationale and the full decision are in `outputs/recommendation_memo.md`.

## 9. Assumptions and limitations
30-day window (no retention/LTV view); two-tailed test at α = 0.05; engagement missings excluded not imputed; revenue outliers kept; segment cuts are directional not separately powered. ARPCU decline should be re-checked after a retention window.

## 10. Screenshots
In `screenshots/`: `summary_metrics.png` (Control vs Treatment table), `hypothesis_test_output.png` (z-test evidence), `kpi_tree_preview.png` (KPI tree).
