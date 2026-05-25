# Statistical Test Checklist

Use this page before submitting any paper with statistical tests, regressions, simulations, surveys, crash models, model comparisons, or ML experiments.

## Study Design First

- [ ] Define the outcome type: continuous, binary, count, ordinal, nominal, time-to-event, spatial/network, ranking, or text/image-derived metric.
- [ ] Define predictors: treatment/control, groups, continuous covariates, repeated measures, panel/time series, spatial units, or model variants.
- [ ] Identify the unit of analysis: crash, person, vehicle, trip, segment, intersection, image, frame, video, model run, seed, city, or paper.
- [ ] State the independence level: independent observations, clustered sites, repeated subjects, repeated routes, repeated models, or time periods.
- [ ] State the estimand: mean difference, proportion difference, odds ratio, rate ratio, risk difference, marginal effect, prediction metric difference, correlation, or causal effect.
- [ ] Separate exploratory analysis from confirmatory hypothesis testing.
- [ ] Write the null and alternative hypothesis before choosing the test.

## Test and Model Decision Matrix

| Situation | Default choice | Check before reporting |
| --- | --- | --- |
| Two independent groups, continuous outcome | Welch two-sample t-test | Distribution, outliers, unequal variance, effect size |
| Two paired measurements, continuous outcome | Paired t-test | Distribution of paired differences |
| More than two independent groups | ANOVA or Welch ANOVA | Variance, residuals, planned contrasts |
| More than two paired or repeated groups | Repeated-measures ANOVA, mixed model, or Friedman test | Within-subject/site dependence |
| Binary outcome | Logistic regression | Separation, calibration, odds ratio interpretation |
| Count outcome | Poisson or negative binomial regression | Overdispersion and excess zeros |
| Crash frequency with exposure | Count model with offset | Correct denominator such as VMT, AADT, time, or segment length |
| Ordered severity outcome | Ordinal logistic or probit model | Proportional odds assumption |
| Nominal multiclass outcome | Multinomial logistic model | Class imbalance and reference category |
| Time-to-event outcome | Kaplan-Meier or Cox model | Censoring and proportional hazards |
| Continuous outcome with covariates | Linear regression or robust regression | Residuals, leverage, heteroskedasticity |
| Panel or repeated-site data | Fixed effects, random effects, mixed model, GEE, or clustered SE | Site/time dependence and estimand |
| Spatially correlated data | Spatial model or spatial/cluster robust SE | Spatial autocorrelation and leakage |
| Before/after intervention | Difference-in-differences or interrupted time series | Parallel trends, seasonality, comparison group |
| Same test set model comparison | McNemar, paired bootstrap, permutation test, or corrected resampled test | Paired dependence and multiple metrics |
| Correlation | Pearson, Spearman, or Kendall | Linear vs monotonic relationship |
| Small expected cell counts | Fisher exact or exact/permutation method | Cell sizes and test assumptions |
| Many related tests | Holm, Benjamini-Hochberg, or planned contrasts | Family of hypotheses |

## Assumption Checks

- [ ] Check independence at the correct unit, not only row count.
- [ ] Check normality of residuals or paired differences when the test requires it.
- [ ] Check unequal variance and use Welch or robust standard errors when needed.
- [ ] Check residual plots for linearity and heteroskedasticity.
- [ ] Check multicollinearity before interpreting coefficients.
- [ ] Check overdispersion for count models.
- [ ] Check zero inflation for crash, event, and rare-count outcomes.
- [ ] Check proportional odds for ordinal models.
- [ ] Check proportional hazards for Cox models.
- [ ] Check missingness mechanism, exclusions, and imputation sensitivity.
- [ ] Check class imbalance and report appropriate metrics.
- [ ] Check temporal leakage in train/test splits.
- [ ] Check spatial leakage when nearby sites, frames, trips, or road segments may be duplicated across splits.

## Required Formulas and Reporting

- [ ] Report the model equation or test statistic.
- [ ] Define all variables, indices, offsets, weights, and link functions.
- [ ] Report sample size by group and final analytic sample after exclusions.
- [ ] Report descriptive statistics matched to distribution: mean/SD, median/IQR, count/percent, or rate with exposure.
- [ ] Report effect size: Cohen's d, Hedges g, odds ratio, rate ratio, risk difference, marginal effect, AUC difference, F1 difference, RMSE difference, or domain-unit difference.
- [ ] Report confidence intervals or bootstrap intervals.
- [ ] Report exact p-values when appropriate and avoid making p-values the whole result.
- [ ] Report multiple-comparison correction when testing a family of related hypotheses.
- [ ] Report software, package versions, random seeds, split logic, and relevant hardware or compute.
- [ ] Report practical significance in domain units.

## Diagnostics

- [ ] Include residual vs fitted plot for regression models.
- [ ] Include Q-Q plot or paired-difference distribution where normality matters.
- [ ] Include influence or leverage diagnostics for regression.
- [ ] Include observed vs predicted or calibration plot for prediction models.
- [ ] Include confusion matrix for classification.
- [ ] Include ROC and PR curves when relevant; prefer PR curves for rare-event detection.
- [ ] Include overdispersion statistic for count models.
- [ ] Include sensitivity analysis for influential observations, alternative specifications, and missing-data choices.
- [ ] Include robustness check using nonparametric, bootstrap, or permutation method when assumptions are marginal.
- [ ] Include external, temporal, or geographic validation if generalization is claimed.

## Transportation and CS Pitfalls

- [ ] Do not use ordinary t-tests on repeated model runs when folds, seeds, subjects, or sites are dependent.
- [ ] Do not compare ML classifiers only by accuracy under severe class imbalance.
- [ ] Do not treat frames or images from the same video, site, or trip as independent observations.
- [ ] Do not ignore site, route, driver, weather, city, or time clustering.
- [ ] Do not model crash counts without exposure.
- [ ] Do not claim crash risk from crash frequency without a denominator.
- [ ] Do not use Poisson regression when overdispersion is substantial without correction.
- [ ] Do not dichotomize continuous variables unless theoretically justified.
- [ ] Do not interpret odds ratios as risk ratios when outcomes are common.
- [ ] Do not claim causality from cross-sectional association.
- [ ] Do not control for post-treatment variables in causal models.
- [ ] Do not tune models on the test set.
- [ ] Do not report only the best seed or fold.
- [ ] Do not ignore multiple hypotheses across metrics, subgroups, or model variants.
- [ ] Do not present statistical significance without effect size.
- [ ] Do not use nonparametric tests as a fix for dependence, confounding, or poor design.
- [ ] Do not confuse prediction performance with explanatory validity.

## Final Statistical Gate

- [ ] Every hypothesis has a matched test or model.
- [ ] Every model has assumptions checked or explicitly relaxed.
- [ ] Every result has an effect size and confidence interval when applicable.
- [ ] Every p-value belongs to a stated hypothesis family.
- [ ] Every ML comparison uses paired or resampling-aware inference when applicable.
- [ ] Every transportation safety result uses correct exposure, unit, and clustering.
- [ ] Every causal claim is supported by design, identification assumptions, and sensitivity checks.
