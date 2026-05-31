---
layout: page
title: Research
permalink: /research/
description: Bayesian and causal machine learning for healthcare data.
nav: true
nav_order: 1
---

I am a PhD candidate in Biomedical AI at the University of Edinburgh, working with [Dr Sohan Seth](https://sohanseth.github.io/) at the [Data Science Unit](https://web.inf.ed.ac.uk/data-science-unit). My research sits at the intersection of **Bayesian modelling**, **semi-supervised and causal machine learning**, and **healthcare**, with a more recent line of work on **efficient inference for large language models**. I am drawn to interpretable methods that recover meaningful subgroups from high-dimensional or longitudinal data, identify the factors that drive those subgroups, and understand how interventions move them along.
{: .text-justify}

Four threads run through my work to date.

## Scalable, interpretable and robust Bayesian semi-supervised clustering

Real-world tabular and image data are often high-dimensional, only partially labelled, and noisy in unpredictable ways. The most common Bayesian clustering methods either do not scale or treat every pairwise constraint as ground truth. My ICML 2026 paper introduces **BASIL**, a scalable Bayesian semi-supervised clustering framework that combines a Hidden Markov Random Field formulation with stochastic variational inference, while jointly learning cluster-specific feature relevance and adaptively down-weighting unreliable supervision. BASIL trains efficiently on settings ranging from MNIST digit benchmarks to ChestMNIST medical imaging and a 501k-patient UK CPRD multimorbidity cohort, where metric-learning baselines fail to converge in over two days. It remains robust under up to 30% noisy constraints.
{: .text-justify}

- **Paper.** Scalable Bayesian Semi-supervised Clustering with Feature Selection and Adaptive Constraint Weighting, ICML 2026. *To appear.*
- **Project page.** [BASIL](https://demi-wlw.github.io/BASIL-Scalable-Bayesian-Semi-supervised-Clustering/)
- **Code.** [GitHub](https://github.com/Demi-wlw/BASIL-Scalable-Bayesian-Semi-supervised-Clustering)
- **Talks.** ICML 2026 (forthcoming).

## Supervised causal clustering for heterogeneous treatment effects

Clinical trials often report no average benefit when in fact a benefit exists for a specific subpopulation, and unsupervised clustering of patient covariates rarely surfaces those subpopulations cleanly. My recent preprint introduces **Bayesian Supervised Causal Clustering (BSCC)**, a framework that uses individual treatment effect as the outcome guiding the clustering process. BSCC recovers homogeneous subgroups whose members are similar both in their covariate profiles and in how they respond to treatment, giving clinicians and trialists subgroups that are operationalisable rather than merely statistical. I evaluated BSCC on simulated benchmarks and on real-world data from the third International Stroke Trial.
{: .text-justify}

This thread builds on earlier work I did as a research assistant on a Turing-funded project, where I evaluated supervised metric-based clustering for recovering subphenotypes of critically ill COVID-19 patients under convalescent plasma treatment. That project introduced a "FavorCP" outcome that improved odds-ratio testing across discovered subgroups, and motivated the move to a fully Bayesian, causal formulation in BSCC.
{: .text-justify}

- **Paper.** [Bayesian Supervised Causal Clustering, arXiv 2026](https://arxiv.org/abs/2603.05288)
- **Earlier project.** [Supervised Clustering of Critically Ill Patients](/projects/supervisedClust/)

## Interpretable clustering of multi-faceted time series

Real-world time series rarely live in a single facet. Patient histories, like most longitudinal data, carry trend, seasonality, regime changes, and event sequences at once, and treating them as a single signal collapses the structure that clinicians actually care about. My UAI 2025 paper introduces a **nonparametric Bayesian framework that learns a separate clustering for each facet simultaneously**, using variational inference to scale to real cohorts. Applied to the English Longitudinal Study of Ageing, it recovers interpretable subgroups that single-facet models miss.
{: .text-justify}

- **Paper.** [Nonparametric Bayesian Multi-Facet Clustering for Longitudinal Data, UAI 2025](https://proceedings.mlr.press/v286/wang25c.html)
- **Code.** [GitHub](https://github.com/Demi-wlw/Nonparametric-Bayesian-Multi-Facet-Clustering-for-Longitudinal-Data)
- **Poster.** [UAI 2025](/assets/pdf/Poster__NPBayes_MultiFacet_Clustering.pdf)
- **Talks.** UAI 2025 poster, [UKAIRS 2025](https://www.ukairs.ac.uk/ukairs-programme/) oral, Joint CDT Conference on AI for Healthcare 2025 oral.
- **Background reading.** [The real-world data are multi-faceted](/blog/2025/Multi-facet/)

## Disease trajectories in multimorbidity

Multimorbidity, the co-existence of two or more chronic conditions, is increasingly the norm rather than the exception, and care models designed for a single disease break down for these patients. Most existing analyses are cross-sectional. Far fewer take the **temporal order** of disease onset seriously. My MSc dissertation, conducted with the Data Science Unit, used temporal clustering to surface meaningful patterns of how multiple conditions accumulate over time, and to link those patterns to outcomes such as mortality. This thread shapes the longitudinal modelling questions I continue to pursue in the PhD.
{: .text-justify}

- **Project page.** [Clustering Individual Trajectories of Multiple Long-Term Conditions](/projects/clustTrajMLTC/)

## Where I'm heading

A common thread runs through these projects. I want to build **interpretable models under uncertainty**, models that a domain expert can act on while honestly representing what the data does and does not support. I'm increasingly drawn to causal machine learning as the natural next step, moving from asking *which patients look alike* to asking *which interventions change which patients' trajectories, and why*. I have also been pulled toward the inference side of large language models. A co-authored **ICML 2026** paper develops Adaptive Sequential Monte Carlo with cache-coherent resampling for training-free LLM test-time scaling, and I am interested in how Bayesian thinking can sharpen reasoning under compute budgets.
{: .text-justify}

The fastest way to reach me about research is by [email](mailto:luwei.wang@ed.ac.uk).
