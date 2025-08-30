---
layout: distill
title: The Real-World Data are Multi-faceted
description: Motivation for interpretable AI/ML models
date: 2025-08-30
giscus_comments: true
tags: machine-learning/AI
categories: site-posts
published: true
thumbnail: assets/img/MF.icon.png
featured: true
pretty_table: true

authors:
  - name: Luwei Wang
    affiliations:
      name: University of Edinburgh

#bibliography: 2025-03-19-ChatGPT.bib

# Optionally, you can add a table of contents to your post.
# NOTES:
#   - make sure that TOC names match the actual section names
#     for hyperlinks within the post to work correctly.
#   - we may want to automate TOC generation in the future using
#     jekyll-toc plugin (https://github.com/toshimaru/jekyll-toc).
toc:
  - name: Why Multi-facet for Complex Data?
  - name: What Is Multi-facet Clustering?
  - name: How Is It Different to Multi-view and Multi-assignment Clustering?

# Below is an example of injecting additional post-specific styles.
# If you use this post as a template, delete this _styles block.
_styles: >
  .fake-img {
    background: #bbb;
    border: 1px solid rgba(0, 0, 0, 0.1);
    box-shadow: 0 0px 4px rgba(0, 0, 0, 0.1);
    margin-bottom: 12px;
  }
  .fake-img p {
    font-family: monospace;
    color: white;
    text-align: left;
    margin: 12px 0;
    text-align: center;
    font-size: 16px;
  }
---

## Why Multi-facet for Complex Data?

Real-world data are often multi-faceted, particularly when dealing with complex and high-dimensional settings. To illustrate this, we take **time series data** as an example. In the figure below, the left panel shows individual income trajectories over time, while the right panel presents multiple time series for each person, capturing frailty, wellbeing, and social isolation.
{: .text-justify}

In the case of income trajectories, we might describe a person’s income as *“poor, stable but fluctuating”*. Such descriptions are determined by three key characteristics of a time series: *value, variation, and volatility*. In healthcare, however, individuals typically have multiple time series across their lives. The interesting characteristics here could include the *intercepts of variables, interactions between variables, the scale of each variable, and the noise in trajectories*.
{: .text-justify}

Importantly, these characteristics are not directly observed but are meaningful **hidden features** that shape the form of an observed trajectory. We refer to each such hidden characteristic as a **facet**. Within each facet, there can be several **specific clusters**. For example, in the *value* facet of income trajectories, clusters might correspond to different levels of income such as *“poor”, “comfortable”, or “luxury”*. This idea extends beyond time series. Consider an **image**: if an object is characterized by two facets—*shape* and *color*—then the combination of clusters in the shape facet and the color facet allows us to causally and interpretably describe the object’s overall class. This illustrates both the approach and the advantage of considering multiple facets when building AI/ML models.
{: .text-justify}

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/SingleTS.png" title="Single time series data" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/MultiTS.png" title="Multiple time series data" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

## What Is Multi-facet Clustering?

Clustering is widely used in AI applications. However, most traditional clustering methods are what we call **single-facet clustering**. That is, they partition data by aggregating information from all characteristics/facets. The draw back is that we **lose interpretability** since we don't know explicitly which characteristics actually contribute to the clustering solution. By contrast, **multi-facet clustering** can disentangle these characteristics/facets and partition data along different facets separately and simultaneously.
{: .text-justify}

As illustrated by the following figure comparing single-facet and multi-facet clustering. Suppose each object has two characteristics: *color* and *shape*.
{: .text-justify}

- A single-facet clustering might only reveal groups like *blue ducks* and *red bears*.
- Multi-facet clustering, however, separates the characteristics and shows that there are **three clusters in color** and **two clusters in shape**.

This way, each overall cluster can be interpreted in terms of its **facet-specific clusters**. For more details, we refer to our work on a novel Bayesian multi-facet clustering model for longitudinal data, available here: [Wang et al., PMLR 2025](https://proceedings.mlr.press/v286/wang25c.html).
{: .text-justify}

<div class="row justify-content-sm-center">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/IllusMF.png" title="Single-facet vs. Multi-facet Clustering" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

## How Is It Different to Multi-view and Multi-assignment Clustering?

The concept of multi-facet clustering is distinct from *Multi-view* and *Multi-assignment* clustering, as shown in the following table. In multi-facet clustering, the input is data from a single cohort, and the outputs are multiple clustering solutions, each corresponding to a different facet. By contrast, in multi-view clustering, the input consists of multiple views of data for the same cohort, but the goal is to produce a *single integrated clustering solution* that combines all views. In multi-assignment clustering, the input is again data from a single cohort, but the output is a clustering solution on a single facet where each individual can belong to *multiple clusters simultaneously*.
{: .text-justify}

|      Method      |      Facet     |        Input         |       Output      |
| :--------------: | :------------: | :------------------: | :---------------: |
| Multi-facet      |    Multiple    | Single data matrix   | Multiple clusters |
| Multi-view       |    Multiple    | Multiple data matrix | Single cluster    |
| Multi-assignment |    Single      | Single data matrix   | Multiple clusters |
