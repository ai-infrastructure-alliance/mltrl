# MLTRL Card example - Bayesian optimization algorithm - level 4

| Summary info        | Content, links       |
| -------------------------- | ------------- |
| Tech name (project ID)  | Mixed-variable BO (R02.1)[^1]   |
| Current Level           | 4 (*link to prior level cards*) |
| Owner(s)                | Gunes Baydin                        |
| Reviewer(s)             | Yarin Gal                           |
| Main project page       | (*link to e.g. team's internal wiki page*)   |
| Req's, V&V docs         | (*link, if not on main page above*)   |
| Code repo & docs        | (*link to Github etc*)   |
| Ethics checks?          | WIP: *link to MVBO [checklist](../ethics_checklist.md)*   |


[^1]: Note the ID convention shown is arbitrary — we use `R` for research, `02` for some index on the team's projects, and `1` for a version of the project.

**TL;DR** — MVBO is a novel Bayesian optimization (BO) algorithm for the efficient optimization of mixed-variable functions (which may represent a real-world system, data-driven model, or other parameterized process).


### Top-level requirements

*Link to full [R&D requirements doc](); there is not yet a product req's doc.*

1. The algorithm shall jointly optimize discrete and continuous variables.
2. The BO approach shall be useful for hyperparameter optimization of data-driven models.
3. The BO approach shall effectively model and tune mechanistic equations (of physical systems).
4. The algorithm shall have a total runtime at least 1-2 order of magnitude faster than the end-to-end system/function.
5. The method shall be transparent to surface info such as quantified uncertainties, bounds, etc.

**Extra notes**: Req's are intentionally succinct and specific to the mixed-variable alg variant we're developing, ignoring generic BO items that are well-studied/validated.


### Model / algorithm info

A Bayesian optimization (BO) algorithm — a probabilsitic scheme for finding optimal parameters of a typically black-box, expensive function or system — but modified for mixed-variable settings: Our variation "mixed-variable BO" (MVBO) is for settings that have both discrete and continuous variables to optimize.

Implementation notes:

- Gaussian process surrogate model, with standard RBF kernel
- Thompson sampling scheme, which we run until converging to a local optimum
- Implementation leverages the standard BO libraries GPyTorch and BoTorch.

**Extra notes**: Our working definition of Bayesian Optimization (BO): The objective is to select and gather the most informative (possibly noisy) observations for finding the global maximum of an unknown, highly complex (e.g., non-convex, no closed-form expression or derivatives) objective function modelled by a GP given a sampling budget (e.g., number of costly function evaluations). The rewards (informativeness measure) are defined using an improvement-based (e.g. probability of improvement or expected improvement over currently found maximum), entropy-based, or upper confidence bound (UCB) acquisition function.


### Intended use

- Optimize the parameters of an expensive, black-box function `f` with constraints.
- This algorithm is specifically useful when `f` is mixed-variable: contains both discrete and continuous variables to optimize.
- ML model parameter tuning is a common example for BO. With this MVBO we can tune the hyperparameters of a convnet: continuous variables (e.g. learning rate, momentum) and discrete variables (e.g. kernel size, stride, padding), subject to constraints – some combos of kernel/stride/padding lead to invalid networks.
- Other applications include optimization in sensor placement / array design.

**Extra notes**: MVBO use-cases are still exploratory, as this began at Level 1 without a specific application area in mind.


### Testing status

- Low-level tests verify the algorithm can find solutions for simple mixed-variable functions
- Tests verify the algorithm converges for standard BO problems
- There are several unit tests on the BO loop, but more are needed (notably for diverse parameter sets)

**Extra notes**: Base BO tests are assumed valid from the source BoTorch and GPyTorch repositories


### Data considerations

Benchmark experiments have been run on standard optimization benchmarks, e.g. Branin Hoo

Links to full [product requirements doc]() and the [R&D requirements doc]() if applicable from earlier levels.

**Extra notes**: none


### Caveats, known edge cases, recommendations

- We have not yet run experiments to fully understand the algorithm relative to other BO components – e.g. GP vs RF as surrogate models.
- For most BO problems you are best off starting with default algorithms (see BoTorch)


### MLTRL stage debrief

<!-- Succinct summary of stage progress – please respond to each question, link to extended material if needed... -->

1. What was accomplished, and by who?

    Investigated the algorithm's fundamental properties for efficiently navigating solution spaces of BO benchmark problems of mixed-variable domains. Codebase refactored to (1) follow spec and extend industry standard libs BoTorch and GPyTorch, and (2) include automated unit test suite. See *link to experiments page w/ plots*.

2. What was punted and/or de-scoped?

    n/a

3. What was learned?

    - Algorithm behaves similar to two (coupled) EI acquisition functions.
    - Convergence properties satisfied, on par w/ existing BO algorithms for computational efficiency: *link to notebook of results*.

4. What tech debt what gained? Mitigated?

    - Moved code from team sandbox (research-caliber) to mainline R&D repo, with sufficient unit tests (over MVBO), integration tests (with BoTorch and GPyTorch), and lightweight synthetic test data generators.

---
