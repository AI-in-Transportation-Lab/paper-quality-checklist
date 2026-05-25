# Venue Checklists

Use the venue family that best matches the intellectual contribution. For mixed AI-in-transportation work, use both the transportation and CS/AI sections.

## Venue Name Sanity Check

- [ ] Use `NeurIPS`, not `NeuralIPS`.
- [ ] Use `ICLR` or `ICML`; `ICMLR` is usually a typo.
- [ ] Check whether `AC` means `ACM`, `ACL`, or something else.
- [ ] Use `IEEE T-ITS` for IEEE Transactions on Intelligent Transportation Systems.
- [ ] Use `Transportation Research Part C`, not only `TRC`, in formal text.
- [ ] Use the venue's current official author instructions, template, and policy page.

## Transportation Engineering

Example venues: TRB/TRR, Transportation Research Part C, Analytic Methods in Accident Research, IEEE T-ITS, ASCE transportation journals, Accident Analysis & Prevention, Transportation Research Record-style outlets.

### Scope Fit

- [ ] The core contribution is transportation-relevant, not only an algorithm applied to mobility data.
- [ ] The paper names the transportation problem: safety, operations, planning, infrastructure, behavior, freight, transit, micromobility, automation, or ITS.
- [ ] The study context is clear: facility type, geography, mode, time period, users, and operating conditions.
- [ ] The practical implication is defensible for engineers, agencies, researchers, or policy makers.

### Evidence Standard

- [ ] Data provenance is credible and documented.
- [ ] Exposure is correct for rates and risk claims: AADT, VMT, trips, segment length, time, population, or relevant denominator.
- [ ] Crash, conflict, severity, delay, behavior, or operations metrics are defined precisely.
- [ ] Spatial, temporal, site, driver, road-user, or route clustering is handled.
- [ ] Transferability limits are stated for other cities, road types, periods, and user groups.
- [ ] Safety conclusions distinguish frequency, risk, severity, conflict, perception, and surrogate measures.

### Common Failure Modes

- [ ] Do not claim policy impact without a mechanism and implementation context.
- [ ] Do not pool heterogeneous road users or facility types without checking interactions.
- [ ] Do not interpret crash frequency as crash risk without exposure.
- [ ] Do not present black-box predictions as safety insight without interpretation or validation.
- [ ] Do not make causal claims from cross-sectional associations.

## ACM Computing

Example venues: ACM Transactions, CHI, KDD, SIGIR, SIGMOD, SIGCOMM, CSCW, UIST, IMWUT, and other SIG venues.

### Scope Fit

- [ ] The paper fits the target ACM community, not just ACM formatting.
- [ ] The contribution type is clear: algorithm, system, dataset, HCI study, theory, benchmark, measurement, or artifact.
- [ ] The paper uses the correct ACM template, CCS concepts, keywords, rights statement, and anonymization mode.
- [ ] The related work speaks to the target SIG's expectations.

### Evidence Standard

- [ ] The evaluation matches the SIG: user validity for CHI/CSCW, scale and baselines for KDD, retrieval metrics for SIGIR, system evidence for SIGMOD/SIGCOMM.
- [ ] Human-subjects work states IRB, consent, recruitment, compensation, and risk handling as required.
- [ ] Artifact claims are supported by setup instructions, expected runtime, environment, data access, and license status.
- [ ] Claims about usability, fairness, robustness, scalability, or efficiency are backed by direct evidence.
- [ ] Ablations or component studies isolate the contribution when the method has multiple parts.

### Common Failure Modes

- [ ] Do not submit a domain application without a computing contribution.
- [ ] Do not hide implementation details needed to evaluate the artifact.
- [ ] Do not use an impressive demo as a substitute for a valid evaluation.
- [ ] Do not ignore participant, platform, or dataset bias.
- [ ] Do not claim an ACM artifact badge unless the artifact satisfies the venue's badge criteria.

## Major CS and AI Conferences

Example venues: NeurIPS, ICML, ICLR, AAAI, IJCAI, ACL, EMNLP, NAACL, CVPR, ICCV, ECCV, KDD, TheWebConf.

### Scope Fit

- [ ] The main contribution is clear to the target community: learning method, theory, benchmark, dataset, system, empirical finding, evaluation protocol, or application with general insight.
- [ ] The closest baselines are recent and strong.
- [ ] The paper explains why the result matters beyond one dataset or case study.
- [ ] The submission follows anonymity, page limit, checklist, ethics, reproducibility, and supplemental rules.

### Evidence Standard

- [ ] Experiments include fair baselines, ablations, error analysis, and uncertainty across seeds or splits when needed.
- [ ] ML papers report hyperparameters, tuning budget, compute, data splits, and random seeds.
- [ ] Vision and NLP papers include qualitative analysis only when it adds evidence, not decoration.
- [ ] Rare-event, imbalanced, or safety-critical tasks report metrics beyond accuracy.
- [ ] Benchmark or dataset papers include licensing, documentation, collection process, bias analysis, and intended use.
- [ ] Claims about state of the art use comparable settings and official metrics.

### Common Failure Modes

- [ ] Do not tune on the test set.
- [ ] Do not report only the best seed, fold, or checkpoint.
- [ ] Do not compare against weak or outdated baselines.
- [ ] Do not claim generalization from one small or leaked dataset.
- [ ] Do not confuse prediction performance with explanation or causal validity.
- [ ] Do not omit negative societal, safety, privacy, or misuse risks when relevant.

## Venue Family Matrix

| Venue family | Main contribution | Evidence standard | Artifact expectation | Common trap |
| --- | --- | --- | --- | --- |
| Transportation journals | Transportation insight, method, or policy relevance | Domain-valid data, exposure, clustering, transferability | Data/code when possible; clear restrictions when not | Treating AI performance as transportation contribution |
| Transportation conferences | Timely transportation result or practice-facing insight | Clear problem framing and practical implication | Usually lighter than journals but still auditable | Weak venue fit or formatting errors |
| ACM journals | Mature computing contribution | Complete evaluation, proofs, or systems evidence | Strong reproducibility and artifact maturity | Conference-length evidence in a journal paper |
| ACM conferences | SIG-specific computing contribution | Community-specific evaluation | Artifact readiness when claimed | Missing SIG audience fit |
| AI/ML conferences | Method, benchmark, theory, or strong empirical insight | Strong baselines, ablations, uncertainty | Code/data/checklist details increasingly expected | Overclaiming novelty or generalization |
| Vision/NLP conferences | Task, model, dataset, or benchmark contribution | Official metrics, qualitative error analysis, leakage control | Dataset/model cards where relevant | Hidden data leakage or weak baselines |
