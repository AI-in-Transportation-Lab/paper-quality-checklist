# ML Model Selection and Validation

Use when the paper proposes, applies, or compares ML/DL models.

---

## 1. Task-to-Model Map

### Tabular and Structured Data

| Task | Recommended | Baseline to beat | Note |
|---|---|---|---|
| Binary/multiclass classification | Gradient boosting (XGBoost, LightGBM) | Logistic regression | Neural nets viable at N > 100k |
| Regression (tabular features) | Gradient boosting; elastic net | Linear regression | Neural nets for very large N |
| Crash / event count | NB GLM with exposure offset | Poisson GLM | Check overdispersion $\hat{\phi}$ |
| Ordered severity | Ordinal logistic; random forest | Binary logistic | Do not use OLS on integer codes |
| Survival / time-to-event | Cox PH; random survival forests | KM estimator | Check PH assumption |
| Panel / longitudinal tabular | Mixed effects; LASSO-FE | Pooled OLS | ICC determines clustering need |

### Temporal and Sequence Data

| Task | Recommended | Baseline to beat | Note |
|---|---|---|---|
| Short-horizon traffic prediction | Transformer (PatchTST, iTransformer); N-HiTS | ARIMA, linear regression | Benchmark on same test split |
| Long-horizon traffic prediction | N-BEATS; TimeMixer | Exponential smoothing | Simple models often competitive |
| Event detection in time series | LSTM/TCN + attention | Threshold-based rule | Report latency at deployment scale |
| Trajectory prediction | Social Force; LSTM encoder-decoder; Transformer | Constant velocity | Report ADE/FDE at 1s, 3s, 5s |

### Spatial and Graph Data

| Task | Recommended | Baseline to beat | Note |
|---|---|---|---|
| Road network prediction | STGNN (DCRNN, GWNET, STID) | GCN; historical average | Prevent spatial leakage in splits |
| Spatial interpolation | Kriging; GNN | IDW; spatial regression | Validate on held-out regions |
| OD demand matrix | Graph Transformer; matrix factorization | Gravity model | Requires spatial holdout eval |

### Vision and Sensor Data

| Task | Recommended | Baseline to beat | Note |
|---|---|---|---|
| Object detection (AV) | YOLOv9; DETR family | Faster R-CNN | Official split; no frame-level split |
| Semantic segmentation | SegFormer; Mask2Former | DeepLab | IOU per class + mIOU |
| Point cloud detection | CenterPoint; VoxelNet | PointPillars | nuScenes or Waymo official metrics |
| Video anomaly / incident detection | 3D CNN; SlowFast; VideoMAE | Optical flow baseline | Clip-level split; AUPRC for rare events |

### Foundation and Pre-trained Models

- [ ] License checked and cited (Apache 2.0, MIT, CC, or proprietary).
- [ ] Fine-tuning protocol documented: frozen layers, learning rate schedule, epochs.
- [ ] Zero-shot / few-shot claims tested against a supervised lower bound.
- [ ] Domain shift between pre-training corpus and transportation data discussed.
- [ ] LLM outputs used as features or labels are validated against ground truth.

---

## 2. Validation Protocol

### Data Split Strategy

| Data type | Required split | Common mistake |
|---|---|---|
| IID tabular | 60/20/20 or stratified k-fold | No stratification on class or site |
| Time series | Chronological split (no shuffle) | Random shuffle leaks future |
| Spatial data | Spatially disjoint holdout regions | Nearby sites in train and test |
| Video / trajectory | Clip- or trip-level split | Frame-level split leaks clips |
| Multi-site crash | Site-level holdout | Same site in train and test |
| Rare event | Stratified on event rate | Class imbalance distorts random split |

- [ ] Split boundaries defined **before** any model fitting.
- [ ] Preprocessing (scaling, imputation, encoding) fitted on train only; applied to val and test.
- [ ] Hyperparameters tuned on validation set; test set touched **exactly once**.
- [ ] Final reported metrics come from the untouched test set.

### Cross-Validation

- [ ] Stratified k-fold for classification (k = 5 or 10 standard).
- [ ] Expanding or sliding-window CV for temporal data.
- [ ] Report mean ± std across folds — not only mean.
- [ ] For significance testing: 5×2CV paired t-test; plain t-test on fold means is incorrect.

---

## 3. Evaluation Metrics

### Classification

| Scenario | Primary | Secondary |
|---|---|---|
| Balanced classes | Macro-F1, accuracy | Confusion matrix |
| Imbalanced (safety-critical) | AUPRC, balanced accuracy | Precision-recall curve |
| Binary crash / incident | AUPRC (preferred over AUROC for rare events) | FPR at fixed TPR |
| Multiclass severity | Macro-F1, Cohen's κ | Per-class F1 |

- [ ] Accuracy alone is **not sufficient** when class ratio > 5:1.
- [ ] AUPRC preferred over AUROC for rare positive events.
- [ ] Decision threshold is reported when a fixed operating point is used in deployment.

### Regression

| Metric | Formula | When |
|---|---|---|
| RMSE | $\sqrt{\frac{1}{n}\sum(y_i-\hat{y}_i)^2}$ | Scale-sensitive; same units as $Y$ |
| MAE | $\frac{1}{n}\sum|y_i-\hat{y}_i|$ | Outlier-robust; same units |
| MAPE | $\frac{100}{n}\sum\frac{|y_i-\hat{y}_i|}{y_i}$ | Avoid when $y_i \approx 0$ |
| $R^2$ | $1 - SS_{res}/SS_{tot}$ | Proportion of variance explained |

- [ ] Report in domain units: crashes/year/km, vehicles/hr, kg CO₂/km, ms latency.
- [ ] Report both RMSE and MAE; they capture different error characteristics.

### Trajectory Prediction

| Metric | Definition |
|---|---|
| ADE | Mean L2 distance over all time steps |
| FDE | L2 distance at final predicted time step |
| Miss Rate | Fraction with FDE > threshold (e.g., 2 m) |
| minADE / minFDE | Best over K predictions (multimodal models) |

- [ ] Report for multiple horizons (1 s, 3 s, 5 s are standard).
- [ ] Include constant-velocity and social force as baselines.

### Calibration (Required for Safety-Relevant Models)

- [ ] Expected Calibration Error (ECE) reported.
- [ ] Reliability diagram (confidence vs accuracy) included.
- [ ] Temperature scaling or Platt scaling applied if ECE is high.

---

## 4. Ablation Study Design

- [ ] Each ablated component corresponds to a **design claim** in the paper.
- [ ] All ablation conditions trained under identical conditions (epochs, optimizer, data).
- [ ] Full model is not the only condition trained to convergence.
- [ ] Ablation table reports mean ± std across seeds.
- [ ] Ordering of conditions follows the paper's contribution narrative.

---

## 5. Hyperparameter Reporting

- [ ] Search space (ranges and scales: linear, log) defined and reported.
- [ ] Tuning method: grid / random / Bayesian — with number of trials and compute budget.
- [ ] Final model trained on train + validation after best hyperparameters found.
- [ ] Early stopping criterion (patience, metric, epoch) documented.
- [ ] Optimizer, learning rate, batch size, weight decay, and scheduler reported.

---

## 6. Common Failure Modes

- [ ] **Data leakage:** features derived from the test set (e.g., global statistics, encodings) used in training.
- [ ] **Optimistic test set:** test set referenced during development; final eval should be run once.
- [ ] **Weak baselines:** stale (> 3 years), not tuned, or missing strong recent methods.
- [ ] **Undocumented tricks:** gradient clipping, loss weighting, label smoothing used but not reported.
- [ ] **Single-seed reporting:** variance across ≥ 3 seeds not reported.
- [ ] **Benchmark mismatch:** comparing against results from a different split or data version.
- [ ] **Transfer claims without transfer eval:** generalization to new cities or conditions claimed but not tested.
- [ ] **Calibration ignored:** confidence scores used in safety decisions without calibration check.
- [ ] **Subgroup fairness overlooked:** disparate performance across demographic, geographic, or temporal subgroups not analyzed.
