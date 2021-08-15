---
title: "Zamponi 2018 : Mitochondrial network complexity emerges from fission/fusion dynamics"
subtitle: ""
date: 2021-04-08T17:18:43+08:00
author: "Zamponi et al"
authorLink: ""
description: ""

series: ["mitochondrial dynamics", "mitochondria"]
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

Sciwheel[^1]

[^1]: Zamponi N, Zamponi E, Cannas SA, Billoni OV, Helguera PR, Chialvo DR. Mitochondrial network complexity emerges from fission/fusion dynamics. Sci Rep. 2018 Jan 10;8(1):363.[PMC5762699](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5762699/)

Mitochondrial networks exhibit a variety of complex behaviors, including coordinated cell-wide oscillations of energy states as well as a phase transition (depolarization) in response to oxidative stress.

<!--more-->

## Introduction

A typical mitochondrion comprises a network of tube-like structures, with fragments of all sizes (ranging from less than 1 μm to 15 μm or more). A quantitative description of such complexity is still lacking.

In this work, we present a quantitative description of mitochondrial network structure using tools of network and percolation theory. To do that, we developed a pipeline to extract structural parameters from confocal images.

## Results

![Fig1](https://user-images.githubusercontent.com/40054455/114002213-3f9e0d00-988f-11eb-8336-7e0f8db2903f.png "Fig 1. Network structure from mitochondrial images.")

**Fig1** Network structure from mitochondrial images.
- (a) Confocal image of a MEF in which mitochondria are shown in green and the actin cytoskeleton in magenta. Image processing:
- (b) Grayscale images were converted to binary images by choosing the indicated threshold.
- (c) Detected lines in binary images were reduced to a single pixel width (skeleton). The mean degree 〈k〉 of each skeleton was computed by analysing the nearest neighbors of each pixel occupied.
- (d) Cluster mass distributions p(s) were computed by counting the number of pixels that made up each segment within clusters. Red curves represent power laws with exponents −1 (dashed) and −2 (continuous). Scale bars represent 10 μm.

The long-tail behaviour displayed by p(s) was in accordance with recent work suggesting that mitochondrial networks operate near a percolation phase transition. Long-tail distributions in Fig. 1(d) indicated that mitochondrial networks exhibited scale free properties, such as the coexistence of numerous small fragments with few massive clusters.


![Fig2](https://user-images.githubusercontent.com/40054455/114002677-a7ecee80-988f-11eb-9216-8207f61c720d.png "Fig 2. Typical examples of mitochondrial network images obtained under different conditions.")

**Fig2** Typical examples of mitochondrial network images obtained under different conditions.
Confocal images of MEFs transfected with mYFP under control conditions (ctl), paraquat treatment (pqt) or mitofusin 1 over-expression (mfn). Pixel intensity is depicted using a pseudocolor (calibration bar). Insets highlight the effect asserted by each treatment on mitochondrial structure. Scale bars represent 10 μm.

### Quantification of mitochondrial network properties

The application of different intensity thresholds (th) resulted in different skeletons and hence different network architectures.  We reasoned that a way to avoid this arbitrariness would be to compare the behavior of network parameters as a function of the threshold.

![Fig3](https://user-images.githubusercontent.com/40054455/114003002-fc906980-988f-11eb-9d31-e2d79ba88e26.png "Fig 3. Network parameters computed from single images")

![Fig4](https://user-images.githubusercontent.com/40054455/114003496-5bee7980-9890-11eb-97c6-11326968da2c.png "Fig 4. Changes in mass distributions upon fission/fusion balance perturbatio")


### Fission/fusion balance is linked to mitochondrial network complexity

We investigated the scaling properties of mitochondrial networks by performing a finite size scaling analysis.

![Fig5](https://user-images.githubusercontent.com/40054455/114003694-8a6c5480-9890-11eb-9813-065be9669483.png "Fig 5. Changes in mitochondrial network complexity")

Given the functional relevance of the spatial distribution of mitochondria36–39, we decided to quantify the **fractal dimension** Df of the networks.

Alterations in the fission/fusion balance tended to reduce network complexity, as shown by normalized Kolmogorov complexity.

Shannon’s entropy of cluster masses (Hj)

### Are mitochondrial networks poised at criticality

This view propose that a steady-state mitochondrial network requires a proper balance of the two opposing tendencies, one towards fusing segments and one favoring fragmentation.

![Fig6](https://user-images.githubusercontent.com/40054455/114004797-91e02d80-9891-11eb-9e5f-6fe589ec5391.png "Fig 6. Comparison of the present experimental results with those of the Sukhorukov model.")


## Discussion

- Mitochondria organize as complex networks that display temporal and spatial coordination, pressumably by operating close to the edge of dynamic instability.
- A straightforward approach to quantify structural properties of mitochondrial networks.
- Promoting fission or fusion lowered the fractal dimension of the networks, reducing the space-filling capacity of mitochondria, lowering the Kolmogorov complexity.
- Balanced fission/fusion dynamics lead to a network capable of a phase transition : three different regimes, subcritical (pqt), critical (ctl) and supercritical (mfn),
- Under normal physiological conditions, mitochondrial networks are poissed near a percolation transition point

## Materials and Methods

- Mouse embryonic fibroblast (MEF) expressing a mitochondria-targeted yellow fluorescent protein (mYFP)
- Microscopy -> binarize -> skeletons of mitochondrial network -> cluster mass (s) and degree (k)
- Perturbed the structure of mitochondrial networks either by increasing mitochondrial fission using paraquat (pqt)12–15, or by promoting mitochondrial fusion by mitofusin 1 (mfn) over-expression.
