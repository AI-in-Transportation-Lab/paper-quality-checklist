# Statistical Test Checklist

Use before submitting any paper with statistical tests, regressions, crash models, simulations, or ML experiments.

---

## 1. Formulate Before Testing

Write $H_0$ and $H_1$ before running any test. State the estimand explicitly.

$$H_0: \theta = \theta_0 \qquad H_1: \theta \neq \theta_0 \text{ (two-tailed) or } H_1: \theta > \theta_0 \text{ (one-tailed — justify)}$$

- [ ] Each $H_0$ names the estimand: mean, proportion, rate ratio, OR, AUC, RMSE, $\Delta$F1, …
- [ ] Exploratory analyses are reported as exploratory, not confirmatory.
- [ ] The full family of planned hypotheses is declared before testing (for multiple-comparison correction).
- [ ] One-tailed tests are pre-registered or mechanistically justified, not chosen after seeing results.

---

## 2. Study Design First

- [ ] Define the outcome type: continuous, binary, count, ordinal, nominal, time-to-event, spatial/network, ranking, or text/image-derived metric.
- [ ] Define predictors: treatment/control, groups, continuous covariates, repeated measures, panel/time series, spatial units, or model variants.
- [ ] Identify the unit of analysis: crash, person, vehicle, trip, segment, intersection, image, frame, video, model run, seed, city, or paper.
- [ ] State the independence level: independent observations, clustered sites, repeated subjects, repeated routes, repeated models, or time periods.
- [ ] State the estimand: mean difference, proportion difference, odds ratio, rate ratio, risk difference, marginal effect, prediction metric difference, correlation, or causal effect.
- [ ] Separate exploratory analysis from confirmatory hypothesis testing.
- [ ] Write the null and alternative hypothesis before choosing the test.

## 3. Test and Model Decision Matrix

| Outcome | Design | Default test / model | Key check |
|---|---|---|---|
| Continuous | Two independent groups | Welch t-test | Levene; unequal variance by default |
| Continuous | Two paired measurements | Paired t-test | Normality of differences $d_i$ |
| Continuous | 3+ independent groups | Welch ANOVA | Levene; residual normality |
| Continuous | 3+ repeated / within | RM-ANOVA, mixed model, or Friedman | Within-unit dependence |
| Continuous | With covariates | Linear regression | Residuals, VIF, heteroskedasticity |
| Continuous | Panel / clustered sites | FE, RE, mixed model, or cluster-robust SE | Estimand; Hausman test |
| Count | No exposure | Poisson → NB if $\hat{\phi} > 1.5$ | Overdispersion; zero inflation |
| Count | With exposure | Poisson/NB with $\log(t)$ offset | Correct denominator (VMT, AADT, hrs) |
| Binary | Cross-sectional | Logistic regression | Separation; calibration; OR ≠ RR |
| Ordinal severity | Cross-sectional | Ordinal logistic (PO model) | Brant test for PO assumption |
| Nominal multiclass | Cross-sectional | Multinomial logistic | Class imbalance; reference category |
| Time-to-event | Survival | KM + Cox PH | Schoenfeld residuals for PH |
| Spatial | Any | Spatial lag / error model or spatial-robust SE | Moran's I on residuals |
| Before/after | Quasi-experiment | DiD or ITS | Parallel trends; staggered adoption |
| Categorical × categorical | Cross-tab | $\chi^2$ (Fisher if $E_{ij} < 5$) | Cell sizes; Cramér's V |
| Two ML models | Same test set | McNemar / DeLong / 5×2CV t-test | Paired dependence; multiple metrics |
| Two forecasts | Time series | Diebold-Mariano | Loss function choice |
| Many tests | Exploratory family | Holm (always) or BH-FDR | Declare family before testing |

---

## 4. Formulas and Hypothesis Templates

### 4.1 Means — Welch Two-Sample t-Test

$$H_0: \mu_1 = \mu_2 \qquad H_1: \mu_1 \neq \mu_2$$

$$t = \frac{\bar{X}_1 - \bar{X}_2}{\sqrt{s_1^2/n_1 + s_2^2/n_2}}, \qquad \nu \approx \frac{(s_1^2/n_1 + s_2^2/n_2)^2}{\frac{(s_1^2/n_1)^2}{n_1-1} + \frac{(s_2^2/n_2)^2}{n_2-1}}$$

**Effect size — Cohen's d:**

$$d = \frac{\bar{X}_1 - \bar{X}_2}{s_{\text{pooled}}}, \quad s_{\text{pooled}} = \sqrt{\frac{(n_1-1)s_1^2 + (n_2-1)s_2^2}{n_1+n_2-2}}$$

Benchmarks: $|d| = 0.2$ small, $0.5$ medium, $0.8$ large.

- [ ] Welch by default; Student's t only when $n_1 = n_2$ and equal variance verified by Levene ($p > 0.05$).
- [ ] Reported: $t(\nu)$, $p$, 95% CI on difference, Cohen's $d$.

### 4.2 More Than Two Groups — ANOVA

$$H_0: \mu_1 = \mu_2 = \cdots = \mu_k \qquad H_1: \text{at least one } \mu_i \neq \mu_j$$

$$F = \frac{SS_B/(k-1)}{SS_W/(N-k)} = \frac{MS_B}{MS_W}, \qquad \eta^2 = \frac{SS_B}{SS_T}$$

$\eta^2$ benchmarks: $0.01$ small, $0.06$ medium, $0.14$ large.

- [ ] Used Welch ANOVA when Levene's $p < 0.05$.
- [ ] Significant omnibus $F$ → planned contrasts or Tukey HSD.
- [ ] Reported: $F(k-1,\, N-k)$, $p$, $\eta^2$ or $\omega^2$.

Non-parametric fallback (non-normal, small $n$):

| Parametric | Non-parametric | Effect size |
|---|---|---|
| Welch t | Mann-Whitney U | $r = Z/\sqrt{n}$ |
| Paired t | Wilcoxon signed-rank | $r = Z/\sqrt{n}$ |
| One-way ANOVA | Kruskal-Wallis $H$ | $\eta^2_H = (H - k + 1)/(n - k)$ |
| RM-ANOVA | Friedman $\chi^2_r$ | Kendall's $W$ |

### 4.3 Chi-Square and Fisher Exact

$$H_0: \text{independence} \qquad \chi^2 = \sum_{i,j} \frac{(O_{ij} - E_{ij})^2}{E_{ij}}, \quad E_{ij} = \frac{R_i C_j}{N}$$

Use Fisher exact when any $E_{ij} < 5$.

**Effect size — Cramér's V:**

$$V = \sqrt{\frac{\chi^2}{n \cdot \min(r-1,\, c-1)}}$$

- [ ] Verified all $E_{ij} \geq 5$ before using $\chi^2$.
- [ ] Reported: $\chi^2(\text{df})$, $p$, Cramér's $V$.

### 4.4 Linear Regression

$$Y = \beta_0 + \beta_1 X_1 + \cdots + \beta_p X_p + \varepsilon, \quad \varepsilon \sim \mathcal{N}(0, \sigma^2)$$

- [ ] Residuals vs fitted plot and Q-Q plot inspected.
- [ ] Breusch-Pagan test for heteroskedasticity; use HC3 robust SE if violated.
- [ ] VIF $< 5$ (at minimum $< 10$) for all predictors.
- [ ] Reported: $\hat{\beta}$, SE, $t$, $p$, 95% CI, $R^2$, adjusted $R^2$.

### 4.5 Logistic Regression (Binary Outcome)

$$\log\frac{P(Y=1)}{P(Y=0)} = \beta_0 + \sum_{j=1}^p \beta_j X_j$$

$$\text{OR}_j = e^{\beta_j}, \quad \text{95% CI} = \left(e^{\hat{\beta}_j - 1.96\,\text{SE}_j},\; e^{\hat{\beta}_j + 1.96\,\text{SE}_j}\right)$$

- [ ] Checked for complete separation (use Firth logistic regression if present).
- [ ] Calibration assessed: Hosmer-Lemeshow test or calibration plot.
- [ ] **OR ≠ RR when outcome prevalence > 10%**; convert with Zhang-Yu formula or report RR directly.
- [ ] Reported: OR (95% CI), $p$, McFadden pseudo-$R^2$, AUC.

### 4.6 Poisson and Negative Binomial (Count Outcome)

**Poisson with exposure offset:**

$$\log(\lambda_i) = \beta_0 + \sum_{j=1}^p \beta_j X_{ij} + \underbrace{\log(t_i)}_{\text{offset}}$$

Offset $t_i$ = VMT, $\text{AADT} \times L$, person-hours, or trips — **never include as a predictor**.

**Overdispersion check:**

$$\hat{\phi} = \frac{\chi^2_{\text{Pearson}}}{n - p} = \frac{\sum (y_i - \hat{\lambda}_i)^2 / \hat{\lambda}_i}{n - p}$$

If $\hat{\phi} > 1.5$ → use Negative Binomial.

**Negative Binomial:**

$$\text{Var}(Y_i) = \lambda_i(1 + \alpha\lambda_i), \quad \alpha > 0 \text{ (dispersion parameter)}$$

Zero-inflation: use Vuong test or rootogram. ZIP / ZINB if excess zeros confirmed.

- [ ] Reported: rate ratio $= e^{\hat{\beta}_j}$ (95% CI), $\hat{\phi}$ or $\hat{\alpha}$, AIC comparison vs Poisson, LR test.

### 4.7 Ordinal Logistic Regression

$$\log\frac{P(Y \leq k)}{P(Y > k)} = \alpha_k - \boldsymbol{\beta}^T \mathbf{x}, \quad k = 1, \ldots, K-1$$

- [ ] Tested proportional odds (PO) assumption: Brant test or score test.
- [ ] If PO violated: partial PO model (e.g., `VGAM::vglm`) or multinomial fallback.
- [ ] Reported: cumulative OR per $k$, Brant test result.

### 4.8 Cox Proportional Hazards

$$h(t \mid \mathbf{x}) = h_0(t)\, \exp(\boldsymbol{\beta}^T \mathbf{x})$$

$$H_0: \boldsymbol{\beta} = \mathbf{0} \qquad \text{(global LR test)}$$

- [ ] PH assumption tested: scaled Schoenfeld residual plots; $\rho$ and $p$ per covariate.
- [ ] Reported: HR $= e^{\hat{\beta}_j}$ (95% CI), concordance C-statistic.

### 4.9 Clustered and Panel Data — Mixed Effects

$$Y_{ij} = \beta_0 + \beta_1 X_{ij} + u_i + \varepsilon_{ij}, \quad u_i \sim \mathcal{N}(0, \sigma_u^2), \quad \varepsilon_{ij} \sim \mathcal{N}(0, \sigma_\varepsilon^2)$$

**Intraclass correlation:**

$$\text{ICC} = \frac{\sigma_u^2}{\sigma_u^2 + \sigma_\varepsilon^2}$$

ICC $> 0.05$ → clustering is non-trivial; model it or use cluster-robust SE.

- [ ] Fixed effects used for within-unit causal estimand; random effects for population-average.
- [ ] Hausman test reported when choosing between FE and RE.
- [ ] Reported: ICC, $\hat{\sigma}_u$, LR test vs pooled OLS.

### 4.10 Spatial Autocorrelation — Moran's I

$$I = \frac{N}{\sum_i \sum_j w_{ij}} \cdot \frac{\sum_i \sum_j w_{ij}(x_i - \bar{x})(x_j - \bar{x})}{\sum_i (x_i - \bar{x})^2}$$

$E[I] = -1/(N-1)$ under independence.

- [ ] Compute Moran's I on model residuals before claiming spatial independence.
- [ ] Significant Moran's I → spatial lag model, spatial error model, or spatial-cluster-robust SE.

### 4.11 Difference-in-Differences

$$Y_{it} = \alpha + \beta_1 \text{Treat}_i + \beta_2 \text{Post}_t + \tau(\text{Treat}_i \times \text{Post}_t) + \varepsilon_{it}$$

$$H_0: \tau = 0$$

- [ ] Parallel pre-treatment trends verified: event-study plot + pre-period interaction test.
- [ ] Standard errors clustered at the treatment assignment level.
- [ ] Staggered adoption: use Callaway-Sant'Anna (2021) or Sun-Abraham (2021) to avoid negative-weighting bias.

### 4.12 ML Model Comparison

**McNemar (two classifiers, same test set):**

$$H_0: p_{01} = p_{10} \qquad \chi^2 = \frac{(b - c)^2}{b + c}, \quad \text{df} = 1$$

$b$ = correct by model 1 only; $c$ = correct by model 2 only.

**5×2CV paired t-test (Dietterich 1998) — correct when sharing training data:**

$$t = \frac{p_1^{(1)}}{\sqrt{\hat{s}^2}}, \quad \hat{s}^2 = \sum_{i=1}^{5} \sum_{j=1}^{2} \left(p_i^{(j)} - \bar{p}_i\right)^2 / 5$$

**DeLong test — two correlated AUROCs:**

$H_0: \text{AUROC}_1 = \text{AUROC}_2$. Use `pROC::roc.test()` (R) or `scipy` equivalent.

**Diebold-Mariano — time-series forecasts:**

$$DM = \frac{\bar{d}}{\hat{\sigma}_d / \sqrt{T}} \overset{d}{\longrightarrow} \mathcal{N}(0,1), \quad d_t = L(e_{1t}) - L(e_{2t})$$

- [ ] Did not use an unpaired t-test on fold metrics when folds share training data.

---

## 5. Assumption Checklist

| Assumption | Diagnostic | Action if violated |
|---|---|---|
| Normality of residuals | Q-Q plot; Shapiro-Wilk ($n < 50$) | Bootstrap CI; nonparametric test |
| Homoscedasticity | Breusch-Pagan; residual vs fitted | HC3 robust SE; WLS |
| Independence | Design review; Durbin-Watson | Cluster SE; mixed model |
| No multicollinearity | VIF; condition number | Drop/combine; ridge |
| Proportional odds | Brant test | Partial PO model; multinomial |
| PH in Cox | Schoenfeld residuals | Time-varying coefficients |
| No overdispersion | $\hat{\phi} = \chi^2_P / (n-p)$ | NB regression; quasi-Poisson |
| No zero inflation | Vuong test; rootogram | ZIP / ZINB |
| Spatial independence | Moran's I on residuals | SAR/SEM; spatial SE |
| Parallel trends (DiD) | Pre-treatment event study | Synthetic control; matching |

---

## 6. Multiple Comparison Corrections

$$p_{\text{Bonferroni}} = \min(m \cdot p_{(i)},\; 1) \qquad p_{\text{Holm}} = \min((m - i + 1) \cdot p_{(i)},\; 1)$$

| Method | When to use |
|---|---|
| Holm | Default for any family of hypotheses; always more powerful than Bonferroni |
| Bonferroni | Simple strict bound; transparent for small families |
| Benjamini-Hochberg FDR | Large exploratory family ($> 10$ tests); discovery setting |
| Planned contrasts | Pre-specified hypotheses; no correction needed |

- [ ] The full family of tested hypotheses is declared before testing.
- [ ] BH-FDR is used only for exploratory discovery, not confirmatory claims.

---

## 7. Power and Sample Size

$$n = \frac{2\sigma^2 (z_{\alpha/2} + z_\beta)^2}{\delta^2} \quad \text{(two-sample t, equal } n, \text{ two-tailed)}$$

$z_{\alpha/2} = 1.96$ ($\alpha = 0.05$); $z_\beta = 0.84$ (80% power), $1.28$ (90% power).

- [ ] Power analysis is pre-study; effect size $\delta$ comes from prior literature or smallest practical effect.
- [ ] Post-hoc power is NOT reported for non-significant results — report CI width instead.
- [ ] Cluster-adjusted sample size used when observations are not independent (multiply $n$ by design effect $\text{DEFF} = 1 + (m-1)\text{ICC}$).

---

## 8. Reporting Standards

| Quantity | Minimum required |
|---|---|
| Test statistic | $t$, $F$, $\chi^2$, $Z$, $W$, $H$, $I$ with df |
| $p$-value | Exact (e.g., $p = 0.032$); use $p < 0.001$ only below that threshold |
| Effect size | $d$, $r$, $\eta^2$, OR, RR, $\Delta$AUC, $\Delta$RMSE, $\Delta$F1, or domain unit |
| Uncertainty | 95% CI or bootstrap CI |
| Sample size | Per group/condition; after exclusions |
| Software | Package name and version |

- [ ] Practical significance stated in domain units: crashes per 100M VMT, seconds of delay, kg CO₂/km, ms latency, etc.
- [ ] $p$-value without effect size is an incomplete result.

---

## 9. Transportation-Specific Pitfalls

- [ ] Crash count model includes exposure as an **offset**, not a predictor: $\log(\text{VMT})$, $\log(\text{AADT} \times L)$.
- [ ] Regression-to-the-mean addressed in before/after studies: use EB method or comparison group.
- [ ] Site, route, or time clustering is modeled — not just acknowledged.
- [ ] Severity outcome uses ordinal or multinomial model, not OLS on integer severity codes.
- [ ] Surrogate safety measures (TTC, PET, DRAC) have explicit threshold and source justification.
- [ ] Video or sensor-derived observations account for within-clip/segment correlation.
- [ ] Spatial leakage: nearby road segments, intersections, or detectors are not split across train/test.

## 10. ML-Specific Pitfalls

- [ ] No temporal or spatial leakage in splits: preprocessing fitted on train only.
- [ ] Hyperparameters tuned on validation set; test set touched exactly once.
- [ ] Results reported as mean ± std across ≥ 3 seeds, not best run.
- [ ] AUPRC (not just AUROC) reported for rare-event outcomes (crashes, incidents, anomalies).
- [ ] Comparison baselines use same feature set, preprocessing, and tuning budget.
- [ ] Compute budget and hardware reported for reproducibility.

---

## 11. Final Statistical Gate

- [ ] Every hypothesis has a matched test or model with stated $H_0$ and $H_1$.
- [ ] Every model has assumptions checked or explicitly relaxed with justification.
- [ ] Every result reports effect size, CI, and $p$-value together.
- [ ] Every $p$-value belongs to a declared hypothesis family (with correction if needed).
- [ ] Every ML comparison uses paired or resampling-aware inference.
- [ ] Every transportation safety result uses correct exposure, unit of analysis, and clustering.
- [ ] Every causal claim is backed by design, identification assumptions, and sensitivity checks.
