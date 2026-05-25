# Paper Quality Checklist

Pre-submission review workflow for AIT Lab. Run in order; each step links to the detailed doc.

---

## Workflow

```
Step 1  ->  Universal Checklist      (every paper)
Step 2  ->  Venue Checklist          (pick your venue)
Step 3  ->  Statistical Checklist    (any paper with data, models, or experiments)
Step 4  ->  ML Model Selection       (if proposing or comparing ML/DL models)
Step 5  ->  Causal Inference         (if claiming a causal effect or guiding policy)
Step 6  ->  Final Submission Gate    (24 h before submit)
```

---

## TXST Open Access APC Note

Before choosing a paid open-access option, check the [TXST University Libraries open publishing agreements FAQ](https://askalibrarian.library.txstate.edu/faq/371997). TXST has negotiated open-access publishing agreements and discounts; eligible corresponding authors may have APCs covered or reduced for covered publishers and journals.

Important checks:

- [ ] Use the TXST institutional email and affiliation for the corresponding author when the publisher workflow asks for eligibility.
- [ ] Confirm the current agreement, article type, license, and journal coverage before submission; publisher agreements can change.
- [ ] For ACM venues, check ACM Open eligibility. ACM states that corresponding authors from participating institutions can publish eligible articles open access in ACM journals, proceedings, and magazines at no cost to the authors.
- [ ] Do not pay an APC until the library or publisher workflow confirms whether the article is covered.

Relevant TXST-covered Springer Nature titles to consider for AIT Lab work:

| Area | Journal |
|---|---|
| Computer vision / multimodal systems | [Machine Vision and Applications](https://link.springer.com/journal/138) |
| AI and society | [AI & SOCIETY](https://link.springer.com/journal/146) |
| Neural computing | [Neural Computing and Applications](https://link.springer.com/journal/521) |
| Human factors / work systems | [Cognition, Technology & Work](https://link.springer.com/journal/10111) |
| Knowledge systems | [Knowledge and Information Systems](https://link.springer.com/journal/10115) |
| AI theory / methods | [Annals of Mathematics and Artificial Intelligence](https://link.springer.com/journal/10472) |
| Applied AI | [Applied Intelligence](https://link.springer.com/journal/10489) |
| AI governance / law | [Artificial Intelligence and Law](https://link.springer.com/journal/10506) |
| Data mining | [Data Mining and Knowledge Discovery](https://link.springer.com/journal/10618) |
| Machine learning | [Machine Learning](https://link.springer.com/journal/10994) |
| Transportation | [Transportation](https://link.springer.com/journal/11116) |
| User modeling | [User Modeling and User-Adapted Interaction](https://link.springer.com/journal/11257) |
| Computer vision | [International Journal of Computer Vision](https://link.springer.com/journal/11263) |
| Multimodal interfaces | [Journal on Multimodal User Interfaces](https://link.springer.com/journal/12193) |
| Transportation security | [Journal of Transportation Security](https://link.springer.com/journal/12198) |
| Public transport | [Public Transport](https://link.springer.com/journal/12469) |
| Intelligent transportation | [International Journal of Intelligent Transportation Systems Research](https://link.springer.com/journal/13177) |
| AI methods | [Progress in Artificial Intelligence](https://link.springer.com/journal/13748) |
| Infrastructure / geotechnology | [Transportation Infrastructure Geotechnology](https://link.springer.com/journal/40515) |
| AI education | [International Journal of Artificial Intelligence in Education](https://link.springer.com/journal/40593) |
| Data science | [Annals of Data Science](https://link.springer.com/journal/40745) |
| Developing economies | [Transportation in Developing Economies](https://link.springer.com/journal/40890) |
| Transportation data science | [Data Science for Transportation](https://link.springer.com/journal/42421) |
| Human-AI systems | [Human-Intelligent Systems Integration](https://link.springer.com/journal/42454) |
| AI ethics | [AI and Ethics](https://link.springer.com/journal/43681) |

---

## Venue Quick Selector

Journal and venue finder tools:

- [Elsevier Journal Finder](https://journalfinder.elsevier.com/): match title, abstract, keywords, and field to Elsevier journals.
- [Springer Nature Journal Suggester](https://www.springer.com/gp/authors-editors/selecting-a-journal/1258): search Springer Nature journals and filter by scope and publishing model.
- [Wiley Journal Finder](https://www.wiley.com/en-gb/publish/journal-finder): search and compare Wiley journals.
- [IEEE Publication Recommender](https://publication-recommender.ieee.org/periodicals): find IEEE periodicals by keywords or abstract.
- [Sage Journal Recommender](https://journal-recommender.sagepub.com/): match a manuscript to Sage journals.
- [ACM Digital Library publications](https://www.acm.org/publications): browse ACM journals, proceedings, magazines, and publication policies.
- [Directory of Open Access Journals](https://doaj.org/): check fully open-access journals outside publisher-specific tools.

Special issue finder tools:

- [ScienceDirect Calls for Papers](https://www.sciencedirect.com/browse/calls-for-papers): browse Elsevier special issues and article collections with open calls.
- [Springer Nature Article Collections](https://www.springernature.com/gp/authors/publish-an-article/collections): find Springer Nature collections, topical collections, and special issues.
- [Wiley Special Issues](https://www.wiley.com/publish/special-issues): browse and submit to Wiley special issues.
- [IEEE Calls for Papers](https://www.computer.org/publications/author-resources/calls-for-papers): check IEEE Computer Society journal and magazine calls.
- [Sage Journal Recommender](https://journal-recommender.sagepub.com/): identify Sage journals, then check journal pages for active special issues.
- [Taylor & Francis Online](https://www.tandfonline.com/): search the target journal page for special issue, collection, and call-for-paper notices.

Special issue checks:

- [ ] The special issue is hosted on the official publisher or journal website.
- [ ] Guest editors, scope, article type, deadline, review process, and APC policy are clear.
- [ ] The topic fits the manuscript naturally; do not force a paper into a special issue only because the deadline is convenient.
- [ ] The special issue still uses normal peer review and does not promise unusually fast acceptance.
- [ ] TXST open-access coverage is checked before selecting an optional open-access route.

| Your paper | Target venues |
|---|---|
| Crash model, severity, safety countermeasure | AA&P, AMAR, TRR, TR-C |
| ITS, AV, traffic operations, ML in transportation | TR-C, IEEE T-ITS, ITSC, IV |
| Travel demand, network optimization, behavioral model | TR-B, Transportation Science |
| Environmental impact, emissions, energy | TR-D |
| Spatial data, mobility, trajectory, urban computing | ACM SIGSPATIAL, KDD |
| ML method, deep learning, representation learning | NeurIPS, ICLR, ICML |
| Broad AI: planning, reasoning, multiagent | AAAI, IJCAI |
| Computer vision, perception, AV sensing | CVPR, ICCV, ECCV |
| Robot learning, AV policy, sim-to-real | CoRL |
| NLP for transportation, report analysis | ACL, EMNLP |
| HCI, mobility apps, user studies | ACM CHI |

---

## Repository Map

| File | Purpose |
|---|---|
| [docs/universal-checklist.md](docs/universal-checklist.md) | Every paper, every venue |
| [docs/venue-checklists.md](docs/venue-checklists.md) | TR-B/C/D, AA&P, T-ITS, TRR, SIGSPATIAL, KDD, NeurIPS, ICLR, ICML, AAAI, CVPR, CoRL, ACL |
| [docs/statistical-test-checklist.md](docs/statistical-test-checklist.md) | Test selection, formulas ($H_0/H_1$), assumptions, effect sizes, ML comparison tests |
| [docs/ml-model-selection.md](docs/ml-model-selection.md) | Model choice, validation protocol, metrics, ablation, common failures |
| [docs/causal-inference.md](docs/causal-inference.md) | DAGs, DiD, IV, RDD, matching, sensitivity analysis |
| [docs/final-submission-gate.md](docs/final-submission-gate.md) | Final 24-hour pre-submission gate |

---

## Agents

Use these prompts with any LLM (ChatGPT, Claude, Gemini) to automate parts of the review. Paste the system prompt, then paste the relevant section of your manuscript.

| Prompt | Input | Output |
|---|---|---|
| [agents/full-paper-review.md](agents/full-paper-review.md) | Abstract + Methods + Results | Section-by-section issue list (CRITICAL / MAJOR / MINOR) |
| [agents/statistical-audit.md](agents/statistical-audit.md) | Methods (stats) + Results + Tables | Statistical validity report with fix suggestions |
| [agents/venue-fit.md](agents/venue-fit.md) | Abstract + contribution sentence | Top 3 venue recommendations with scores and rejection risks |

---

## Quick Submission Gate

- [ ] Venue name, track, and submission deadline are correct.
- [ ] Contribution fits venue scope and can be stated in one precise sentence.
- [ ] Every major claim has a result, citation, proof, or stated limitation.
- [ ] Statistics: correct test chosen, assumptions checked, effect size and CI reported.
- [ ] Reproducibility: data, code, seeds, environment, and access restrictions stated.
- [ ] Ethics, AI-use disclosure, conflicts of interest, and funding handled per venue policy.
- [ ] Final PDF compiled from clean source, searched for errors, and manually inspected page by page.
