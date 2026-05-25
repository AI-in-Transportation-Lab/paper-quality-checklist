# Causal Inference Checklist

Use when the paper claims that X causes Y, estimates a treatment effect, evaluates a policy, or recommends a countermeasure.

---

## 1. When Causal Language Is Warranted

| Design | Supports causation? | Condition |
|---|---|---|
| RCT / Randomized experiment | Yes | Valid randomization, no spillover, no attrition |
| Natural experiment (IV, RDD, DiD) | Conditionally | Identification assumptions must hold and be defended |
| Matching / IPW / DML | Conditionally | No unmeasured confounders (NUC) — untestable |
| Cross-sectional regression | No — association only | Can support causation only with strong prior theory |
| Before/after without control group | No | Cannot separate treatment from time trends |

- [ ] The causal estimand is named: ATE, ATT, LATE, or local effect at a threshold.
- [ ] The identification assumption is stated explicitly in the paper.
- [ ] Causal language (*causes*, *effect*, *impact*, *reduces*) is used **only** where the design supports it.
- [ ] Association language (*associated with*, *predicts*, *correlates*) is used elsewhere.

---

## 2. Directed Acyclic Graph (DAG)

Draw and report the DAG **before** choosing the adjustment set.

- [ ] All assumed causal paths ($X \to Y$) are shown.
- [ ] Known confounders are included as nodes with arrows into both $X$ and $Y$.
- [ ] Mediators are distinguished from confounders — do not condition on a mediator for the total effect.
- [ ] Colliders identified and **not conditioned on** (conditioning on a collider opens a non-causal path).
- [ ] The minimal sufficient adjustment set is identified via the backdoor criterion.
- [ ] The DAG is included in the paper or supplement.

**Backdoor criterion:** A set $Z$ satisfies the backdoor criterion relative to $(X, Y)$ if (1) no node in $Z$ is a descendant of $X$, and (2) $Z$ blocks every path with an arrow into $X$.

---

## 3. Method-Specific Checklists

### 3.1 Difference-in-Differences (DiD)

$$Y_{it} = \alpha_i + \lambda_t + \tau (\text{Treat}_i \times \text{Post}_t) + \varepsilon_{it}$$

$$H_0: \tau = 0$$

- [ ] Parallel pre-treatment trends verified: event-study plot + regression with pre-period × treatment interactions (all coefficients should be near zero and jointly insignificant).
- [ ] No anticipation: treatment was not anticipated before the event window.
- [ ] SUTVA: no spillover between treated and control units; no contamination.
- [ ] Standard errors clustered at the **treatment assignment level** (not observation level).
- [ ] **Staggered adoption:** if units adopt treatment at different times, use Callaway-Sant'Anna (2021) or Sun-Abraham (2021) — plain two-way FE DiD produces biased estimates with heterogeneous effects.
- [ ] Robustness: placebo treatment dates, alternative control groups, Goodman-Bacon decomposition.

### 3.2 Instrumental Variables (IV)

Three conditions for instrument $Z$ (all must hold):

1. **Relevance:** $\text{Cov}(Z, X) \neq 0$ — testable; first-stage F-statistic must exceed 10 (prefer > 16 by Stock-Yogo).
2. **Exclusion:** $Z$ affects $Y$ only through $X$ — **untestable; justify on theory or design.**
3. **Independence (exogeneity):** $Z \perp U$ (no unmeasured confounders of $Z$ and $Y$) — justify on design.

$$\hat{\beta}_{IV} = \frac{\text{Cov}(Z, Y)}{\text{Cov}(Z, X)}$$

- [ ] First-stage F-statistic reported; weak instruments ($F < 10$) acknowledged with appropriate SE correction (Anderson-Rubin CI).
- [ ] Exclusion restriction justified with theoretical argument.
- [ ] LATE interpretation stated: IV identifies the effect for **compliers only**, not the full population.
- [ ] With multiple instruments: Sargan-Hansen J-test for overidentification reported.
- [ ] Sensitivity to partial exclusion violation reported (Conley et al. plausibly exogenous bounds).

### 3.3 Regression Discontinuity (RDD)

$$\hat{\tau}_{RDD} = \lim_{x \to c^+} \mathbb{E}[Y \mid X=x] - \lim_{x \to c^-} \mathbb{E}[Y \mid X=x]$$

- [ ] Discontinuity in the running variable at threshold $c$ is exogenous by design.
- [ ] **Manipulation test:** McCrary density test (or Cattaneo rddensity) — no heaping or bunching at $c$.
- [ ] Bandwidth selected by MSE-optimal CCT method (Calonico-Cattaneo-Titiunik).
- [ ] Polynomial order is low — **linear preferred**; cubic rarely justified.
- [ ] Robustness: alternative bandwidths, donut holes around threshold, placebo cutoffs.
- [ ] Pre-treatment covariate balance at $c$ tested.
- [ ] Effect is **local to the threshold**; generalization to other values of the running variable requires justification.

### 3.4 Synthetic Control

$$\hat{Y}_{1t}^{(0)} = \sum_{j=2}^{J+1} w_j^* Y_{jt}, \quad w_j^* \geq 0, \quad \sum w_j^* = 1$$

- [ ] Pre-treatment fit between treated unit and synthetic control is visually close (plot required).
- [ ] Donor pool is justified: no treated units included; units are plausibly similar to treated unit.
- [ ] Inference via placebo permutation: synthetic control run for each donor unit; effect compared to permutation distribution.
- [ ] Generalization beyond the single treated unit is **not claimed**.

### 3.5 Matching and Inverse Probability Weighting (IPW)

$$e(X) = P(D=1 \mid X) \quad \text{(propensity score)}$$

$$\hat{\tau}_{IPW} = \frac{1}{n}\sum_i \left[\frac{D_i Y_i}{e(X_i)} - \frac{(1-D_i)Y_i}{1-e(X_i)}\right]$$

- [ ] Covariate balance before and after matching/weighting shown (SMD table; SMD < 0.1 per covariate as target).
- [ ] Overlap (common support) checked: propensity score histogram by treatment group; trimming rule stated.
- [ ] **Doubly robust estimator** (AIPW or TMLE) used when possible — consistent if either the propensity or outcome model is correct.
- [ ] NUC assumption stated as a limitation.
- [ ] Sensitivity analysis: Rosenbaum bounds ($\Gamma$) or E-value.

---

## 4. Sensitivity Analysis (Required)

| Method | Purpose | Use for |
|---|---|---|
| Rosenbaum bounds $\Gamma$ | How much hidden bias would overturn the result | Matching studies |
| E-value | Minimum confounding association to explain away the observed effect | Observational regression |
| Placebo tests (fake outcome or treatment date) | Should show no effect under the null | DiD, IV, RDD |
| Bandwidth variation | Stability of RD estimate | RDD |
| Leave-one-out | Robustness to a single influential unit | Synthetic control, DiD |
| Partial exclusion bounds | Range of IV estimates under mild exclusion violation | IV |

- [ ] At least one sensitivity analysis is reported for every causal claim.
- [ ] E-value: $EV = RR + \sqrt{RR \cdot (RR-1)}$ where $RR$ is the observed risk ratio.
- [ ] Placebo test results are displayed (not just stated).

---

## 5. Causal Pitfalls

- [ ] **Omitted variable bias:** not controlling for a confounder on the backdoor path.
- [ ] **Controlling for a mediator:** blocks the causal path; reports direct effect unintentionally.
- [ ] **Collider bias:** conditioning on a common effect of $X$ and $Y$ (or their causes).
- [ ] **Reverse causality:** especially in cross-sectional data; address with theory or lagged instruments.
- [ ] **SUTVA violation:** treated and control units interact (spillover); address with buffer zones or network models.
- [ ] **Over-controlling with fixed effects:** high-dimensional FE can absorb treatment variation, yielding imprecise estimates.
- [ ] **LATE misapplied:** IV estimates are local to compliers — do not extrapolate to non-compliers or the full population.
- [ ] **No sensitivity analysis:** all causal claims require at least one formal sensitivity analysis.
- [ ] **Regression-to-the-mean in crash studies:** treated sites selected because of high crash counts; use EB method or comparison group.
