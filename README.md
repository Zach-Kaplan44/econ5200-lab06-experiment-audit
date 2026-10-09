# econ5200-lab06-experiment-audit
## Experiment Design Audit: Power, Selection & Weighting

### Objective
I audited an A/B test for statistical power and corrected selection bias in an observational comparison using inverse probability weighting.

### Methodology
- Checked the power of an A/B test that gave 2% of traffic (1,000 users) to treatment, for detecting a 0.8pp lift.
- Calculated the sample size needed per group to reach 80% power.
- Wrote my own `power_check` function and validated it against statsmodels.
- Used `power_check` to see what power the same 50,000 users would have had if split evenly between two groups.
- Compared the naive treatment-vs-control estimate in a wellness-program dataset against the known true effect to diagnose selection bias.
- Applied inverse probability weighting to adjust for the bias.

### Key Findings
- **The A/B test was underpowered.** With 1,000 treatment users, it had 19.8% power to detect a 0.8pp lift. Reaching 80% power would have taken 12,514 users per group.
- **The same traffic would have been enough.** An even split of the 50,000 users would have given 97.7% power.
- **The naive estimate was badly off.** The wellness-program comparison showed -$1,396 against a true effect of -$500, a sign of selection bias.
- **Weighting moved the estimate.** Inverse probability weighting brought it to $-522.
