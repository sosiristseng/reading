---
title: "Hoffman 2017 : A multimethod computational simulation approach for investigating mitochondrial dynamics and dysfunction in degenerative aging"
subtitle: ""
date: 2021-07-15T16:43:13+08:00
draft: false
author: ""
authorLink: ""
description: ""

series: ["ODE", "mitochondria", "mitochondrial dynamics", "ROS"]
categories: ["Reading"]

hiddenFromHomePage: false
hiddenFromSearch: false

featuredImage: ""
featuredImagePreview: ""

toc:
  enable: true
math:
  enable: false
lightgallery: true
---

[Sciwheel](https://sciwheel.com/work/#/items/5413180/)[^Hoffman2017]

[^Hoffman2017]: Hoffman TE, Barnett KJ, Wallis L, Hanneman WH. A multimethod computational simulation approach for investigating mitochondrial dynamics and dysfunction in degenerative aging. Aging Cell. 2017 Aug 16;16(6):1244–55. [PMC5676065](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5676065/)

<!--more-->

## Summary

We have taken an *in silico* approach to expand the focus of the MFRTA by including other key mitochondrial stress response pathways, as they have been observed in the nematode *Caenorhabditis elegans*.
These include the
- mitochondrial unfolded protein response (UPR mt)
- mitochondrial biogenesis and autophagy dynamics (**no fission / fusion**)
- the relevant DAF‐16 and SKN‐1 axes
- and NAD-dependent deacetylase activities.

To integrate these pathways, we have developed a multilevel hybrid‐modeling paradigm, containing
- agent‐based elements among stochastic system‐dynamics environments of
- logically derived ordinary differential equations,

to simulate aging mitochondrial phenotypes within a population of energetically demanding cells.

![](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5676065/bin/ACEL-16-1244-g001.jpg "The integrated aging mechanism of interest and computational simulation approach")

## Introduction

MFRTA: mitochondrial free radical theory of aging is mediated by

- ROS (but physiological amount is beneficial)
- mitochondrial unfolded protein response (UPRmt)

The degenerative aging response is not a result of a single concrete cellular pathway, but is dependent upon specific magnitudes of multiple key mitochondrial pathways that allow for cellular senescence states and pathological phenotypes.

## Model construction

[Supporting information (pdf)](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5676065/bin/ACEL-16-1244-s001.pdf)

To fill this network with realistic parameters and relevant reaction schemes for the aging nematode, we gathered a vast set of information from the literature to determine:
- mitochondria counts and mtDNA counts.
- mitochondrion‐level system‐dynamics and discrete‐event computational methods for oxidative metabolism, proteostasis, and heteroplasmic mtDNA analysis.
- cell‐level system‐dynamics computational methods surrounding the UPRmt and mitochondrial protein import
- Agent‐based principles that govern stress‐dependent cellular degeneration

The model consists of

- logically derived ordinary differential equations (ODEs)
- discrete‐event (stochastic) statements

### Reference
- superoxide production and disposition to complement C. elegans data (Gruber et al., 2011)
- compartmentalized dynamic model of oxidative metabolism carried out to predict endpoints seen in PD development (Cloutier & Wellstead, 2012)
- stochastic modeling analysis of damaged mtDNA in aging mitochondria (Tam et al., 2015)

## Model performance and predictions for spontaneous functional declines

![Fig2](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5676065/bin/ACEL-16-1244-g002.jpg "Experimental and predictive biomarkers of bioenergetic function for normal and pharmacologically altered aging in C. elegans")

A sharp decline in tissue ATP presents itself after NAD+ levels have begun to decline (around 7500 min)

![Fig3](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5676065/bin/ACEL-16-1244-g003.jpg "Stochastic single‐cell mitochondrial health data from three representative cells in the model")

Mitochondrial dynamics, including biogenesis and selective mitophagy, were simulated, and organelle counts were tracked for an entire population of cells.

![Fig4](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5676065/bin/ACEL-16-1244-g004.jpg "Model‐generated mitochondrial counts and heteroplasmic mtDNA content in normal and pharmacologically altered aging")


Oxidative stress levels were measured in silico as well (Fig. 5A), and closely matched spontaneous increases seen previously in C. elegans (Gruber et al., 2011).

![Fig5](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5676065/bin/ACEL-16-1244-g005.jpg "Simulation analysis of normal and pharmacologically modified oxidative burden in aging cells")


## Endpoint changes after control of selective mitophagy

To perturb the computational model, we determined mathematical methods for introducing rapamycin or bafilomycin as regulators of mitophagy (Box S7).

## Age‐dependent total cellular damage and degeneration analysis

![Fig6](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5676065/bin/ACEL-16-1244-g006.jpg "Age‐dependent total cellular damage and degeneration analysis")
