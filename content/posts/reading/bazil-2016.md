---
title: "Bazil 2016 : Catalytic Coupling of Oxidative Phosphorylation, ATP Demand, and Reactive Oxygen Species Generation"
date: 2020-10-22T17:43:36+08:00
tags: ["differential equations"]
series: ["ODE", "mitochondria", "ROS", "complex 1", "complex 3", "complex 4" ,"cardiomyocyte"]
categories: ["Reading"]
author: "Bazil et al."
math:
  enable: false
lightgallery: true
---

[Sciwheel](https://sciwheel.com/work/#/items/5916855)[^Bazil2016]

<!--more-->

Based on the two previous papers.[^Bazil2014][^Bazil2013]

## Introduction
* the concentration of cytoplasmic Pi is thought to be the most important feedback signal controlling oxidative phosphorylation
*  alternative hypothesis: open-loop stimulation by calcium => attempts to demonstrate these stimulatory effects within the physiological range of calcium concentrations, temperature, ionic strength, and substrate concentrations, have failed
* Elevated ROS levels from complex I caused by matrix alkalization after mitochondrial KATP channel opening contributes to cardioprotection against ischemia/reperfusion injury. But the existence of the KATP channel is still debated
* Extrapolating ROS production rates measured in vitro to expected rates in vivo must be done with caution
* As it is currently extremely difficult to accurately measure ROS production in vivo, a mathematical model is required
* Our recent work identifying and analyzing thermodynamically constrained models describing the catalytic mechanisms of respiratory complexes Iand III
* predicts that an increase in the quinone pool (Q pool) redox state is responsible for the apparent activation of complex III by inorganic phosphate

## Materials and Methods
![gr1](https://user-images.githubusercontent.com/40054455/125478083-e20771f7-c545-466e-9d71-1d555f22a755.jpg)


* The model descriptors for NADH production, complexes I, III, and IV were updated from the 2005 Beard model to capture the substrate/product and hydrogen peroxide/superoxide production kinetics

## Results and Discussion
![image](https://user-images.githubusercontent.com/40054455/125478149-52ab8a10-3156-435f-a9f1-f716437a28e2.png "Model simulations compared to experimental data from isolated rat heart mitochondria")
![image](https://user-images.githubusercontent.com/40054455/125478230-d091bac5-a3ac-4e23-baaa-c3f3675a16b3.png "FCCP titration of mitochondrial energetics")

![image](https://user-images.githubusercontent.com/40054455/125479086-cdb05005-1a0e-4666-937a-0352d3400cb1.png "The OxPhos flux control coefficients for increasing workloads")

![image](https://user-images.githubusercontent.com/40054455/125479228-2e1ee46c-4cb2-4fc6-82f4-20c24531edc5.png)

![image](https://user-images.githubusercontent.com/40054455/125479298-bd7cbca2-ec34-4b7d-a0f4-0e67388fd690.png "Model simulations of ischemia/reperfusion (I/R)")

* orange: with succinate accumulation. blue: without succinate accumulation
* For the ischemic period, the O2 concentration was set to 1 nM to reflect the hypoxic conditions during ischemia. For the reperfusion period, the O2 concentration was set back to the baseline value.
* For the I/R Simulation 2 conditions, RET is the dominant source of ROS and leads to a 10-fold higher ROS production rate compared to forward electron transport
* This conclusion is strongly corroborated by Chouchani et al. , who demonstrate that elevated ROS production during reperfusion after ischemia is due to accumulation of mitochondrial succinate

## Conclusion
* an oxidative-phosphorylation model that is capable of simulating ROS dynamics
* updated complexes I, III, and IV, and ANT

## References
[^Bazil2016]: Bazil JN, Beard DA, Vinnakota KC. Catalytic Coupling of Oxidative Phosphorylation, ATP Demand, and Reactive Oxygen Species Generation. Biophys J. 2016;110(4):962-71. [PMC4776027](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4776027/)

[^Bazil2014]: Bazil JN, Pannala VR, Dash RK, Beard DA. Determining the origins of superoxide and hydrogen peroxide in the mammalian NADH:ubiquinone oxidoreductase. Free Radic Biol Med. 2014;77:121-9. [PMC4258523](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4258523/)

[^Bazil2013]: Bazil JN, Vinnakota KC, Wu F, Beard DA. Analysis of the kinetics and bistability of ubiquinol:cytochrome c oxidoreductase. Biophys J. 2013;105(2):343-55. [PMC3714890](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3714890/)
