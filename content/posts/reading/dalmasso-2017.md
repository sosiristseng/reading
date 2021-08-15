---
title: "Dalmasso 2017 : Agent-Based Modeling of Mitochondria Links Sub-Cellular Dynamics to Cellular Homeostasis and Heterogeneity"
subtitle: ""
date: 2021-07-15T21:58:22+08:00
draft: false
author: ""
authorLink: ""
description: ""

series: ["mitochondria", "mitochondrial dynamics", "agent-based modeling"]
categories: ["Mitochondrial dynamics"]

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

[Sciwheel](https://sciwheel.com/work/#/items/2930392)[^Dalmasso2017]

[^Dalmasso2017]: Dalmasso G, Marin Zapata PA, Brady NR, Hamacher-Brady A. Agent-Based Modeling of Mitochondria Links Sub-Cellular Dynamics to Cellular Homeostasis and Heterogeneity. PLoS ONE. 2017 Jan 6;12(1):e0168198. [PMC5217980](http://www.ncbi.nlm.nih.gov/pmc/articles/PMC5217980)

<!--more-->

## Introduction

We sought to analyze how reactions of individual mitochondria form a collective population response, to organize morphological states and maintain mass homeostasis, under basal conditions and in response to bioenergetic stress.

We employed agent-based modeling (ABM), a computational method to simulate spatial and temporal population activities.

## Modeling

Mitochondrial fusion and fission processes were modeled using a discrete approach, since a continuous approximation was unreasonable due to the low copy number of mitochondria.

![](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5217980/bin/pone.0168198.g001.jpg "An agent-based model of mitochondrial dynamics determined by organelle mobility and fusion-fission cycles")

Parameters are in [Table 1](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5217980/table/pone.0168198.t001/)

Mitochondrial fusion and fission cycles occur on the order of minutes, and thus, at larger time scales than mitochondrial movement. The rule sets for mitochondrial fission and fusion were only evaluated every 5 minutes.

Here we employed parameter sweeping to find parameter combinations which produced the best description of experimentally-established dynamics of mitochondrial growth and degradation, and two sensitivity analysis methods.

## The effect of fusion and fission on mitochondrial morphology is intrinsically connected to the total mitochondrial mass

![](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5217980/bin/pone.0168198.g002.jpg "Impact of fusion and fission probabilities and mitochondrial mass on mitochondrial subpopulations")

These results suggest that mitochondrial morphology homeostasis depends on both, fusion and fission probabilities and the total mitochondrial mass.

## Influence of mitochondrial directionality on subpopulation distributions


![](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5217980/bin/pone.0168198.g003.jpg "Impact of mitochondrial directionality on mitochondrial mass subpopulation distributions")

The time course distribution of mitochondrial subpopulations was unchanged between restricted and unrestricted movements. These findings suggest that the impact of mitochondrial directionality on the state of the mitochondrial population is negligible.

## Transmission dynamics of the mitochondrial network

Mitochondrial network transmissivity has been previously measured by photoactivatable GFP within a subpopulation of mitochondria (~10%), finding that the complete mitochondrial population was fluorescent within 30–60 minutes.

![](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5217980/bin/pone.0168198.g004.jpg "In silico photoactivation to quantify transmission dynamics in mitochondrial networks")

Under conditions of free movement (Fig 4B), a balanced probability of fusion and fission (50%/50%) produced the fastest GFP transmission. Similar tendencies were obtained under conditions of restricted movement, but the 50% transmission time was decreased relative to free movement.

We applied a global sensitivity analysis using Latin-Hypercube Sampling (LHS) and Extended Fourier Amplitude Sampling Test (eFAST).
![](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5217980/bin/pone.0168198.g005.jpg "Sensitivity analysis of the transmission dynamics model")

## Integrating mitochondrial dynamics with mitochondrial biogenesis

![](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5217980/bin/pone.0168198.g006.jpg "Integration of mitochondrial biogenesis through parameter fitting")

## Integrating mitochondrial dynamics with mitochondrial damage and mitophagy

![](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5217980/bin/pone.0168198.g007.jpg "Integration of mitochondrial damage sensing and mitophagy through parameter fitting")

A probability variable (dp) stands for the fission process whereby one mitochondrion fragments into one healthy and one damaged mitochondrion.

Two damage states, low and high, correspond to pre-mitophagy and mitophagy induction states.

Degradation is represented by frequency (Df) parameter and damage (dT) and receptor (MRT) thresholds.

The resulting model fit by GA eliminates all damaged mitochondria within one day.

## Bioenergetics and mitochondrial dynamics

We thus considered functions of the metabolic sensor AMP-activated protein kinase (AMPK). AMPK is activated in response to decreased ATP production, i.e. bioenergetic stress, and activates PGC-1 alpha, the master regulator of mitochondrial biogenesis. AMPK also regulates the removal of defective mitochondria.

![](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5217980/bin/pone.0168198.g008.jpg "Interaction between mitochondrial health and cellular energetic state, based on the energetic stress")

![](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5217980/bin/pone.0168198.g009.jpg "Sensitivity analysis of the full model")

## Discussion

The deregulation of mitochondrial dynamics is a contributing factor to many diseases [16, 78, 79].

Mitochondrial density contributes independently of a probability for fusion and fission.

Sensitiity analysis showed mitochondrial mobility is an essential component for transmission dynamics rather than the total mitochondrial mass.

In the context of AMPK energetic sensing, the model appeared to be mainly subjected to the damage probability and to the frequencies of fusion, fission and biogenesis.
