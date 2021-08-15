---
title: "Sukhorukov 2012 : Emergence of the mitochondrial reticulum from fission and fusion dynamics"
subtitle: ""
date: 2021-07-15T22:43:06+08:00
draft: false
author: ""
authorLink: ""
description: ""

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

[Sciwheel](https://sciwheel.com/work/#/items/4966662)

[^Sukhorukov2012]: Sukhorukov VM, Dikov D, Reichert AS, Meyer-Hermann M. Emergence of the mitochondrial reticulum from fission and fusion dynamics. PLoS Comput Biol. 2012 Oct 25;8(10):e1002745. [PMC3486901](http://www.ncbi.nlm.nih.gov/pmc/articles/PMC3486901)

<!--more-->

## Introduction

In the past few years mitochondria came into focus by ongoing discoveries of their central role in aging [1]–[3], ischemia [4], [5], development of cancer and common neurological and metabolic diseases [6]–[9].

![](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3486901/bin/pcbi.1002745.g001.jpg "Large-scale structure of mitochondria")

The mnitochondrial network architecture is rather diverse and flexible, is able to adjust itself on a time scale of minutes depending on the actual physiological condition, and is highly variable among different cell types.


## Results

The details of fission and fusion processes can be deduced from the morphological still image analysis.

The main advantage of this procedure is circumvention of the problems related to explicit 4-dimensional reconstruction of the network, not sufficiently reliable yet.

Computational image analysis of mtGFP-harboring mitochondria in HeLa cells revealed an exclusive presence of apparent node degrees 1≤k≤4.

### Nodes of degree three dominate the branching structure of the mitochondrial reticulum

Because the network structure is determined solely by the branching node types, quantitative image analysis is restricted to these only.

The degree 3 nodes result exclusively from interactions of a mitochondrial tip (k = 1) with a side surface (k = 2).  ∼96% of the actual branching points are of degree 3, while the fraction of k = 4 nodes is statistically insignificant. Accordingly, the model discussed in the following is designed to exclusively exhibit nodes with 1≤k≤3.

### The model of mitochondrial network dynamics

We represent the mitochondrial reticulum with a graph (nodes linked by edges, Fig. 1 C) consisting of the following node types: free ends of mitochondrial segments (k = 1), bulk sites (k = 2) and branching points (k = 3).

The graph formalism does not imply actual physical existence of discrete subunits of uniform size l, the length scale of the mitochondrial network, inside the mitochondrial bodies, but incorporates in a formal way their divisibility potential. Physically, l corresponds to the average distance between the membrane-bound fusion or fission complexes projected on the mitochondrial body axis.

Because under the microscope mitochondria (diameter ≈0.2 µm) in the maximally fragmented configuration resemble spherical vesicles, their diameter can be used as typical network edge length l = 0.2 µm, thus giving the value of the discretization parameter L = 30000 (≈5000/0.2). Keeping `L` as a free model parameter provides simple means for exploring the chondriome sizes relevant for different cell types.

### Assummptions in the model
The modeling framework proposed here can be utilized under the assumptions of
- (a) the network topology (1≤k≤3)
- (b) absence of correlations between reaction events.
- (c) mitochondria are well mixed

Some anisotropy could arise in the very periphery of widely spread cells where microtubules may become arranged in bundles or preferentially oriented towards the cellular distal edge.

In the bulk of the cytosol, frequent transitions between the fibers resulting from the high density of the cytoskeletal mesh common for the eukaryotes are expected to average the effect of single filaments out. This supposition was checked and confirmed by control simulations using an extended model where the mitochondrial network elements were assigned spatial positions by connecting them to explicit mesh of cytoskeletal fibers (data not shown).

The dynamics of mitochondria is governed here by node transformation rates, and thus the diffusion in physical space is not explicitly implemented.

The actual effective values for fusion/fission rates are taken from experimental measurements performed in living cells [15], which overall account for all known and unknown factors affecting the dynamics, without discrimination between those internal and external to mitochondria.

Importantly, the framework of dynamic quantitative graph introduced here can be utilized for an upgraded model where coordinates, velocities, and/or external forces are assigned explicitly to the network constituents.

Value of `L` (discretization value), the parameter accounting for the organelle size is assumed time-independent here

### Deterministic description links morphology to the fission and fusion rates

![](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3486901/bin/pcbi.1002745.g002.jpg "Steady state solutions of differential-algebraic model of the mitochondrial reticulum")

However, physiologically the most relevant parameter range is fairly narrow (see below), with all xk being far from saturation.

### Agent-based dynamics for the study of chondriome stochastic characteristics

- verified by investigation of the potential fusion points in a setting with explicit representation of the cytoskeleton (data not shown), for the long-term evolution a non-spatial approximation is justified inside the majority of the cytosolic volume.
- Thus, reaction events and timings are put under the operation of the Gillespie algorithm.
- In the absence of detailed biochemical data on fission and fusion rates, the simulation parameters were adjusted to reproduce the experimentally observed average frequencies of fusion and fission events ≈0.25 (cell·sec.)−1
- The following discussion is focused on the stochastic properties of the reticulum expressed in terms of statistical distributions.

### Tubular segment lengths are well approximated with a geometrical law

Using the agent-based model, we find that with a good accuracy the steady-state distributions of mitochondrial segment lengths (Fig. 3 A) can be expressed as a superposition of two qualitatively different, fast and slow decaying, terms with their relative strength being strongly dependent on c 1 and less on c 2.

![](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3486901/bin/pcbi.1002745.g003.jpg "Chondriome segment lengths")

All segment types other than disconnected loops (2-2), the geometric distribution provides a good approximation to the agent-based result.

### Sizes of disconnected chondriome parts correspond to the negative binomial distribution

![](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3486901/bin/pcbi.1002745.g004.jpg "Sizes of disconnected mitochondrial clusters")

### Percolation phase transition in the mitochondrial reticulum

In the thermodynamic limit of infinitely large network, the transition over a percolation threshold would correspond to an abrupt formation of a giant (percolating) cluster.

![](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3486901/bin/pcbi.1002745.g005.jpg "Percolation transition in the mitochondrial network")

*plotted as a function of c2 while keeping c1 constant*

In contrast, no phase transition is found in tip-to-tip rate c1.

The predicted phase transition implies two distinct classes of mitochondrial structures: a subcritical network consisting of a relatively uniform set of multiple disconnected mitochondria, as opposed to a supercritical one characterized by the presence of a dominant giant cluster accumulating the majority of the mitochondrial mass, accompanied by a few much smaller satellite mitochondria.

## Discussion

- We find that fusion and fission dynamics should lead to a branched reticulum of tubules which lengths are well approximated by a geometric law and which mean size in equilibrium is determined by relative rates of these processes.
- The cluster sizes are well approximated with a superposition of negative binomial distributions.
- Notably, the distribution shape is distinctly convex (Fig. 4 A), featuring numerous tiny clusters coexisting along with a few relatively large entities.
  - Mitophagy for small clusters. Autophagosomal bodies are not able to engulf objects larger than a few µm in mammals.
- A mitochondrial network capable of a phase transition. The critical transitional region lays in a narrow range of tip-to-side fusion/fission rates.
