---
title: "Bazil 2013 : Catalytic coupling of oxidative phosphorylation, ATP demand, and reactive oxygen species generation"
date: 2020-10-22T17:36:38+08:00
tags: ["differential equations"]
series: ["ODE", "ROS", "complex 3", "ATP", "mitochondria", "enzyme kinetics", "cardiomyocyte"]
categories: ["Reading"]
author: "Bazil et al."
lightgallery: true
---

[Sciwheel](https://sciwheel.com/work/#/items/5931055)[^Bazil2013]

[^Bazil2013]: Bazil JN, Vinnakota KC, Wu F, Beard DA. Analysis of the kinetics and bistability of ubiquinol:cytochrome c oxidoreductase. Biophys J. 2013;105(2):343-55. [PMC3714890](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3714890/)

<!--more-->

## Introduction

* The biochemical equation of Complex III for the net reaction is shown as
![image](https://user-images.githubusercontent.com/40054455/125469534-2b76f5cb-5574-424a-891e-c29287fe58f7.png)

* Previous models are either too simple or too complex
* The model developed here maintains the features presented above in a tenable, well-constrained representation of the bc1 complex

## Methods

###  Model structure

![image](https://user-images.githubusercontent.com/40054455/125469589-33ac25ef-39ab-4336-a0be-cf3c43d0226c.png)
* This model includes the redox biochemistry that occurs at the Qo-site and Qi-site of the complex and couples cyt c reduction with the first electron transfer from ubiquinol
* This first electron transfer at the Qo-site is the one of the primary, rate-limiting steps in the catalytic cycle
* we assume that up to two mobile electrons can exist at both the Qo-site and Qi-site
* 6 states
* The fractional substate occupancies and the state transitions are governed by the thermodynamic driving force of the redox biochemistry defined by the midpoint potentials some of them being pH-dependent
* Binding polynomials for Qo, Qi site, and ISP FeS
* Under the right circumstances when cyt bL is reduced, there is a small but significant level of SQ at the Qo-site
* State transitions are governed by two primary Gibb’s free energies of reaction.
* The net turnover flux through the enzyme: ![image](https://user-images.githubusercontent.com/40054455/125469631-37c1bba4-0f62-40c1-9240-28a1c40ede4a.png)
* Superoxide production rate: ![image](https://user-images.githubusercontent.com/40054455/125469677-4c688c85-1af7-4771-8be7-87e034bb43f5.png)
*  analytic expressions for the states at steady state
![image](https://user-images.githubusercontent.com/40054455/125469714-dfcf4c2f-4038-4701-a7e4-4c34390d7613.png)
* The analytical solution for each state contains ∼1000 terms, so they are not explicitly presented here (using KA method ?)

## Results and Discussion

* [Table1](https://www.cell.com/biophysj/fulltext/S0006-3495(13)00616-4#tbl1): fixed parameter values obtained from the literature and used to simulate the model
    * midpoint potentials, stability constants, pKa values, and other parameters
* [Table2](https://www.cell.com/biophysj/fulltext/S0006-3495(13)00616-4#tbl2):  fitted parameter values and sesitivity

![image](https://user-images.githubusercontent.com/40054455/125469850-3dfab754-ada9-4f2f-a409-e06901063398.png)
![image](https://user-images.githubusercontent.com/40054455/125469903-87cf7134-241e-47d2-ac65-f6d5cc9f857f.png)
![image](https://user-images.githubusercontent.com/40054455/125469919-30947d5a-858f-4cfe-8cae-c10286b3476c.png)
![image](https://user-images.githubusercontent.com/40054455/125469928-1598eaaf-9384-4b56-bab7-a0b960c827ab.png)
![image](https://user-images.githubusercontent.com/40054455/125470062-d636068d-cbba-4dc6-aa38-19a46ac48cd9.png)

* The cyt c binding constants were assumed to be similar to the fitted constants for horse heart cyt c, based on its apparent universal nature as a substrate for bc1 complexes from other species

![image](https://user-images.githubusercontent.com/40054455/125470136-d86f5e9e-e23c-419c-bc33-c11ceead16ef.png)
