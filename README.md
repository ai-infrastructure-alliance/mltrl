# MLTRL Cards

In the ML Technology Readiness Levels framework [Lavin et al. '21](https://arxiv.org/abs/2101.03989), the maturity of each ML technology is tracked via "report cards" that grow and improve upon graduating levels, and provide a means of inter-team and cross-functional communication. Where the systems engineering framework itself defines a lingua franca for ML development and adoption, these *MLTRL cards* are like a [pilot's flight plan](https://en.wikipedia.org/wiki/Flight_plan) (and the MLTRL ethics checklist is like the pilot *and* crew [preflight checks](https://pilotinstitute.com/pre-flight-checks/)).

The content of an MLTRL card is roughly in two categories: project info, and implicit knowledge. The former clearly states info such as project owners and reviewers, development status, and semantic versioning—not just for code, also for models and data. In the latter category are specific insights that are typically siloed in the ML development team but should be communicated to other stakeholders: modeling assumptions, dataset biases, corner cases, etc.
MLTRL cards aim to be more information-dense than [comparisons](#comparisons-and-complements), like datasheets for medical devices and engineering tools, and should be prioritized for the progression of projects, rather than documentation afterthoughts; the aim is to promote transparency and trust, within teams and across organizations.

Here we incude a template for MLTRL practitioners to copy/fork for use in their projects, teams, organizations, and so on. Please refer to the full paper for more details and context, and cite the journal publication where appropriate: (todo: replace with DOI on publication) [arxiv.org/abs/2101.03989](https://arxiv.org/abs/2101.03989).


### Comparisons and complements

Recent ["ML model cards"](arxiv.org/abs/1810.03993) are related but not as all-encompassing... [Blog post](https://cloud.google.com/blog/products/ai-machine-learning/google-cloud-ai-explanations-to-increase-fairness-responsibility-and-trust) from Tracey Frey, Director of Strategy, Google Cloud AI: "Our aim with these first model card examples is to provide practical information about models' performance and limitations in order to help developers make better decisions about what models to use for what purpose and how to deploy them responsibly."

ML model card comparisons:
    - https://github.com/tensorflow/model-card-toolkit
    - https://huggingface.co/course/chapter4/4?fw=pt
    - GPT2 examples: https://huggingface.co/gpt2 and https://github.com/openai/gpt-2/blob/master/model_card.md

(The huggingface gpt2 example is the closest to the TRL Card deliverable: clean yet detailed, actual examples that are information rather than Google card fluff, versioned and taggable.)

MLTRL Cards should leverage other community tools (documentation, provenenance, etc.) where beneficial. For instance, **datasets** should have their own "datacard", which we don't specify (yet) in MLTRL.
    - Google does well here with Datasheets for Datasets ([paper](https://arxiv.org/abs/1803.09010), [template](https://research.google/static/documents/datasets/crowdsourced-high-quality-colombian-spanish-es-co-multi-speaker-speech-dataset.pdf)), and it would be straightforward to follow suit. (Microsoft also provides a version, but in a format that is less implementable and transparent as a deliverable: https://www.microsoft.com/en-us/research/project/datasheets-for-datasets/)
    - MLTRL prescribes semantic versioning for datasets... doable to coordinate datacards w/ DVC (data commits/tags and data artifacts/registries)?
    - Following data accountability best-practices as they evolve: https://arxiv.org/abs/2010.13561.


Similarly, within MLTRL there are additional tools and deliverables that MLTRL Cards link to, namely for **ethics**: (link to "ML ethics checklist" section/page/repo).


#### Domain expert consortiums

- Rivera et al.[76]: calling for clinical trials reports for interventions involving AI – which will greatly benefit from the use of our TRL
reporting cards.
- more...


---


## Card Outline

### Card content

> First is a quick summary table...

- Tech name
- Current level
- Owner(s)
- Reviewer(s)
- link to main project page (in company wiki, for example)
- link to code, documentation
- link to ethics checklist

> Then we have more details...

#### Top-level requirements

(Be sure to see how MLTRL defines *research-* and *product-requirements*, and the use of verification and validation (V&V).)

1. The algorithm shall jointly optimize discrete and continuous variables.
2. The BO approach shall be useful for hyperparameter optimization.
3. ...

Link to full req's + V&V table.

#### Model/algorithm info

Bayesian Optimization (BO)1 algorithm:
    - Gaussian process surrogate model, with standard RBF kernel
    - Thompson sampling scheme, which we run until converging to a local optimum
Implementation leverages GPyTorch and BoTorch.

#### Intended use

- Optimize the parameters of an expensive, black-box function `f` with constraints.
- This algorithm is specifically useful when `f` is mixed-variable: contains both discrete and continuous variables to optimize.
- ML model parameter tuning is a common example for BO. With this MVBO we can tune the hyperparameters of a convnet: continuous variables (e.g. learning rate, momentum) and discrete variables (e.g. kernel size, stride, padding), subject to constraints – some combos of kernel/stride/padding lead to invalid networks.
- Other applications include optimization in sensor placement / array design.

#### Testing status

Low-level tests verify the algorithm can find solutions for simple mixed-variable functions Tests verify the algorithm converges for standard BO problems
There are several unit tests on the BO loop, but more are needed

#### Data considerations

Benchmark experiments have been run on standard optimization benchmarks, e.g. Branin Hoo

(Note this section is much more important with image models! We’ll want to explain precisely what data and conditions a model has been trained on.)

#### Caveats, known edge cases, recommendations

- We have not yet run experiments to fully understand the algorithm relative to other BO components – e.g. GP vs RF as surrogate models.
- For most BO problems you are best off starting with default algorithms (see BoTorch)
