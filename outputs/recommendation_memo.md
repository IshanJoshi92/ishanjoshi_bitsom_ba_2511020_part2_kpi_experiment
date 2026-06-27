# Recommendation Memo — New Onboarding & Activation Campaign

## 1. Executive summary
The new onboarding/activation campaign (Treatment) **more than doubled paid conversion** versus the existing experience (3.19% → 7.04%, +120.9% relative, p = 0.0011). The full funnel and engagement improved in step. However, two guardrails moved against us: support-ticket rate nearly doubled and revenue per converted user roughly halved. **Recommendation: Launch to all users — conditional on scaling support capacity and monitoring revenue quality and the West region.** The conversion gain is large, significant, and ARPU is still slightly positive; the guardrail risks are real but manageable, not disqualifying.

## 2. North Star metric
**Paid conversion rate.** It is the business outcome the campaign targets and the metric closest to revenue. Funnel step-rates, engagement, and ARPU are supporting metrics; refunds, support load, revenue quality, and segment decline are guardrails.

## 3. KPI tree explanation
Paid conversion decomposes into three primary drivers — Landing Page Visit Rate, Trial Start Rate, and Onboarding Completion Rate — each with two sub-drivers (see `outputs/kpi_tree.png`). Five guardrails sit beneath the tree to catch harm that a conversion gain could mask.

## 4. Experiment result summary
| Metric | Control | Treatment | Change |
|---|---|---|---|
| Paid conversion rate | 3.19% | 7.04% | +120.9% |
| Landing visit rate | 63.6% | 72.4% | +8.8 pp |
| Trial start rate | 25.1% | 29.0% | +3.9 pp |
| Onboarding completion | 15.7% | 21.1% | +5.5 pp |
| ARPU | 51.97 | 54.25 | +4.4% |
| Avg engagement | 57.0 | 62.9 | +5.9 |
| Avg days to convert | 8.9 | 6.4 | faster |

## 5. Hypothesis test interpretation
Two-proportion z-test on paid conversion: Z = 3.264, two-tailed p = 0.0011 < 0.05 → reject H0. The conversion improvement is statistically significant and corroborated by the supporting funnel metrics. (Full notes: `analysis/hypothesis_test_notes.md`.)

## 6. Guardrail analysis
| Guardrail | Control | Treatment | Risk |
|---|---|---|---|
| Refund rate (overall) | 0.0% | 0.42% | Low — stays under 1% |
| Refund rate among converted | 0.0% | 6.0% | Watch — new converts include some refunders |
| Support ticket rate | 14.8% | 24.8% | **High — staffing/cost impact** |
| Support tickets per user | 0.22 | 0.37 | High — more load per user |
| ARPCU (revenue/converted) | 1,630 | 770 | **Medium — lower-value conversions** |
| Days to convert | 8.9 | 6.4 | Positive — faster activation |

The campaign converts **more** users but **lower-value** ones, and they generate **more support load**. ARPU is still up only because volume offsets the lower per-head value.

## 7. Segment-level insight
Conversion improves in **every** region, so no segment is harmed. The lift is weakest in **West** (3.38% → 5.08%, ~+50%) versus North/East/South (~+135–155%). No "do-not-launch" segment exists, but West warrants closer monitoring and possibly campaign tuning.

## 8. Final recommendation
**Launch to all users**, conditional on:
1. **Scale support capacity** ahead of rollout (ticket volume ≈ doubles).
2. **Monitor revenue quality** (ARPCU, refund-among-converted) for 30–60 days; investigate whether new converts retain.
3. **Track West region** separately; tune if its lift stays low.

Rejecting the launch would forgo a large, significant conversion gain with positive ARPU and faster activation. The guardrail issues are operational risks to mitigate, not reasons to withhold.

## 9. Risks and limitations
- 30-day window only — no view of retention/LTV; ARPCU decline could matter more over time.
- Support-load increase may erode margin if not staffed.
- 8 duplicate rows removed; engagement_score missing for 14 users (excluded from averages, not imputed); 3 revenue outliers kept as genuine.
- Observational segment cuts are directional, not separately powered tests.

## 10. Next steps
1. Staff support for the higher ticket volume before launch.
2. Instrument a 60–90 day retention/LTV follow-up on Treatment converts.
3. Run a focused iteration for the West region.
4. Re-evaluate ARPCU after the retention window before declaring full success.
