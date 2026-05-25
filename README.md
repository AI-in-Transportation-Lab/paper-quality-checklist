# Paper Quality Checklist

Compact submission checks for AIT Lab papers before journal, conference, or workshop submission.

Use this repository as a final review workflow, not as a writing handbook. Each item should be answered directly in the manuscript, cover letter, supplement, code repository, or response plan.

## Quick Start

1. Run the [Universal Checklist](docs/universal-checklist.md).
2. Select the closest venue family in [Venue Checklists](docs/venue-checklists.md).
3. Run the [Statistical Test Checklist](docs/statistical-test-checklist.md) if the paper reports empirical, experimental, simulation, survey, crash, model-comparison, or ML results.
4. Finish with the [Final Submission Gate](docs/final-submission-gate.md).

## Quick Submission Gate

- [ ] The target venue is named correctly and the paper fits its scope.
- [ ] The contribution can be stated in one precise sentence.
- [ ] Every major claim is supported by a result, citation, proof, or limitation.
- [ ] The method, data, and evaluation choices match the research question.
- [ ] Figures, tables, equations, citations, and references are complete and cross-referenced.
- [ ] Statistical tests, model choices, uncertainty, and effect sizes are reported where needed.
- [ ] Reproducibility status is clear: data, code, prompts, environment, seeds, and restrictions.
- [ ] Ethics, privacy, safety, AI use, and conflicts of interest are handled according to the venue.
- [ ] The final PDF was compiled from the submission source and manually reviewed.

## Universal Paper Quality Checklist

- [ ] Title states the topic and contribution without overclaiming.
- [ ] Abstract includes problem, gap, method, data, main result, and implication.
- [ ] Introduction separates motivation, research gap, contribution, and paper organization.
- [ ] Literature review explains what prior work cannot answer, not only what it did.
- [ ] Methods are specific enough for a skilled reader to reproduce or audit.
- [ ] Results answer the stated research questions in the same order they are introduced.
- [ ] Discussion connects findings to transportation, computing, policy, safety, or engineering practice.
- [ ] Limitations distinguish data limits, model limits, causal limits, and external validity limits.
- [ ] Conclusion stays broad and does not repeat detailed coefficients or table values.

## Venue Family Selector

- Transportation engineering: use when the contribution is a transportation, safety, operations, planning, infrastructure, mobility, ITS, or policy contribution.
- ACM computing: use when the contribution is primarily computing, systems, HCI, data mining, retrieval, networking, or software/method artifact quality.
- Major CS/AI conferences: use when the contribution is primarily ML, AI, vision, NLP, data mining, or algorithmic evaluation.
- Mixed AI-in-transportation papers: satisfy both the transportation relevance checks and the CS/AI evidence checks.

## Final 24-Hour Checks

- [ ] Search the final PDF for `error`, `??`, `undefined`, missing references, and broken citations.
- [ ] Search every figure, table, algorithm, appendix, and equation number in the text.
- [ ] Check that every acronym is defined once and used consistently.
- [ ] Open the PDF on another machine or viewer and inspect fonts, margins, captions, and equations.
- [ ] Confirm author names, affiliations, acknowledgments, funding, and conflicts of interest.
- [ ] Confirm the submitted files match the final internal version.

## Repository Map

- [Universal checklist](docs/universal-checklist.md)
- [Venue-family checklists](docs/venue-checklists.md)
- [Statistical test checklist](docs/statistical-test-checklist.md)
- [Final submission gate](docs/final-submission-gate.md)
