---
title: "Hatano 2015 : Distinct Functional Roles of Cardiac Mitochondrial Subpopulations Revealed by a 3D Simulation Model"
date: 2020-10-23T00:04:20+08:00
series: ["PDE", "cardiomyocyte", "ATP", "mitochondria"]
categories: ["Reading"]
author: "Hatano et al."
math:
  enable: false
lightgallery: true
---

[Sciwheel](https://sciwheel.com/work/#/items/3609754)[^Hatano2015]

<!--more-->

## Introduction
* Mitochondria located in specific cell regions are reported to have different morphological and biochemical properties => subsarcolemmal mitochondria (SSM) and interfibrillar mitochondria (IFM)
* IFM and SSM are differentially affected under pathological conditions

## Materials and Methods
### 3D cardiomyocyte model
Previous model[^Hatano2012]
![image](https://user-images.githubusercontent.com/40054455/123205297-33b80380-d4ec-11eb-9ae0-50feda0f2d86.png)
* Added oxygen and myoglobin buffering
* compared simulated oxygen and NADH distributions with the experimental results of Takahashi et al

### Modeling SSM and IFM
* Mitochondria facing the surface sarcolemma were taken to be SSM and others were taken to be IFM
* 10% of the mitochondrial node volume was treated as cytosolic space (corresponding to intermembrane space). Ions and metabolites freely diffusable between through OMM.
* IFM have ∼50% higher oxidative capacity and TCA activity than SSM in reports.
    * equal model: same capacity
    * hetero model: 50% higher enzymatic activity in IFM

![tbl1](https://user-images.githubusercontent.com/40054455/86618472-8d79a200-bfeb-11ea-8d33-41d97829b630.png)

### Oxygen diffusion and oxidative phosphorylation
* myoglobin as an immobile oxygen buffer and adopted a fast equilibrium assumption
  ![eqn1 myoglobin saturation](https://user-images.githubusercontent.com/40054455/86618462-8b174800-bfeb-11ea-840a-39791951b1ea.png)
  ![eqn2 partial oxygen pressure (PO2)](https://user-images.githubusercontent.com/40054455/86618467-8c487500-bfeb-11ea-8733-f9b5d17dd101.png), α = 1.5 μM / mmHg
* Rates of oxygen consumption and proton pumping (complex IV activity) multiplied by the MM factor of oxygen.
* The governing equations are shown in the Appendix with rate constants obtained from the literature
### Simulation protocols
* simulation with the published experiment by Takahashi et al. measured intracellular oxygen and intramitochondrial NADH gradients. rat cardiomyocytes
* simulate electrical pacing, we applied a current pulse (100 μA/cm², duration 0.5 ms)

## Results
### Validation of the oxygen diffusion model
![image](https://user-images.githubusercontent.com/40054455/123205237-197e2580-d4ec-11eb-988f-e348eaf8f41a.png)
* The simulated rate of oxygen consumption was 0.23 μM/ms, which is comparable to the rates observed experimentally (0.15 μM/ms in Fig. 2 C and 0.24 μM/ms in Fig. 2 D

### SSM and IFM responses to changes in contraction frequency
![image](https://user-images.githubusercontent.com/40054455/123205349-4af6f100-d4ec-11eb-8d83-70f8b9d4c121.png)
* Despite the higher NADH and inner membrane potential levels, IFM synthesized ATP at nearly the same rate as SSM. This strongly indicate a dominant effect of the local environment on the apparent functional differences between IFM and SSM

### Response to hypoxia
![image](https://user-images.githubusercontent.com/40054455/123205320-3f0b2f00-d4ec-11eb-9c5e-9f125ef3062e.png)
* Immediately below the sarcolemma, PO2 decreased to 0.042 mmHg because of the transportation barrier created by the sarcolemma, whereas in the core region, PO2 dropped to <10−5 mmHg
* proton pump activity in core IFM dropped to nearly zero, resulting in mitochondrial membrane potential deprivation, whereas SSM continued to function. ATPase activity dropped to minus values in core IFM
* creatine phosphate (CrP) decreased fairly rapidly, and after depletion ATP started to drop
* peak Ca2+ transient levels decreased after a latent peroid from depletion of SR Ca2+ content caused by depressed SR Ca2+-ATPase (SERCA) activity
### Comparing the hypoxic response of the hetero and equal models
![image](https://user-images.githubusercontent.com/40054455/123205358-4df1e180-d4ec-11eb-9dbd-845946b4764d.png)
* hetero (dotted line) and equal (solid line) models
* Under normoxic conditions, the contribution of SSM to ATP production was relatively small, only ∼9.5% in the equal model and 5.8% in the hetero model
* under hypoxic conditions, the role of SSM dramatically increased in both models, with >70% of ATP being produced in SSM in the later stage of hypoxia
* Regarding ATPase activity, IFM (especially outer IFM) showed less negative activity in the hetero model

## Discussion
### Validation of the model
* EC coupling validated previously[^Hatano2012]
* Oxygen and NADH gradients
### Effect of subcellular location on mitochondrial Ca2+ handling
* SSM showed lower Ca2+ levels, weaker NADH recovery, and higher ADP levels, indicating a dominant effect of the local environment
* IFM show higher Ca2+ accumulation, but species dependent
* But sarcolemmal Na+-Ca2+ exchanger distribution between the surface and t-tubules would change the mitochondrial Ca2+ environment
### Response to hypoxia
* steep oxygen gradients, core IFM stopped functioning and even started to consume ATP reserves, whereas in SSM function was upregulated
* ATP and CrP diffusion is fast enough to keep [ATP] constant throughout the cell under normoxic conditions
* ATP produced in SSM may preferentially serve to maintain the reactions of neighboring organelles and molecules, and sustain them for longer periods of time; contractile activity supported by IFM deteriorates quickly
### Possible differences in intrinsic properties between IFM and SSM
* IFM showed a higher NADH, inner membrane potential, and faster recovery after a change in the pacing frequency in the hetero model compared with the equal model
* the role of SSM in ATP production increased significantly under hypoxic conditions (upregulated by 5x)
### Study limitations
* Not including some components working in low-[ATP] conditions, i.e., glycolysis, adenylate kinase, acidosis, and ADP- and AMP-dependent reactions, including KATP channels and myosin ATPase
## Appendix
![eqn3 reaction-diffusion equation for oxygen](https://user-images.githubusercontent.com/40054455/86618469-8ce10b80-bfeb-11ea-8e27-962915f9f10d.png)
![tbla1](https://user-images.githubusercontent.com/40054455/86618474-8d79a200-bfeb-11ea-8fad-00819614d18f.png)

## Reference

[^Hatano2015]: Hatano A, Okada J, Washio T, Hisada T, Sugiura S. Distinct functional roles of cardiac mitochondrial subpopulations revealed by a 3D simulation model. Biophys J. 2015;108(11):2732-9. [PMC4457478](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4457478/).

[^Hatano2012]: Hatano A, Okada J, Hisada T, Sugiura S. Critical role of cardiac t-tubule system for the maintenance of contractile function revealed by a 3D integrated model of cardiomyocytes. J. Biomech. 2012;45(5):815-823. doi:10.1016/j.jbiomech.2011.11.022.
