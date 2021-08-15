---
title: "Patel 2013 : Optimal dynamics for quality control in spatially distributed mitochondrial networks"
subtitle: ""
date: 2021-07-21T16:14:08+08:00
draft: false
author: "Patel"

series: ["mitochondria", "mitochondrial dynamics", "agent-based modeling"]
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

[Sciwheel](https://sciwheel.com/work/#/items/8390523)[^Patel2013]

[^Patel2013]: Patel PK, Shirihai O, Huang KC. Optimal dynamics for quality control in spatially distributed mitochondrial networks. PLoS Comput Biol. 2013 Jul 11;9(7):e1003108. [PMC3708874](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3708874/)


<!--more-->

Fusion was observed to selectively involve mitochondria with high potential.

This study also distinguished two different classes of fusion, one that allows complete mixing of matrix components and another that allows only partial mixing (transient fusion).

The inhibition of fusion or fission leads to a deterioration of overall mitochondrial health in many organisms.

Recent evidence suggests that mitochondrial motility plays a key role in each of the steps associated with mitochondrial quality control, including fusion, fission, biogenesis, and lysosomal function.

A previous computational study (`Twig et al.`) of the effects of fusion, fission, and autophagy on mitochondrial health in the presence of ROS-mediated damage demonstrated that selective fusion and autophagy can result in stable average health of the mitochondrial population.

Here, we present a computational model that incorporates the spatial dynamics of mitochondrial networks into the quality control cycle of the mitochondrial population.

As long as the density of mitochondria is high enough to preserve a critical level of fusion, quality control is sufficient to maintain a healthy mitochondrial population.

## A model of stochastic, spatially dependent mitochondrial dynamics

We define a quantity for each mitochondrion that we will refer to as its “health,” which is a proxy for mitochondrial membrane potential.

![](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3708874/bin/pcbi.1003108.g001.jpg "A cycle of fusion, fission, and autophagy contribute to quality control of mitochondrial health")

![](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3708874/bin/pcbi.1003108.g002.jpg "Active transport model of mitochondrial spatial dynamics")

We consider the mitochondria to be spatially distributed across a two-dimensional, square-shaped cell.

Autophagy is selective; only dysfunctional mitochondria with lower mitochondrial membrane potential are targeted to autophagosomes. Therefore, we model autophagy by removing mitochondria whose health is less than a given autophagy threshold.

The removal of mitochondria through autophagy is balanced by biogenesis, or replication.

## Autophagy is required for maintaining a healthy mitochondrial population

![](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3708874/bin/pcbi.1003108.g003.jpg "Maintenance of a healthy mitochondrial population requires autophagy and is enhanced by fusion and fission")

![](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3708874/bin/pcbi.1003108.g004.jpg "Maximal average steady-state health occurs for maximal asymmetry generation through stochastic exchange and fission")

![](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3708874/bin/pcbi.1003108.g005.jpg "Mitochondrial health is maximized when the thresholds for autophagy and fusion are equal.")

## Health maintenance is insensitive to mitochondrial density above a critical level

![](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3708874/bin/pcbi.1003108.g006.jpg "Health is insensitive to density as long as fusion events are sufficiently frequent")

## The motility dependence of fusion alters health primarily by modulating the overall frequency of fusion events

Fusion evenets are connected to mitochondrial motility and encounter.

![](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3708874/bin/pcbi.1003108.g007.jpg "Motion dependence of fusion alters health by rescaling the effective fusion rate")

## Limiting the rates of autophagy and replication affects health and mitochondrial population size in distinct manners

![](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3708874/bin/pcbi.1003108.g008.jpg "Maximal autophagy and replication rates affect health and mitochondrial population size in distinct manners")

## Discreteness is crucial for the effectiveness of membrane potential asymmetry

![](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3708874/bin/pcbi.1003108.g009.jpg "Maintenance of mitochondrial health requires a discrete health parameter")

## Discussion

In the presence of selective autophagy, the benefits of the generation of mitochondrial membrane potential asymmetry during the fusion/fission cycle substantially boost mitochondrial health.

The fusion frequency is a relevant metric:
- Average health is only weakly dependent on density as long as a minimal level of fusion is maintained.
- Imposing a motion dependence on the fusion rate mainly rescaled the effective fusion rate and thereby adjusted health. The cell can enhance fusion rates by actively regulating mitochondrial density and motility rather tha rely on making excessive fusion proteins.

Limiting the maximal rate of autophagy to below the damage rate resulted in a sharp decrease in health, while limiting the replication rate caused a decline in population numbers without affecting health.


## Methods

Model parameters: [Table 1](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3708874/table/pcbi-1003108-t001/)
