---
title: "Wacquier 2016 : Interplay Between Intracellular Ca Oscillations and Ca-stimulated Mitochondrial Metabolism "
subtitle: ""
date: 2021-07-15T17:29:23+08:00
draft: false
author: ""
authorLink: ""
description: ""

series: ["ODE", "mitochondria", "mitochondrial dynamics", "calcium", "MCU"]
categories: ["Reading"]

hiddenFromHomePage: false
hiddenFromSearch: false

featuredImage: ""
featuredImagePreview: ""

toc:
  enable: true
math:
  enable: true
lightgallery: true
---

[Sciwheel](https://sciwheel.com/work/#/items/5724355/)[^Wacquier2016]

[^Wacquier2016]: Wacquier B, Combettes L, Van Nhieu GT, Dupont G. Interplay Between Intracellular Ca(2+) Oscillations and Ca(2+)-stimulated Mitochondrial Metabolism. Sci Rep. 2016 Jan 18;6:19316. [PMC4725975](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4725975/)

<!--more-->

## Introduction

A new integrative model for Ca2+ signalling and mitochondrial metabolism in electrically non-excitable cells.

At rest, $\ce{[Ca^2+]}_m$ and $\ce{[Ca^2+]}_c$ are similar, in the 100 nM range.

In non-excitable cells, these oscillations are due to a cyclical exchange of Ca between the cytosol and the endoplasmic reticulum (ER), through the biphasic regulation of the IP3 receptor (IP3R) by cytosolic Ca.

Mitochondrial membrane potential (ΔΨ) drives cytosolic Ca to the mitochondrial matrix via the Mitochondrial Calcium Uniporter (MCU). Extrusion of Ca2+ out of mitochondria occurs through both a Na+-Ca2+ exchanger (NCX) and a H+-Ca2+ exchanger.

Pyruvate dehydrogenase (PDH) and two rate-limiting enzymes in the TCA cycle, isocitrate dehydrogenase and α-ketoglutarate dehydrogenase, are up-regulated by mitochondrial Ca. Cytosolic Ca also directly influences mitochondrial metabolism as a component of the malate-aspartate shuttle (MAS), the aspartate-glutamate carrier (AGC), is stimulated by modest increases in cytosolic Ca.

Given the complexity and highly non-linear character of Ca2+ and mitochondrial dynamics ( *not the fission/fusion dynamics* ), it is useful to resort to computational modelling to clarify their interplay. This model focues on calcium signaling affecting mitochondrial metabolism.

We found that a reversible Ca2+ leak between the cytosol and the mitochondria, which could correspond to the low conductance mode of the mitochondrial permeability transition pore, was necessary to account for a number of experimental observations.

The phase relationship between Ca2+ peaks in the cytosol, the ER, and the mitochondria31 was investigated in details. The effect of modifying the activity of the MCU or of the NCX was next analysed in the simulations, with respect to previous experimental observations in HeLa cells32,33.

## Model construction

HeLa cells-based.

![Fig1](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4725975/bin/srep19316-f1.jpg "Schematic")

Fluxes and reactions are described by ordinary differential equations (ODEs).

As we neglect spatial aspects, we do not consider Ca2+ microdomains, specifically MAM (mitochondria-associated ER membranes), in the model. Also, we do not consider Ca2+ fluxes through the mitochondrial Ca2+/H+ exchanger.

All concentrations (including Michaelis-Menten constants) are thus averages on the volume of a given intracellular compartment: cytosol (c), endoplasmic reticulum (ER) or mitochondria (m). The fluxes are scaled by the appropriate volume ratio when necessary.

### Parameters

[`Table1`](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4725975/table/t1/)

### ODEs

We adopt a fully deterministic approach, which is appropriate to obtain predictions about the average effect of the different individual fluxes on Ca2+ dynamics. (Cao, 2014)

The full system of equations is simulated using the software package XPPAUT.  Bifurcation diagrams are obtained numerically, by solving the differential equations with the MATLAB solver ode23, or ode23tb when using pulses.

Conservation relationships
- Total intracellular Ca since the cell is non-excitable.
- Total NAD/NADH
- Mitochondrial ATP/ADP
- Cystosolic ATP/ADP

The conservation of ADP/ATP does not hold in the long run as adenine nucleotide/Mg2+ transporters, known as SCaMCs, mediate net transfer of ADP and/or ATP to the mitochondrial matrix. But this conservation assumption is appropriate in the short simulation time of this model.

### MCU

We based this kinetic equation on that proposed by Magnus and Keizer, based on the Monod-Wyman-Changeux (MWC) formalism for allosteric enzymes, which in very good agreement with the results of Csordás et al. (2013) on the MCU.

![](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4725975/bin/srep19316-m15.jpg)

### NCX

The exponential expression was proposed by Bertram et al. (1Ca-3Na)

![](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4725975/bin/srep19316-m16.jpg)

It is assumed that the cytosolic Na+ concentration remains constant and that channel activity is favoured by a large ratio of Ca2+ concentrations between the cytosol and mitochondria.

### Calcium leak

![](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4725975/bin/srep19316-m17.jpg)

The existence of this flux also accounts for the observation that mitochondria take up Ca2+ from the cytosol at nanomolar concentrations, at which the MCU is inactive.
We hypothesize that this flux may reflect the low conductance state of the mitochondrial Permeability Transition Pore (mPTP).

### PDH

This expression is taken from Bertram et al.

![](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4725975/bin/srep19316-m18.jpg)

### Malate aspartate shuttle

![](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4725975/bin/srep19316-m20.jpg)

The aspartate-glutamate carrier is part of the MAS NADH shuttle

### ANT

![](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4725975/bin/srep19316-m22.jpg)

This equation has been erroneously transcribed and simplified in previous publications. (Saa, 2013)

### ATP synthesis

![](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4725975/bin/srep19316-m23.jpg)

A weak decrease in rate with increasing ATPm (i.e. with decreasing ADPm), but for a steep sigmoidal dependency on the mitochondrial potential.

### ATP consumption

![](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4725975/bin/srep19316-m24.jpg)

### Proton leak

Linear relationship.

![](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4725975/bin/srep19316-m25.jpg)

SERCA pumps are Ca-ATPases transporting 2 Ca ions for one molecule of ATP hydrolysed. This incorporates the link between Ca2+ activity and ATP consumption in the cytoplasm.

The second term encompasses the other ATP-consuming processes in the cytoplasm.

## Ca oscillations

![](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4725975/bin/srep19316-f2.jpg "Dynamics of Ca2+ exchanges between cytosol, ER and mitochondria")

![](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4725975/bin/srep19316-f3.jpg "The Ca2+ buffering capacity of mitochondria modifies the amplitude of Ca2+ oscillations")

![](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4725975/bin/srep19316-f4.jpg "The rate of Ca2+ entry into mitochondria alters cytosolic Ca2+ oscillations")

That decreasing the rate of Ca2+ entry into mitochondria through the MCU slows down Ca2+ oscillations appeared as a rather counter-intuitive prediction of the model. We tested this prediction experimentally using HeLa cells transiently transfected with scrambled siRNA or siRNA against MCU.

## Possible nature of the bidirectional Ca2+ flux between the mitochondria and the cytosol

![](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4725975/bin/srep19316-f5.jpg "Analysis of the bidirectional Ca2+ flux between the cytosol and the mitochondria, Jx.")

Inhibition of the mPTP by CSA (cyclosporin A) indeed increased the period of Ca2+ oscillations in response to both 0.3 and 1 μM histamine. It should be noted that CSA has been reported to stimulate SERCA pumps in addition to its effect on the mPTP.

## Dynamics of mitochondrial variables

![](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4725975/bin/srep19316-f6.jpg "Dynamics of mitochondrial variables")

## Glycolytic input and Ca2+ oscillations

We tested this in the model by decreasing kGLY that represents the input of the glycolytic pathway. This leads to a decrease in the period of Ca2+ oscillations, as observed experimentally. A less active glycolytic pathway indeed decreases the mitochondrial voltage and thereby reduces the activity of the MCU. In consequence, Ca2+ is less actively imported in mitochondria, leading to increased cytosolic Ca2+ between successive spikes.

![](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4725975/bin/srep19316-f7.jpg "Decreasing the glycolytic input slows down the cytosolic Ca2+ oscillations")

## Robustness of mitochondrial metabolism with respect to Ca2+ dynamics

We simulated Ca2+ spikes of different frequencies and amplitudes and computed the resulting average values of mitochondrial NADH and ATP concentrations.

![](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4725975/bin/srep19316-f8.jpg "Effect of changing the characteristics of Ca2+ spikes on mitochondrial metabolism")

Optimised metabolism is naturally obtained in the model for the parameter values listed in `Table 1`.

## Discussion

As compared with previous modelling approaches, we also considered the existence of one additional Ca2+ exchange flux between the cytosol and the mitochondria. (mPTP bidirectional)

Other modes of Ca2+ uptake into mitochondria, not considered in the model but reported to be active at low concentrations of cytosolic Ca2+, could also play a role.
- Ryanodine receptors
- Rapid mode of Ca2+ uptake by mitochondria (RaM)

The model is fully consistent with the reported effect of alterations in the rates of mitochondrial Ca2+ exchanges on the characteristics of Ca2+ oscillations. The frequency of oscillations can decrease when inhibiting the activity either of the NCX or of the MCU.

Altering mitochondrial metabolism in the model also accounts for corresponding published experimental observations about energising mitochondria.

The model finally predicted that mitochondrial metabolism remains relatively robust with respect to the amplitude and frequency of the stimulating Ca2+ oscillations.
