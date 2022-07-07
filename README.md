# Machine Learning Technology Readiness Levels

Repository for the MLTRL framework and materials. [![DOI](https://zenodo.org/badge/511701165.svg)](https://zenodo.org/badge/latestdoi/511701165)

![Alt text](assets/mltrl_flow_full.png?raw=true "MLTRL Flow")


The development and deployment of machine learning (ML) systems can be executed easily with modern tools, but the process is typically rushed and means-to-an-end. The lack of diligence can lead to technical debt, scope creep and misaligned objectives, model misuse and failures, and expensive consequences. Engineering systems, on the other hand, follow well-defined processes and testing standards to streamline development for high-quality, reliable results. The extreme is spacecraft systems, where mission critical measures and robustness are ingrained in the development process. Drawing on experience in both spacecraft engineering and ML (from research through product across domain areas), we have developed a proven systems engineering approach for machine learning development and deployment: *Machine Learning Technology Readiness Levels (MLTRL)* framework defines a principled process to ensure robust, reliable, and responsible systems while being streamlined for ML workflows, including key distinctions from traditional software engineering. MLTRL further defines a lingua franca for people across teams and organizations to work collaboratively on artificial intelligence and machine learning technologies.

See the main paper ["Technology Readiness Levels for Machine Learning Systems"](https://arxiv.org/abs/2101.03989) (in-press) for details on the framework and results in areas including ML for medical diagnostics, consumer computer vision, satellite imagery, and particle physics.



## MLTRL Cards

Here we incude a template for MLTRL practitioners to copy/fork for use in their projects, teams, and organizations: [MLTRL Card](mltrl_card.md).
We also provide several real-world example Cards, and welcome others to be submitted via pull request.

Please see the MLTRL journal paper for details on Card implementation and utilities.


## AI Ethics Guide

The MLTRL framework frequently calls on ethics policies to ensure safe and responsible technolgies.

Here we include a thorough AI ethics guide for all to use, and adapt to your domain as needed: (local link to ethics_checklist.md)

Note the recent develoment of community guidelines for AI publishing has resulted in a handful of industry-specific checklists. We list those that we know of here (and accept contributions from the community):

- [MI_CLAIM (Minimum Information for CLinical AI Modeling)](https://github.com/beaunorgeot/MI-CLAIM)
- [Checklist for Artificial Intelligence in Medical Imaging (CLAIM)](https://pubs.rsna.org/doi/10.1148/ryai.2020200029)
- *TODO: more?*


## MLTRL resources

Please submit additional materials via pull request, thanks.

### Talks:

- 2022 @ MIT Media Lab (TODO)
- [2022 @ Immunai](assets/mltrl-immunai22.pdf)
<!-- - 2021 @ AAAI; Lavin, "" -->
<!-- - 2021 @ Cambridge; Lavin, "" -->

### Papers:

- **[Lavin et al. '21, *TRL for ML Systems*](https://arxiv.org/abs/2101.03989)**
- [Lavin & Renard '21, *TRL for AI&ML*](https://arxiv.org/abs/2006.12497)
- [Paleyes et al. '22, *Challenges in Deploying Machine Learning: a Survey of Case Studies*](https://dl.acm.org/doi/10.1145/3533378)


## Citations

If you use MLTRL and/or develop related methods, please cite our work as follows:
```
@article{Lavin22NatureComms,
  title={Technology Readiness Levels for Machine Learning Systems},
  author={Alexander Lavin and Ciar{\'a}n M. Gilligan-Lee and Alessya Visnjic and Siddha Ganju and Dava Newman and Atilim Gunes Baydin and Sujoy Ganguly and Danny B. Lange and Ajay Sharma and Stephan Zheng and Eric P. Xing and Adam Gibson and James Parr and Chris Mattmann and Yarin Gal},
  journal={ArXiv},
  year={2021},
  volume={abs/2101.03989}
}
```
