# MLTRL Cards

In the ML/AI Technology Readiness Levels framework ([Lavin et al. '21](https://arxiv.org/abs/2101.03989)), the maturity of each ML technology is tracked via "report cards" called *MLTRL cards*. As a given technology or project proceeds through the framewark, a Card evolves corresponding to the progression of technology readiness levels. Cards provide a means of inter-team and cross-functional communication. Where the systems engineering framework itself defines a lingua franca for ML development and adoption, these *MLTRL cards* are like a [pilot's flight plan](https://en.wikipedia.org/wiki/Flight_plan) (and the MLTRL ethics checklist is like the pilot *and* crew [preflight checks](https://pilotinstitute.com/pre-flight-checks/)).

The content of an MLTRL Card is roughly in two categories: project info, and implicit knowledge. The former clearly states info such as project owners and reviewers, development status, datasets, code and deployment characteristics, and semantic versioning (for code, models and data). In the latter category, Cards communicate specific insights that are typically siloed in the ML development team but should be transparent with other stakeholders: modeling assumptions, dataset biases, corner cases, etc. These critical details can be incomplete or ignored if Cards are treated as typical software documentation afterthoughts, and thus should be prioritized in project workflows; in MLTRL, Cards are key for progressing to subsequent development levels.

the aim is to promote transparency and trust, within teams and across organizations.

Here we incude a template for MLTRL practitioners to copy/fork for use in their projects, teams, organizations, and so on. Please refer to the full paper for more details and context, and cite the journal publication where appropriate: (todo: replace with DOI on publication) [arxiv.org/abs/2101.03989](https://arxiv.org/abs/2101.03989).

The best subtrates/platforms for MLTRL Cards we've seen are git-traceable markdown (as in this repo) and internal company docs on platforms such as Nuclino and Confluence. These exemplify several **necessary features of whatever tool you choose: Card provenance, cross-linking with users and pages, and living/editable doc that mitigates stagnation.**


### Comparisons

MLTRL Cards aim to be more information-dense than recent comparisons; we're aiming for the utility of datasheets for medical devices and engineering tools, rather than high-level product whitepapers.

Recent ["ML model cards"](arxiv.org/abs/1810.03993) are related but are not nearly as thorough and robust — from a [Google Cloud blog post](https://cloud.google.com/blog/products/ai-machine-learning/google-cloud-ai-explanations-to-increase-fairness-responsibility-and-trust): `"Our aim with these first model card examples is to provide practical information about models' performance and limitations in order to help developers make better decisions about what models to use for what purpose and how to deploy them responsibly."`

Additional ML model card comparisons:

- [Tensorflow Model Card Toolkit](https://github.com/tensorflow/model-card-toolkit)
- [🤗-Building a model card](https://huggingface.co/course/chapter4/4?fw=pt)
- GPT2 examples: [HuggingFace](https://huggingface.co/gpt2) and [OpenAI](https://github.com/openai/gpt-2/blob/master/model_card.md)

The HuggingFace GPT2 example is the closest to the MLTRL Card deliverable: clean yet detailed, actual examples that are informative towards practical use (rather than simplistic Google card 'results'), versioned and taggable.


### Complements

MLTRL Cards should leverage other community tools (documentation, provenenance, etc.) where beneficial. For instance, **datasets** should have their own "datacards", which we don't specify (yet) in MLTRL.

- Google's "Datasheets for Datasets" ([paper](https://arxiv.org/abs/1803.09010), [template](https://research.google/static/documents/datasets/crowdsourced-high-quality-colombian-spanish-es-co-multi-speaker-speech-dataset.pdf)) — it is straightforward to follow this practice within the context of MLTRL. (Note that Microsoft also provides a version, but in a format that is less implementable and transparent as a deliverable: [MS Datasheets for Datasets](https://www.microsoft.com/en-us/research/project/datasheets-for-datasets/))
- Semantic versioning for datasets, prescribed in MLTRL, is becoming a standard practice and supported by many tools: for example, one can easily coordinate datacards and MTRL Cards with [DVC](https://dvc.org/) (including programmatic tools for keeping track with data commits/tags and data artifacts/registries).
- Data accountability, ethics, and overall best-practices are constantly evolving areas that should be tracked, potentially for incorporating new methods into MLTRL, and potentially for MLTRL learning lessons to inform the field. [Hutchinson et al. '21](https://arxiv.org/abs/2010.13561) is a good place to start.

<!-- #### Domain expert consortiums

- Rivera et al.[76]: calling for clinical trials reports for interventions involving AI – which will greatly benefit from the use of our TRL
reporting cards.
- more...
 -->

---


## Card Outline

It's useful to view the Card contents in the context of real example Cards: [Level 4 BayesOpt Card](examples/mltrl_card_BO_level4.md)

### Card content

> First is a quick summary table...

- Tech name, project ID
- Current level
- Owner(s)
- Reviewer(s)
- link to main project page (in company wiki, for example)
- link to code, documentation
- link to ethics checklist

> Then we have more details...

#### Top-level requirements

A quick view of the main req's is very handy for newcomers and stakeholders to quickly grok the tech and development approach. The req's listed here will be top-level, i.e. referenced with integers 1, 2, 3, ... aligned with the full project req's document, which follows the format `requirement number.subset.component`.

Then there will be link(s) to full requirements + V&V table; refer to the main manuscript to see how MLTRL defines *research-* and *product-requirements*, and the use of verification and validation (V&V).

#### Model/algorithm info

Concise "elevator pitch" — think from the perspective of a MLTRL reviewer who may be a domain expert but not skilled in ML.

#### Intended use

This can have mission-critical information and should clearly communicate what, how, why of intended *and* unacceptable use-cases. In general this section is most verbose at the early stages of commercialization (Levels 5-8).

#### Testing status

What's tested algorithmically? How is the code/implementation tested? What testing recommendations should be acted on in other MLTRL stages?

#### Data considerations

1. Refer to the MLTRL manuscript for level-by-level data specs.
2. Highlight important/interesting data findings — for example, class imbalances, subpar labels, noise and gaps, acquisition assumptions, etc.
3. Point to specific datasets in use (internal and external sources) and data versioning info.
4. Explain precisely what data and conditions a model has been trained and developed on.

Note this section's content, amongst others, can vary significantly depending on the ML model or algorithm and the domain. For instance, this section can be verbose with examples for image models, but not necessarily for time series algorithms. And in fields such as medicine there should be notes on acquisition, sharing, privacy, and ethics that may not be as significant in e.g. manufacturing.

#### Caveats, known edge cases, recommendations

Additional notes to highlight — for example, this is a good place to call out potential biases, technical or knowledge debt, and other matters to be considered in later stages.


#### MLTRL stage debrief

Succinct summary of stage progress, in a question-response format that is specified at review time (or using defaults like those in the [MLTRL Card examples](examples/).
