---
title: "Kornick 2019 : Population dynamics of mitochondria in cells: A minimal mathematical model"
subtitle: ""
date: 2021-07-20T17:33:24+08:00
draft: false
author: ""
authorLink: ""
description: ""

series: ["mitochondria", "mitochondrial dynamics", "ATP", "ODE"]
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

[Sciwheel](https://sciwheel.com/work/#/items/7993522)[^Kornick2019]

[^Kornick2019]: Kornick K, Bogner B, Sutter L, Das M. Population dynamics of mitochondria in cells: A minimal mathematical model. [Front Phys. 2019 Oct 9;7](https://www.frontiersin.org/articles/10.3389/fphy.2019.00146/full).


<!--more-->

## Introduction

We present a minimal mathematical model to study the interplay of mitochondrial dynamics. The model consists of coupled ODEs to describe populations of healthy and dysfunctional (unhealthy) mitochondria subject to mitochondrial fission, fusion, mitophagy, and varying levels of cellular ATP, which depend on ATP production by mitochondria and energy use during mitochondrial dynamics and other physiological processes.


## Model

![Fig1](https://www.frontiersin.org/files/Articles/429671/fphy-07-00146-HTML/image_m/fphy-07-00146-g001.jpg " The schematic diagram")

- Healthy and dysfunctional mitochondria have the same rates of biogenesis and fission.
- Healthy mitochondria fuse at a higher rate, while dysfunctional mitochondria undergo mitophagy at a higher rate.
- Energy (ATP) is produced by all mitochondria. Healthy mitochondria are more efficient in producing ATP than unhealthy mitochondria.
- Energy (ATP) is used in mitochondrial fission and fusion.
- Coupled ODEs describe the dynamics of the mitochondria populations.
- In the model, this assumption translates to the total number of mitochondria created by biogenesis being equal to the total number of mitochondria that is removed by mitophagy.
- The reaction rates approximately followed the values used in Patel et al.

## Results and Discussion

Healthy mitochondria fuse at higher rates than unhealthy mitochondria while the latter are removed from the cell at a higher rate, one would expect mitochondrial populations to consists of significantly higher concentrations of healthy mitochondria at long times.

![Fig2](https://www.frontiersin.org/files/Articles/429671/fphy-07-00146-HTML/image_m/fphy-07-00146-g002.jpg "Time evolution of concentrations of the four types of mitochondria")

![Fig3](https://www.frontiersin.org/files/Articles/429671/fphy-07-00146-HTML/image_m/fphy-07-00146-g003.jpg "Heat map of the steady state ratio of healthy and unhealthy mitochondria populations (Ch/Cu) as a function of the ratio of their fusion (λh/λu) and mitophagy (Mh/Mu) rates.")

ATP dependence causes small but observable variations in the dynamics of the four mitochondria populations at small times as seen by comparing Figures, while their asymptotic behavior is the same.

![Fig4](https://www.frontiersin.org/files/Articles/429671/fphy-07-00146-HTML/image_m/fphy-07-00146-g004.jpg "Figure 2 but adding ATP dependence")

![Fig5](https://www.frontiersin.org/files/Articles/429671/fphy-07-00146-HTML/image_m/fphy-07-00146-g005.jpg "The ratio of fused and unfused mitochondria concentrations with or without ATP dependence")

Linear stability analysis: The eigenvalues as a function of the selective mitophagy parameter. One of these two eigenvalues has a negative value while the other has a positive value implying that the steady states are saddle points.

![](https://www.frontiersin.org/files/Articles/429671/fphy-07-00146-HTML/image_m/fphy-07-00146-g006.jpg "Linear Stability analyses")

## Future works

We will also frame mitochondrial bioenergetics in terms of the mitochondrial membrane potential [19] and oxidative processes [20, 21] in future work, to better connect to experiments, and systematically quantify how perturbations in mitochondrial dynamics and bioenergetics impact the heterogeneity of mitochondrial genotypes over multiple cell cycles, and in collections of many cells.
