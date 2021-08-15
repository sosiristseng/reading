---
title: "Fridlyand 2005 : Adenine nucleotide regulation in pancreatic beta-cells: modeling of ATP/ADP-Ca2+ interactions"
subtitle: ""
date: 2021-07-21T14:29:11+08:00
draft: false
author: ""
authorLink: ""
description: ""

series: ["mitochondria", "calcium", "ATP", "ODE"]
categories: ["Reading"]

hiddenFromHomePage: false
hiddenFromSearch: false

featuredImage: ""
featuredImagePreview: ""

toc:
  enable: true
lightgallery: true
---

[Sciwheel](https://sciwheel.com/work/#/items/8283971)[^Fridlyand2005]

[^Fridlyand2005]: Fridlyand LE, Ma L, Philipson LH. Adenine nucleotide regulation in pancreatic beta-cells: modeling of ATP/ADP-Ca2+ interactions. [Am J Physiol Endocrinol Metab. 2005 Nov;289(5):E839-48](https://journals.physiology.org/doi/full/10.1152/ajpendo.00595.2004).

<!--more-->

![](https://journals.physiology.org/cms/10.1152/ajpendo.00595.2004/asset/images/large/zh10110543410001.jpeg "Schematic diagram of currents and ion fluxes")

In beta cells, elevated levels of glucose causes an increase in the ratio of ATP to ADP that contributes to depolarization of the plasma membrane (PM) via inhibition of ATP-sensitive K+ (KATP) channels.

Intracellular free MgADP stimulates KATP channel activity, and it has been suggested that ADP, or the ATP/ADP ratio, is responsible for channel regulation in vivo.

Changes in [ATP]/[ADP] are tightly coupled to oscillations in intracellular free Ca2+, oxygen, and glucose consumption in pancreatic β-cells.

Two main types of [Ca2+]i oscillations in pancreatic β-cells: fast, where the period ranges from 10 to 30 seconds; and slow, with periods of several minutes. We focus here only on the slow oscillations in pancreatic β-cells.

## Materials

The islet and dispersed islet cells were isolated from pancreata of 8- to 10-wk-old C57BL/6J **mice**.

## Model Development

Parameters: [Table1](https://journals.physiology.org/doi/full/10.1152/ajpendo.00595.2004#T1)

### Glucose consumption

![](https://journals.physiology.org/na101/home/literatum/publisher/physio/journals/content/ajpendo/2005/ajpendo.2005.289.issue-5/ajpendo.00595.2004/production/images/eqs/eq-00001.gif)

Glucose phosphorylation by glucokinase (**GK**) is the only limiting step in glucose consumption in pancreatic β-cells under physiological conditions.

### Reduce equivalent

![](https://journals.physiology.org/na101/home/literatum/publisher/physio/journals/content/ajpendo/2005/ajpendo.2005.289.issue-5/ajpendo.00595.2004/production/images/eqs/eq-00002.gif)

`KRe` is determined by the quantity of ATP molecules that is produced from one glucose molecule, which equals **31** according to present estimations.

### OXPHOS

![](https://journals.physiology.org/na101/home/literatum/publisher/physio/journals/content/ajpendo/2005/ajpendo.2005.289.issue-5/ajpendo.00595.2004/production/images/eqs/eq-00003.gif)

The dependence of oxidative phosphorylation (JOP) on free MgADP may be calculated using the Hill equation.

We do not take into account effects of Ca2+ on the rate of ATP production in this model.

### ATP and ADP homeostasis

Over 90% of cellular ATP is in `MgATP` form. Thus are about the same concnetrations.

We added the balance equations for free ADP ([ADPf]i) and bound ADP ([ADPb]i). We assume that the concentration of free MgADP in pancreatic β-cells is 1/20 that of total cytosolic ADP.

### KATP channels

![](https://journals.physiology.org/na101/home/literatum/publisher/physio/journals/content/ajpendo/2005/ajpendo.2005.289.issue-5/ajpendo.00595.2004/production/images/eqs/eq-00007.gif)

Free ATP inhibits, whereas MgADP activates, KATP channels.

![](https://journals.physiology.org/cms/10.1152/ajpendo.00595.2004/asset/images/large/zh10110543410002.jpeg)


Decreased free ADP concentration in its physiological range can decrease the open probability of KATP channels at constant ATP concentrations.

### Computational aspects

This model is available for direct simulation on the website “Virtual Cell” ( www.nrcam.uchc.edu) in “MathModel Database” on the “math workspace” in the library “Fridlyand” with name “Chicago.2”.

## Computer Simulation

![](https://journals.physiology.org/cms/10.1152/ajpendo.00595.2004/asset/images/large/zh10110543410004.jpeg "Glucose-induced slow electrical bursting and Ca oscillations")

- slow Ca oscillations when `[Glc]` is above a threshold level of ∼7 mM
- slow oscillations correlate well with our previous model

![](https://journals.physiology.org/cms/10.1152/ajpendo.00595.2004/asset/images/large/zh10110543410005.jpeg "Steady-state simulation")

## Discussion

Intracellular free ATP concentration increases only modestly with increased glucose concentration in pancreatic β-cells or islets.

An increase of glucose from 4 to 8 mmol/l led to a decrease of free MgADP from ∼44 to ∼31 μM.

In intact INS-1 insulinoma cells, citrate and ATP oscillations are in phase with each other.

Slow metabolic oscillations could be driven by cytoplasmic Ca2+ oscillations has previously been dismissed.

The primary role of mitochondrial Ca2+ is the stimulation of oxidative phosphorylation. Slow Ca2+ oscillations are the driving force of metabolic oscillations in pancreatic β-cells.
