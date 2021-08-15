---
title: "Heijman 2016 : Computational models of atrial cellular electrophysiology and calcium handling, and their role in atrial fibrillation"
date: 2020-10-23T00:05:07+08:00
series: ["ODE", "cardiomyocyte", "electrophysiology", "calcium", "atria model"]
categories: ["Reading"]
author: "Heijman et al."
math:
  enable: false
lightgallery: true
---

[Sciwheel](https://sciwheel.com/work/#/items/4522998)[^Heijman2016]

<!--more-->

## Introduction
* Computational modelling was developed to complement experimental approaches to improve understanding of cardiac electrophysiology and arrhythmogenesis
* a central role for **Ca2+ handling** abnormalities has been identified in promoting ectopic activity and re‐entry, the two major mechanisms underlying atrial fibrillation (AF)

## Differences between atrial, ventricular and sinoatrial node cardiomyocytes
![image](https://user-images.githubusercontent.com/40054455/125469140-ab06bbb6-3da7-4f45-9695-8d41911c44fc.png)
* Atrial cardiomyocytes possessing a number of ion currents that are largely absent in the ventricle (e.g. ultra‐rapid delayed‐rectifier K+ current IKur, or acetylcholine‐activated inward‐rectifying K+ current IK,ACh)
* SAN cardiomyocytes additionally express more hyperpolarization‐activated cyclic nucleotide‐gated (HCN) channels but have relatively few Na+ channels. T‐type Ca2+ current is largest in the SAN.
* ventricular cardiomyocytes have a larger basal inward‐rectifying K+ current (IK1)
* differences in Ca2+ handling between cell types
    * ventricular myocytes having a well‐developed system of membrane invaginations (t‐tubules) => homogeneous activation
    * atrial myocytes: centripetal Ca2+ wave
## Role of Ca2+ handling abnormalities in atrial arrhythmias
* Ca2+ overload can activate NCX => EADs and DADs, cardiac alternans
* Ca signalling pathways => remodeling
## Computational modelling of atrial cellular electrophysiology and Ca2+ handling
![image](https://user-images.githubusercontent.com/40054455/125469166-24b43314-abcd-4794-9fed-66c7f3248fb4.png)

### Types of ion‐channel models
* instantaneous, time‐independent (rapid equilibrium): IK1
* Hodgkin–Huxley gating variables
* Markov models: states variables, more complex, additionally capture dependent state transitions
## Atrial cardiomyocyte models and their principal findings
![image](https://user-images.githubusercontent.com/40054455/125469183-a65d52ff-2390-4293-a190-a780d86e4e44.png)

## Computational models based on experimental data from animals
See `Table 1`
## Computational models of human atrial cardiomyocytes
![image](https://user-images.githubusercontent.com/40054455/125469196-91dee0e4-71af-4036-a1a8-412c572f1dc7.png)

## Spatial models of atrial Ca2+ handling
* transverse segmentation allows simulation of the centripetal Ca2+ wave
* subsarcolemmal SR Ca2+‐release sites influence AP shape, whereas the central release sites control centripetal Ca2+ wave propagation
* However, common‐pool models also show alternans, as recently demonstrated for the Grandi model (Chang et al. 2014). This type of alternans critically depends on intrinsic RyR2 properties.
* both transverse and longitudinal compartmentation of Ca2+ handling (Fig. 4 C), along with stochastic gating of RyR2s using a Markov‐model approach => The combination of changes produces sustained triggered activity = paroxysmal AF (pAF)

![image](https://user-images.githubusercontent.com/40054455/125469337-96698aed-c1d3-41d7-89c3-4ee4236fb935.png)

## Applications of computational modelling in AF research
![image](https://user-images.githubusercontent.com/40054455/125469348-93fb663f-6495-4fcb-a271-275dfe1cc9ca.png)

* It's not experimentally possible to modulate the function of a single channel or transporter in human atrial cardiomyocytes with high specificity. Computational assessment of potential mechanisms of atrial arrhythmogenesis could help to identify experimental findings about changes in ion‐channel function
* The advances and applications of atrial cardiomyocyte models have been paralleled by advances in the development of models for other cell types (ventricular: common‐pool and spatial ‘local‐control’ models)
## Gaps in knowledge and future directions
* pronounced inter‐patient and regional variation: tissues surrounding the (PVs) have specific electrophysiological and Ca2+ handling properties, making them more likely to produce ectopic activity
* multiscale understanding of AF
* Channel modeling (e.g. RyR2)

![image](https://user-images.githubusercontent.com/40054455/125469419-8c6c77c8-ab33-49ac-8732-09bc12dc1765.png)

## Reference

[^Heijman2016]: Heijman J, Erfanian Abdoust P, Voigt N, Nattel S, Dobrev D. Computational models of atrial cellular electrophysiology and calcium handling, and their role in atrial fibrillation. J Physiol (Lond) 2016;594(3):537-553. doi:10.1113/JP271404. [PMC5341705](http://www.ncbi.nlm.nih.gov/pmc/articles/PMC5341705).
