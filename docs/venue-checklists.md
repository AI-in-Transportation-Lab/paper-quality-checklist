# Venue Checklists

For mixed AI-in-transportation work, satisfy both the transportation and CS/AI sections relevant to your venue.

---

## 1. Transportation Engineering Venues

### 1.1 Transportation Research Part B — Methodological

**Scope:** Fundamental methodological advances: travel demand, network models, game theory, behavioral models, optimization.

- [ ] The contribution advances a **methodological framework**, not only an application of existing methods.
- [ ] Mathematical derivation, proof, or rigorous convergence analysis is included.
- [ ] Computational complexity or tractability is addressed.
- [ ] Connects to behavioral foundations (utility theory, rational choice, activity-based modeling).
- [ ] Empirical illustration (if any) supports the methodological claim — not the other way around.
- [ ] No contribution = a comparison study without a new model or theory.

### 1.2 Transportation Research Part C — Emerging Technologies

**Scope:** ITS, connected/automated vehicles, ML in transportation, sensor data, real-time control and operations.

- [ ] The ML or technology contribution has a **specific transportation problem** as the central motivation.
- [ ] Evaluation uses real transportation data or a well-justified, calibrated simulation.
- [ ] Algorithmic novelty is distinguished from application novelty — both are valid, but must be positioned correctly.
- [ ] Generalizability across cities, road types, or operating conditions is evaluated or stated as a limitation.
- [ ] Real-time feasibility or deployment constraints are discussed if operational use is claimed.
- [ ] Strong recent baselines are included; a neural network beating a 2015 method is insufficient.

### 1.3 Transportation Research Part D — Transport and Environment

**Scope:** Environmental impacts: emissions, noise, energy, climate, sustainability.

- [ ] Emission calculations use a defensible methodology (MOVES, HBEFA, COPERT, or peer-reviewed equivalent) with year and geography stated.
- [ ] CO₂-equivalent units are used consistently; GWP conversion factors cited.
- [ ] Statistical uncertainty propagates through the emission or energy calculation.
- [ ] Rebound effects and behavioral responses to efficiency improvements are discussed when relevant.

### 1.4 Accident Analysis & Prevention and AMAR

**Scope:** Crash causation, severity, risk factors, countermeasure evaluation.

- [ ] Exposure denominator is **correct for the study type**: VMT, AADT, person-trips, hours exposed, segment length × AADT.
- [ ] Regression-to-the-mean bias addressed in before/after designs (EB/HSM method or comparison group).
- [ ] Spatial and site clustering is modeled: NB with random effects, HGLM, ZINB, or GEE.
- [ ] Severity ordering modeled correctly: ordinal logistic or probit — **not OLS on severity codes**.
- [ ] Countermeasure claims use treatment/control group or quasi-experimental design; before/after with no control group is insufficient for causal claims.
- [ ] Safety conclusions distinguish frequency, risk, severity, surrogate, and perception measures.

### 1.5 IEEE Transactions on Intelligent Transportation Systems (T-ITS)

**Scope:** ITS technology: sensing, communication, control, autonomous vehicles, traffic management.

- [ ] System architecture, latency, and scalability are quantified.
- [ ] Hardware, sensor type, or communication protocol is specified.
- [ ] High-fidelity simulation (SUMO, VISSIM, CARLA) or real-world deployment is used.
- [ ] Safety, robustness under noise/adversarial conditions, and failure modes are reported.
- [ ] At least one strong, recently published baseline is included.

### 1.6 Transportmetrica A / B and IATSS Research

- [ ] **Part A** (Transport Science): network equilibrium, route choice, simulation — requires analytical or simulation-based methods with mathematical grounding.
- [ ] **Part B** (Dynamic Traffic): real-time data, state estimation, short-term prediction — dynamic systems perspective required.
- [ ] IATSS: Asia-Pacific focus; policy and practice implication explicit.

### 1.7 TRB Annual Meeting and Transportation Research Record (TRR)

- [ ] Paper fits a numbered TRB standing committee scope.
- [ ] 7,500-word limit (excluding references and figures); figures and tables count.
- [ ] Practical implication is **explicit for practitioners and agency staff** — this is the primary audience.
- [ ] TRR journal submission requires separate full peer review after TRB acceptance.

### 1.8 ITSC — IEEE Intelligent Transportation Systems Conference

- [ ] 6-page IEEE double-column format (1 additional page allowed with fee).
- [ ] Algorithm, system, or method novelty is the primary claim.
- [ ] Quantitative comparison against published baselines on real or realistic simulation data.

### 1.9 IV — IEEE Intelligent Vehicles Symposium

- [ ] Scope: perception, prediction, planning, control for automated and connected vehicles.
- [ ] Evaluated on standard AV datasets (nuScenes, Waymo Open, KITTI, Argoverse) or real-world tests.
- [ ] Safety and deployment considerations explicitly mentioned.

---

## 2. ACM Venues

### 2.1 ACM SIGSPATIAL — most relevant for transportation and mobility

**Scope:** Spatial data management, GIS, mobility, map matching, trajectory analysis, urban computing.

- [ ] Spatial indexing, query efficiency, or scalability is the primary evaluation dimension.
- [ ] Baselines include state-of-the-art spatial and mobility methods, not only general ML methods.
- [ ] **Spatial leakage** in evaluation is explicitly prevented (geographically separated test set).
- [ ] Large-scale experiments (city or nationwide) support scalability claims.
- [ ] Data pipeline (map, trajectory, point-of-interest preprocessing) is documented.

### 2.2 KDD — ACM SIGKDD

**Research track:** Algorithm or statistical methodology novelty.
**Applied Data Science track:** Real deployment impact, scale, and demonstrated value.

- [ ] Research: ablation isolates each component; baselines are tuned under the same budget.
- [ ] ADS: deployment context, scale (rows, users, throughput), and real-world outcome metric are stated.
- [ ] Scalability demonstrated (wall-clock time, memory on large datasets).

### 2.3 ACM CHI

**Scope:** HCI, UX, accessible interfaces, mobility applications, user studies.

- [ ] User study protocol (participants, recruitment, tasks, compensation, IRB/ethics) is complete.
- [ ] Effect sizes and power reported for quantitative findings.
- [ ] Qualitative coding is systematic: inter-rater reliability (Cohen's κ or Krippendorff's α) reported.
- [ ] Ecological validity and population bias are addressed.

### 2.4 ACM Transactions Relevant to AIT

| Journal | Scope | Key check |
|---|---|---|
| ACM TIST | Intelligent systems, AI applications | Deployment context and real-world evaluation required |
| ACM TKDD | Knowledge discovery, data mining | Algorithmic rigor + large-scale evaluation |
| ACM TOSEM | Software engineering methods | Implementation artifacts, test coverage |

---

## 3. CS and AI Conferences

### 3.1 NeurIPS

**Scope:** ML algorithms, theory, datasets, benchmarks, societal implications.

- [ ] Complete the **NeurIPS paper checklist** (limitations, societal impact, compute, licenses, data).
- [ ] Theory papers: theorem and proof sketch in main text; full proof in appendix.
- [ ] Empirical papers: ≥3 random seeds per dataset; mean ± std or error bars on all main results.
- [ ] Ablation study justifies each major design choice.
- [ ] Societal impact (positive and negative) is in the main paper, not hidden in appendix.
- [ ] Code and data availability stated; reproducibility statement required in final version.
- [ ] No test set used for hyperparameter tuning.

### 3.2 ICLR

**Scope:** Representation learning, deep learning, theory, generalization, robustness.

- [ ] OpenReview submission; complete author anonymization (no self-identifying links).
- [ ] **Reproducibility checklist** attached: code, seeds, hardware, training details.
- [ ] Empirical claims: confidence intervals over ≥3 seeds — not single-run numbers.
- [ ] Ablation justifies each architectural or training decision.
- [ ] Generalization claims tested on held-out domains, datasets, or distribution shifts.
- [ ] ICLR community highly values code release; missing code is a common weak-reject reason.

### 3.3 ICML

**Scope:** ML algorithms, theory, optimization, applications.

- [ ] ICML **experimental reproducibility checklist** submitted.
- [ ] If theory: theorem statements include all required conditions; proofs in appendix.
- [ ] Comparison baselines include the best published result on each benchmark under comparable settings.
- [ ] For new benchmarks: data collection, annotation protocol, intended use, baseline results.
- [ ] **Compute cost and estimated carbon footprint** noted (ICML sustainability guidance).

### 3.4 AAAI

**Scope:** Broad AI: planning, reasoning, NLP, vision, ML, robotics, multiagent, knowledge representation.

- [ ] 7-page content limit + 1 page references; supplemental appendix is separate and optional.
- [ ] Primary contribution is a **technical AI advance** — application alone is insufficient.
- [ ] AAAI **responsible AI checklist** submitted with final paper.

### 3.5 IJCAI

**Scope:** Broad AI, multiagent systems, planning, constraint reasoning, ML.

- [ ] 7 pages content + 1 page references.
- [ ] Contribution framed for the broad AI audience across subfields.
- [ ] Ethics statement included when results have social or safety implications.

### 3.6 CVPR / ICCV / ECCV — Computer Vision

- [ ] Benchmarked on **established datasets** (ImageNet, COCO, Cityscapes, nuScenes, Waymo, BDD100K) using official train/val/test splits.
- [ ] No cherry-picked qualitative examples; include failure cases in supplement.
- [ ] CVPR/ICCV: strict **double-blind** — no author-identifying links until camera ready.
- [ ] Dataset splits do not leak between train and test (especially for video-derived frames).
- [ ] For AV/transportation papers: cite domain-specific baselines (BEVFusion, PointPillars, CenterPoint, etc.).
- [ ] State-of-the-art claims use identical pre-training data and resolution.

### 3.7 ACL / EMNLP / NAACL — NLP

- [ ] Standard benchmarks use official evaluation scripts (SacreBLEU, ROUGE, BERTScore).
- [ ] Significance testing for metric differences uses bootstrap resampling ($p < 0.05$).
- [ ] **Model cards and data statements** submitted with final papers (ACL 2024+ policy).
- [ ] LLM-generated text in experiments or annotation is labeled explicitly.
- [ ] **ACL Responsible NLP Checklist** completed.

### 3.8 CoRL — Conference on Robot Learning

**Scope:** Robot learning, policy learning, imitation learning, sim-to-real, autonomous driving. Directly relevant to AV/ADS safety papers.

- [ ] Real-robot or high-fidelity simulation (CARLA, Isaac Gym, MuJoCo, nuPlan) experiments.
- [ ] **Failure modes and safety edge cases** described — not only success demonstrations.
- [ ] Generalization across environments, scenes, or tasks tested beyond training distribution.
- [ ] Policy checkpoints, environment code, and random seeds available for reproducibility.

---

## 4. Mixed AI-in-Transportation Papers

When the contribution spans both ML/AI methods and transportation problems:

- [ ] The **transportation problem** is the central motivation, not a convenient test bed for an ML method.
- [ ] Data quality and domain validity checks from Section 1 are satisfied.
- [ ] ML rigor checks from Section 3 (baselines, ablations, seeds, uncertainty) are satisfied.
- [ ] Venue is chosen based on the primary audience: transportation researchers vs. AI researchers.
- [ ] If submitting to a CS venue: transportation context explained for a non-domain reader.
- [ ] If submitting to a transportation venue: ML method explained for a non-ML reader.
- [ ] **Interpretability addressed** when the model drives decisions affecting safety or equity.

---

## 5. Venue Family Matrix

| Venue family | Primary contribution | Evidence bar | Artifact expectation | Top rejection reason |
|---|---|---|---|---|
| TR Part B | Methodological framework | Mathematical rigor | Reproducible derivation | Application without method novelty |
| TR Part C | ITS / ML application | Real data + strong baseline | Code when possible | Algorithm without transport framing |
| AA&P / AMAR | Crash / safety analysis | Correct exposure, clustering, design | Data protocol | Causal claim from cross-sectional data |
| IEEE T-ITS | ITS system / algorithm | System-level evaluation | Code / hardware spec | Demo without systematic evaluation |
| TRR | Practice-relevant finding | Clear methodology, practical implication | Data statement | No agency or practitioner relevance |
| ACM SIGSPATIAL | Spatial / mobility data | Spatial leakage-free eval + scalability | Code + data | Ignoring spatial dependencies |
| KDD Research | Algorithm / data mining | Strong baselines, ablation, scalability | Code + reproducibility | Overclaiming on weak or outdated baselines |
| NeurIPS / ICLR | ML method / theory | Seeds, ablation, proof, uncertainty | Code + checklist | Missing ablation or single-seed results |
| CVPR / ICCV | Vision task / model | Official benchmark, no cherry-picking | Code + model | Cherry-picked results; split leakage |
| CoRL | Robot / AV learning | Real or sim-to-real + failure analysis | Policy code + env | No failure analysis; no generalization test |
| ACL / EMNLP | NLP method / benchmark | Official scripts, bootstrap significance | Model cards + data | Missing significance tests; no model card |
