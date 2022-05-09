# MLTRL Card example - Bayesian optimization algorithm - level 8

| Summary info        | Content, links       |
| -------------------------- | ------------- |
| Tech name (project ID)  | Dynamic Solar Array Optmization (P13.2) |
| Current Level           | 8 (*link to prior level cards*) |
| Owner(s)                | Alexander Lavin                           |
| Reviewer(s)             | Eric Xing, Dava Newman                    |
| Main project page       | (*link to e.g. team's internal wiki page*)   |
| Req's, V&V docs         | (*link, if not on main page above*)   |
| Code repo & docs        | (*link to Github etc*)   |
| Ethics checks?          | Yes: *link to completed [checklist](../ethics_checklist.md)*   |
| Coupled components      | R02.1, P12.2         |


**TL;DR** — Applying our MVBO algorithm in a systems optimization context, specifically to deploy with a new (greenfield) solar array control system, running in both live/production and shadow/simulated settings.


### Top-level requirements

*links to full product requirements doc (and the R&D requirements doc if applicable from earlier levels)*

1. The MVBO algorithm shall run efficiently and reliably as a module in the broader industrial control system.
2. The optimization module shall continuously validate and deploy both production and shadow instances.
3. The MVBO algorithm and broader optimization module shall test for, be robust against, and log and shifts in data, environment, or other operations.
4. The control system optimzation scheme shall be resilient to faults and intrusions (internally and externally).
5. The optimization module shall have a total runtime less than 5% of the end-to-end control software pipeline.
6. The optimization module shall have a fallback/bypass mode in case of unforseen failure.

**Extra notes**: More product requirements for the specific customer deployments and/or distribution channels, not listed here in the interest of space.


### Model / algorithm info


![Alt text](example-BO-flowchart.png?raw=true "Solar array optimization flowchart")


**Extra notes**: See previous Cards for details on MVBO


### Intended use

Closed-loop contrained optimization of industrial control system that operates the positioning (i.e. actuation) of solar panels in a given array/field. Extensive V&V testing must be done in simulation with real data and synthetic data prior to live deployment.

**Extra notes**: At this advanced MLTRL stage there should be product datasheet/whitepaper that elucidates the use-cases.

### Testing status

The following should be implemented and running (with visible status indicators and continuous logs):

1. CI/CD test suite implementation and status page
2. Cyber-physical systems tests for device and network bandwiths/latencies
3. Optimization module's shadow testing suite
4. Optimization module's testing suite for environment/data shifts


### Data considerations

Production data should be assumed to be specific to each deployment / environment, even with our domain randomization techniques. This also holds for the synthetic datasets, which are generated based on a limited set of real data.
If there is not sufficient data to validate the optimization module ahead of a given deployment, we can ship the control system software with the module in "pass through" mode such that we can start acquiring real system-specific data and release MVBO features in later updates.

### Caveats, known edge cases, recommendations

In very rare cases that we've only seen in (intentionally challenging) simualted scenarios, the optimization module will try to shift half the solar field m degrees and the other half n degrees, and then back again on the next control loop. Simply adding random noise to several of the actuators eliminates this scenario without affecting performance metrics.

### MLTRL stage debrief

<!-- Succinct summary of stage progress – please respond to each question, link to extended material if needed... -->

1. What was accomplished, and by who?

    Containerization and integrastion of the optimization subsystem into a production-ready software module.

2. What was punted and/or de-scoped?

    n/a

3. What was learned?

    Runtime of optimization module is insignificant relative to the broader control software system :) although most of the CI/CD testing is focused on optmization scenarios and robustness.

4. What tech debt what gained? Mitigated?

    Potentially mitigated by containerizing the optimization subsystem such that we may release it as an independent packge for open-source (and thus gain feedback from external use-cases). Note that open-sourcing is in the backlog for this project (i.e. this solar-opt epic on jira).

---
