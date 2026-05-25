# Universal Checklist

Use this page for every paper before moving to venue-specific checks.

## Contribution and Novelty

- [ ] The paper states **one primary contribution** (method / dataset / theory / empirical finding / system / benchmark / policy insight) and at most two secondary contributions.
- [ ] The novelty is compared against the **closest prior work**, not only broad topic areas.
- [ ] Claims avoid words such as *first*, *novel*, *robust*, *safe*, *causal*, or *generalizable* unless the evidence directly supports them.
- [ ] The title, abstract, introduction, results, and conclusion describe the **same contribution**.
- [ ] The contribution can be stated in one sentence of the form: "We propose X, which achieves Y on Z, enabling W."

## Literature Positioning

- [ ] The related work explains the **gap the paper fills**, not only what prior work did.
- [ ] Foundational, recent (≤ 3 years), and venue-relevant papers are cited.
- [ ] Transportation papers cite domain literature, not only AI or statistics literature.
- [ ] CS/AI papers cite method baselines, benchmark papers, and relevant negative results.
- [ ] Citation claims are verified against the cited paper — not copied from another paper's wording.
- [ ] Missing citation types: ablation baselines, negative results, dataset papers, concurrent work.

## Method Validity

- [ ] Research questions or hypotheses are explicit and numbered.
- [ ] The method matches the question: explanatory, predictive, causal, descriptive, simulation, design, or system evaluation.
- [ ] The unit of analysis is stated (crash, trip, segment, image, frame, model run, city, …).
- [ ] Inclusion and exclusion criteria are stated with counts.
- [ ] Key assumptions are named and checked where possible.
- [ ] Alternative explanations for the main result are considered and addressed.
- [ ] Sensitivity, ablation, or robustness checks are included when the main result depends on modeling choices.

## Data and Protocol

- [ ] Data source, collection period, geography, sampling frame, and preprocessing are documented.
- [ ] Labels, annotations, derived variables, and exclusions are defined.
- [ ] Train, validation, test, temporal, spatial, or external splits are described and justified.
- [ ] The paper states whether data can be shared, and why if it cannot.
- [ ] Privacy, human-subjects, proprietary, and safety-sensitive data constraints are addressed.
- [ ] Missing data handling (listwise deletion, imputation method, MCAR/MAR/MNAR assumption) is reported.

## Results and Claims

- [ ] Each table or figure answers a stated research question or supports a necessary diagnostic.
- [ ] Main results include uncertainty (CI, SE, std across seeds/folds) and effect size where applicable.
- [ ] Practical significance is stated in domain units: crashes, delay, cost, risk, emissions, throughput, latency, F1 gain, etc.
- [ ] Baselines are fair, current (≤ 3 years for fast-moving fields), and appropriate for the venue.
- [ ] Negative, null, or mixed results are reported — not selectively hidden.
- [ ] The discussion does not claim causality from association unless the design supports causal inference.

## Limitations

- [ ] Limitations distinguish: data limits, model/algorithmic limits, causal limits, and external validity.
- [ ] The paper states where the method **should not be used**.
- [ ] Generalization is bounded to the studied population, roadway context, data source, model family, or benchmark.
- [ ] Safety and equity implications are discussed when results affect road users or deployed systems.

## Ethics and AI Use

- [ ] The venue's AI-use policy is checked before submission.
- [ ] AI assistance in writing, coding, analysis, or figure generation is disclosed if required.
- [ ] No confidential, identifiable, or restricted data were entered into unauthorized AI tools.
- [ ] Human-subjects, IRB, consent, or exemption status is stated when relevant.
- [ ] Dataset licenses, model licenses, and third-party figure permissions are checked.
- [ ] No hidden prompts, invisible text, or reviewer-targeted instructions remain in the manuscript.

## Reproducibility

- [ ] Code availability is stated (URL or reason for restriction).
- [ ] Data availability is stated.
- [ ] Package versions, software versions, random seeds, hardware, and compute budget are documented where relevant.
- [ ] Model checkpoints, prompts, hyperparameters, and preprocessing scripts are recorded.
- [ ] Tables and figures can be regenerated from the documented analysis workflow.
- [ ] Restricted artifacts have a clear access procedure.

## Writing and Structure

- [ ] Acronyms are defined on first use and used consistently throughout.
- [ ] Terminology, notation, variable names, and formatting are consistent (check subscripts, superscripts, and bold/italic conventions).
- [ ] The conclusion summarizes contribution, evidence, implication, and limitation without repeating table values.
- [ ] The manuscript follows the required template, page limit, and section order.

## Figures, Tables, Equations, and References

- [ ] Every figure and table is referenced and interpreted in the text.
- [ ] Captions are self-contained: a reviewer can understand the figure without re-reading the paper.
- [ ] Axes, units, legends, color scales (accessible to colorblind readers), sample sizes, and uncertainty markers are present.
- [ ] Equations are numbered when referenced; all variables are defined on first use.
- [ ] References are complete, real, and formatted for the venue.
- [ ] In-text citations match the reference list; no broken cross-references in the final PDF.

## Literature Positioning

- [ ] The related work explains the gap the paper fills.
- [ ] Foundational, recent, and venue-relevant papers are cited.
- [ ] Transportation papers cite domain literature, not only AI or statistics literature.
- [ ] CS/AI papers cite method baselines, benchmark papers, and relevant negative results.
- [ ] Citation claims are checked against the cited paper, not copied from another paper's wording.

## Method Validity

- [ ] Research questions or hypotheses are explicit.
- [ ] The method matches the question: explanatory, predictive, causal, descriptive, simulation, design, or system evaluation.
- [ ] The unit of analysis is clear.
- [ ] Inclusion and exclusion criteria are stated.
- [ ] Key assumptions are named and checked where possible.
- [ ] Alternative explanations are considered.
- [ ] Sensitivity, ablation, or robustness checks are included when the main result depends on modeling choices.

## Data and Protocol

- [ ] Data source, collection period, geography, sampling frame, and preprocessing are documented.
- [ ] Labels, annotations, derived variables, and exclusions are defined.
- [ ] Train, validation, test, temporal, spatial, or external splits are described.
- [ ] The paper states whether data can be shared and why if it cannot.
- [ ] Privacy, human-subjects, proprietary, and safety-sensitive data constraints are addressed.
- [ ] Missing data handling is reported.

## Results and Claims

- [ ] Each table or figure answers a stated research question or supports a necessary diagnostic.
- [ ] Main results include uncertainty, effect size, or variability where applicable.
- [ ] Practical significance is stated in domain units: crashes, delay, cost, risk, time, emissions, capacity, accuracy, false alarms, or compute.
- [ ] Baselines are fair, current, and appropriate for the venue.
- [ ] Negative, null, or mixed results are not hidden.
- [ ] The discussion does not claim causality from association unless the design supports causal inference.

## Limitations

- [ ] Limitations are specific enough to guide future work.
- [ ] Statistical uncertainty, measurement error, confounding, selection bias, and external validity are separated.
- [ ] The paper states where the method should not be used.
- [ ] Generalization is limited to the studied population, roadway context, data source, model family, or benchmark.
- [ ] Safety and equity implications are discussed when results affect road users or deployed systems.

## Ethics and AI Use

- [ ] The venue's AI-use policy is checked before submission.
- [ ] AI assistance in writing, coding, analysis, or figure generation is disclosed if required.
- [ ] No confidential, identifiable, or restricted data were entered into unauthorized AI tools.
- [ ] Human-subjects, IRB, consent, or exemption status is stated when relevant.
- [ ] Dataset licenses, model licenses, and third-party figure permissions are checked.
- [ ] The paper does not include hidden prompts, invisible text, or reviewer-targeted instructions.

## Reproducibility

- [ ] Code availability is stated.
- [ ] Data availability is stated.
- [ ] Package versions, software versions, random seeds, hardware, and compute budget are documented where relevant.
- [ ] Model checkpoints, prompts, hyperparameters, and preprocessing scripts are recorded.
- [ ] Tables and figures can be regenerated from the documented analysis workflow.
- [ ] Restricted artifacts have a clear access procedure or explanation.

## Writing and Structure

- [ ] Acronyms are defined on first use and used consistently.
- [ ] Terminology, notation, variable names, and formatting are consistent.
- [ ] Paragraphs are focused and usually stay below 200 to 250 words.
- [ ] The conclusion summarizes contribution, evidence, implication, and limitation without excessive statistical detail.
- [ ] The manuscript follows the required template, page limit, and section order.

## Figures, Tables, Equations, and References

- [ ] Every figure and table is referenced and interpreted in the text.
- [ ] Captions are self-contained enough for review.
- [ ] Axes, units, legends, color scales, sample sizes, and uncertainty markers are readable.
- [ ] Equations are numbered when referenced.
- [ ] Variables in equations are defined.
- [ ] References are complete, real, and formatted for the venue.
- [ ] In-text citations match the reference list.
- [ ] The final PDF has no broken cross-references, missing fonts, or layout errors.
