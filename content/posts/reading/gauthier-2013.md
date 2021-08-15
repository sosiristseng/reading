---
title: "Gauthier 2013 : An integrated mitochondrial ROS production and scavenging model: implications for heart failure"
date: 2020-10-23T00:01:05+08:00
series: ["ODE", "mitochondria", "ROS", "cardiomyocyte"]
categories: ["Reading"]
author: "Gauthier et al."
math:
  enable: true
lightgallery: true
---

From the series of articles:

* Gauthier2013A: [Sciwheel](https://sciwheel.com/work/#/items/2897916). [Article](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3882515/)
* Gauthier2013: [Sciwheel](https://sciwheel.com/work/#/items/1239950). [Article](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3752118/)
* Kembro2013: [Sciwheel](https://sciwheel.com/work/#/items/1269530). [Article](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3552263/)

<!--more-->


## Introduction

* heart failure (HF): increased mitochondrial reactive oxygen species (ROS) production (4) and decreased antioxidant capacity
* regulation of ATP is carried out by ADP and Ca2+ signals
* Cytosolic Na+ levels have been shown to be elevated in HF (9–11), and contribute to mitochondrial ROS production (less Ca_mt => less NADH and NADPH => more ROS)

## Methods

### Model description
* ETC-ROS model`[Gauthier2013]`
    * scaling ROS production according to Aon et al.
    * slight changes to complex I for the cellular model
* ME-R model`[Kembro2013]` for ROS scavenging

![image](https://user-images.githubusercontent.com/40054455/125473151-d9a0b635-9c24-41d0-8f5f-e8d112e91fbb.png)

### Computational methods
* 37 nonlinear ordinary differential equations, MATLAB, CVODE

### Model integration
* add explicit dependence on succinate and malate and inhibition by oxaloacetate to the equation for succinate dehydrogenase
* state 4 respiration (energized with substrates, but in the absence of ADP) vs state 3 respiration (energized with substrates in the presence of ADP)
![tbl1](https://user-images.githubusercontent.com/40054455/86617944-a0d83d80-bfea-11ea-9687-d563e2f4e650.png)

### Parameter fitting for mitochondrial model in the myocyte
To reproduce kinetic data on ROS emission from isolated myocytes, some parameters were refit
* **NADP+ (IDH2)** was refit using in vitro parameters from Popova et al. 2007
* The **random bi-bi** enzyme kinetics model describing the activity of the **THD** based on the randomly ordered binding of two substrates and the randomly ordered unbinding of two products presented in Kembro et al. was modified to satisfy the thermodynamic constraint from Sazanov and Jackson
* Kinetic parameters for **glutathione peroxidase (GPX)** were refit to improve GSH sensitivity as compared to GSH-dependence data from Aon et al. 2010
* Michaelis-Menten constant of **glutathione reductase (GR)** for NADPH was increased to improve sensitivity over the range of observed NADPH values in the model

### Stimulus protocols
* [Ca2+]i transients were simulated as rectangular pulses of Ca2+ diastolic level of 0.1–1 μM with a width of 200 ms
* Cytosolic ADP was increased from a basal level of 0.1–1.0 mM with a time constant of 2 min to simulate the energy consumption by the contractile machinery in the cytosol
* For the myocyte model simulations, pH and mitochondrial phosphate were held constant.
    * PiC and NHE do not go well with whole cell model
    * Matrix phosphate not buffered
    * Other pathways of proton leak

## Results

### Altered Ca2+ regulation by Ru360 increases ROS
![image](https://user-images.githubusercontent.com/40054455/125473227-534d095b-1825-4481-9820-bf66a1336a34.png)


* if mitochondrial Ca2+ regulation is altered by a decrease in mCU flux, mitochondrial Ca2+ uptake is then severely compromised, as shown in the model (Fig. 2 C, black) and in experiment
![image](https://user-images.githubusercontent.com/40054455/125473237-a393fb29-cab4-4ce3-b79b-644c2d850160.png)

* NADH becomes oxidized, decreasing NADPH levels, GSH becomes more oxidized; TrxR and Trx are similar.
![image](https://user-images.githubusercontent.com/40054455/125473251-c8e545aa-8df0-4398-9510-93cf49e91e1b.png)
* Elevated [Na+]i increases ROS levels
![image](https://user-images.githubusercontent.com/40054455/125473264-c410c4e7-a0f9-4a6a-8641-54cc47ee5e7e.png)

* Elevated [Na+]i limits mitochondrial Ca2+ uptake and depletes scavengers
![image](https://user-images.githubusercontent.com/40054455/125473283-9c66f9a3-7df1-4291-a715-97c6147420ba.png)

* Block of mNCE with CGP reduces ROS overflow in high [Na+]i conditions.
![image](https://user-images.githubusercontent.com/40054455/125473311-17e0245f-94b1-4dbf-bf64-078cb2319054.png)


### Increased GSH pool reduces ROS overflow
![image](https://user-images.githubusercontent.com/40054455/125473325-b46da903-e066-46bd-a0b3-29603cd2e31a.png)
![image](https://user-images.githubusercontent.com/40054455/125473354-5bb71287-4891-4ce3-9c41-e84728f69768.png)

## Discussion
### Model predictions

* NADH levels drop for the mCU inhibition and elevated [Na+]i protocols, NADPH becomes more oxidized than NADH and the GSH and Trx scavenging systems become compromised.  (PMF)-dependence and reversibility of the THD are key to this behavior
* αKGDH plays a larger part in NADH control than IDH
* The absolute concentrations of GSSG and GSH are more important in analyzing the enzyme kinetics of the scavenging reactions. the amount of increase in H2O2 after onset of pacing is very sensitive to the total amount of GSH and GSSG available for pools near 1 mM
* Deficiencies in either pathway ( Trx and GSH ) can be partially compensated by the other, but both depend on NADPH supply.
* ETrx remains more negative than EGSH, reflecting a greater reducing potential for Trx compared to GSH

### Cellular control of ROS production
* separating the role of ROS production from the role of ROS scavenging presents a challenge.
* ROS production for the 90% mCU inhibition and elevated [Na+]i protocols will decrease after the workload transition, due to NADH oxidation and ΔΨ depolarization that occur during ADP addition.
* Older model: ROS from unstable semiquinone (SQ) on the cytosolic-side quinone binding site of complex III
  Alternatively: O2 gain reduced from transient SQ,  from reduced heme bL (more consistent with experiment, that SQ is rare)
* corrects the legacy value of 10 mM total NAD+/NADH pool from Magnus and Keizer to the 1 mM value used in Wei et al.
    * better control of NAD+- and NADH-dependent TCA cycle enzymes
    * good agreement with the ≈0.82 mM NAD pool measured
* the ROS production model used here still requires a highly reduced Q pool. Not consistent with measurements (bell-shaped dependence)

### Previous modeling and critique of the model
* builds on the well-validated scavenging network of Kembro et al. (17), but with dynamic ROS production adapted from Gauthier et al
* Achieving quantitative agreement between the model and the experimental data is hindered by the inability to calibrate experimental fluorescence signals representing some signaling components and the inability to measure other components at all
    * Q pool redox state is difficult to monitor continuously
    * The ROS production component of the cellular model is difficult to validate experimentally
    * Much remains unknown about the mitochondrial environment within the cel
* Changes in ATP, Pi, pH, and the pmf will affect the other ionic species of the mitochondria (Ca2+, Na+, H+) via the mitochondrial ion circuits
    * PiC, mNCE, and mNHE
    * The model break in the cellular model @ high pacing freqs, clamped in thses simulations
* Other processes are still unaccounted
    * β-adrenergic activation and mitochondrial isoform of PKA (cAMP-dependent) regulation of C1 and C4
    * redox modulation of transporters
    * exponential dependence of IMM conductance
    * mitochondrial volume dynamics and potassium dynamics
* These simulations do not represent a comprehensive analysis of all the processes involved in HF.

## A computational model of reactive oxygen species and redox balance in cardiac mitochondria
Gauthier, 2013

### redox-optimized ROS balance (R-ORB) hypothesis
* ROS levels are minimized in an intermediate cellular redox environment,
* Energy output is maximal
* Substrate -> NADH -> NADPH -> GSH -> Trx
* Too reduced: high level of reduction of the ETC complexes => increases ROS emission
* Too oxidized: decrease in NADPH and ROS scavenging capacity => increases ROS emission

### ROS from complex I
* FMN cluster in the hydrophilic arm
* Q-site at the interface of the protein’s matrix and membrane domains

### ROS from complex III
* ROS release to both sides of the IMM
* High ROS production from complex III occurs during forward electron transport (FET).

## Methods
### Model description
* complexes II–IV were modified from Demin et al.
* A thermodynamic model of complex I was constructed (see Fig. 1 B) based on the whole ETC model of Magnus and Keizer; rate constants were parameterized to match respiration and ROS production data from Aon et al.
* 23 parameters were obtained from experimental results or previous models and 39 parameters were adjusted based on experimental data
![image](https://user-images.githubusercontent.com/40054455/125473813-fd292288-40cb-48f9-bf31-90af1bcf431b.png)

### Model reconstructions
![image](https://user-images.githubusercontent.com/40054455/125473822-c94db45a-ffa1-4865-a755-5d22cca3e2af.png)
* The ETC model presented here includes variables describing the concentrations of ubiquinone, ubiquinol, and ubisemiquinone, along with the oxidation states of cytochrome c and the redox centers in complex III
    * high- and low-potential b-hemes (bH and bL) & cytochrome c1
* the reduction in the ubiquinone redox potential that occurs at higher ΔΨm as the concentration of ubiquinone (Q) falls and ubiquinol (QH2) increases
* rat heart maintains a lower NAD+/NADH ratio from 1 to 16 (38,39), liver attains ratios from 30 to 100
* typical ΔΨm-dependent reduction of the b-hemes, the increased reduction of bL plays a critical role in the mechanism of complex III ROS production in the model.
* ΔΨm dependence of the redox states of cytochromes c1 and c: oxidation of cytochrome c1 and c increases with ΔΨ over the range 150–180 mV. [ATP]/[ADP]-ratio-induced inhibition of complex IV?

### Control of ROS production
![image](https://user-images.githubusercontent.com/40054455/125473831-19ae4091-a435-46ac-8586-a99f6f6dbe21.png)
* When complex I rates are fitted to guinea pig cardiac mitochondrial data from Aon et al
* ROS production in complex III exhibits higher rates for state 4 than for state 3
* For the RET conditions in state 4 in the presence of succinate, 72% of ROS production is derived from complex I
* mitochondrial succinate levels have been measured at 0.3 mM (45), much lower than the 4–10 mM used to induce RET (9,15,22) in isolated mitochondria, and that complex I substrates are always present in cells, it is unlikely that physiological conditions favor RET in vivo under nonischemic conditions

## Model predictions
### Control of ROS production
![image](https://user-images.githubusercontent.com/40054455/125473839-f4c22892-4164-487b-b087-e0b3bfa5d22e.png)
* ROS production has been shown to be highly dependent on ΔΨm, in state 4, succcinate oxidation.
* Reduction of cyt b-hemes as ΔΨm increases.
* Decreasing ΔΨm using an uncoupler would also be expected to oxidize the overly-reduced NAD+/NADH couple, the decrease in ROS shown in Fig. 4 is consistent with the R-ORB hypothesis

![image](https://user-images.githubusercontent.com/40054455/125473849-143ebece-2500-4207-a607-e0aa43160aaf.png)
* ROS production from complexes I and III during FET increases with matrix alkalinization
* RET-derived ROS production from complex I also exhibits matrix pH dependence
* Under state 3 respiration, in the presence of succinate, an increase in matrix pH will elevate complex-I-derived ROS
#### Control of ROS production by respiratory blockers
![image](https://user-images.githubusercontent.com/40054455/125473866-daf91e0d-a7e9-462b-9e92-611d510ffb94.png)

#### Interplay of ROS production and scavenging systems
![image](https://user-images.githubusercontent.com/40054455/125473876-2458373f-849b-4eaf-8e22-3baedb90c306.png)
* U-shaped dependence of ROS levels on redox environment follows closely that proposed in the R-ORB hypothesis
* Model ΔΨm at this redox optimum is 152 mV, similar to the nearly minimal ROS production at 153 mV observed by Korshunov

## Discussion
* This model is shown to reproduce
    1. experimental data measuring the ΔΨ dependence of the redox potential of the Q pool and the oxidation states of the b-hemes and cytochromes c1 and c
    2. experimental results describing the dependence of the respiratory flux from complex I or complex II substrates on ΔΨm
    3. measurements of ROS production as a function of substrate concentration and ΔΨm
* This model predits dependence of ROS production on ΔΨ, matrix pH, NAD+/NADH redox potential, and inhibition of complexes I and III

* Detailed description of redox-dependent electron transport processes in the model
* Although the model of complex I does not include explicit electron transfer reactions like the complex III model, each state transition does have a mechanistic basis.

* The explicit inclusion of reactions requiring **protons** leads to some interesting predictions regarding the **pH dependence** of ROS production.
* The complex I model was constrained using the data from Aon et al. some difference of ROS producing rate from others's experiments.

### Validation of the redox-optimized ROS balance hypothesis
* The presence of a minimum in H2O2 emission at an intermediate redox environment and the 1:4 ratio of H2O2 emission for the maximally reduced environment in this protocol compared to the most oxidized environment is in good agreement with the experimental data of Aon et al.
* ΔΨm between 150 and 155 mV, similar to state 3 ΔΨm values for isolated mitochondria (9) and to the ΔΨm value shown by Korshunov et al. However, this ΔΨm range is higher than the typical mitochondrial operating conditions in vivo, which are closer to 100–130 mV.
* R-ORB hypothesis, shows the importance of the interplay between ROS production and scavenging

### Mechanism of ROS production from complex I
* Complex I ROS production was modeled as originating from a redox center in the hydrophilic arm of the protein,  generalized implementation of the hypothesis. => FMN site (IF)
* In the absence of ubiquinone or ubiquinol, the model predicts a dependence of ROS production on NADH redox potential.
* the midpoint potential of this NADH dependence closely matches the two-electron reduction potential of the complex I FMN
* complex I’s quinone-binding site (IQ) ?
    * The model described here was modified to test this Q-linked ROS production hypothesis by removing the superoxide-generating reaction connecting states 4 and 2 of the complex I model (see Fig. 1 B) and replacing it with a reaction connecting state 7 (reduced enzyme bound to Q) to state 2
    * the ability of the Q-linked ROS production model to reproduce the data were very similar
    * this modeling experiment was unable to distinguish between the two mechanisms.

### Mechanism of ROS production from complex III
* reduction of oxygen by the cytosol-side semiquinone radical from a highly reduced ubiquinone pool and high proton motive force

#### Alternative proposals: Little semiquinone, reduced bL to transfer electrons to O2 instead
* Dröse and Brandt: Bell shaped dependence (max Vsox for Q pool is 25% oxidized). Reduced heme bL to oxidized ubiquinol to form a **transient semiquinone**, which reduces oxygen to form superoxide
* Borek et al: ROS production without a significant accumulation of semiquinone at the Qo site
* may lead to different ΔΨ dependence of the electron carrier redox states
* **subject to further refinements**

## Critique of the model
* The model presented here only accounts for superoxide release from the **Qo site**
    * semiquinone at Qi is considered thermodynamically stable
    * the concentration of semiquinone at Qi does increase with membrane potential as well as matrix alkalinization

* The **complex IV** model included here is a relatively simplistic description of an enzyme with a wide variety of properties
    * allosteric ATP inhibition
    * variable Km for O2
    * intrinsic uncoupling at high ΔΨm
* disparity in cytochrome c oxidation due to complex IV issues

## Integrating mitochondrial energetics, redox and ROS metabolic networks: a two-compartment model

### Introduction
Kembro et al.
![image](https://user-images.githubusercontent.com/40054455/125474113-a53ced18-d596-44af-814d-1fe1dd7aa503.png)
* mitochondrial energetic-redox (ME-R) model
    * four main redox couples (NADH/NAD+, NADPH/NADP+, GSH/GSSG, Trx(SH)2/TrxSS).
        * 2 of 3 mitochondria-dependent NADPH-producing mechanisms
    * Scavenging systems—glutathione, thioredoxin, superoxide dismutase, catalase
    * Both mitochondrial matrix and extra-matrix compartments
    * Transport between compartments of ROS species (SOX and H2O2) as well as GSH
* The model is able to simulate:
    * shape and order of magnitude of H2O2 emission and dose-response kinetics with inhibitors of the GSH or Trx scavenging systems
    * steady and transient behavior of ΔΨm and NADH
* The mode stems from previous models[^Wei2011][^Cortassa2004]

### Kinetic modeling of the antioxidant defenses
Model parameters: https://www.cell.com/biophysj/fulltext/S0006-3495(12)05055-2

### Thioredoxin system
* Thioredoxin reductase (TrxR1 extra-matrix, and TrxR2 mitochondrial): bisubstrate MM (similiar to glutathione reductase)
* Peroxiredoxin (Prx): Dalziel kinetics

### Glutathion system
* glutathione peroxidase (GPx) and glutathione reductase (GR): ditto

### NADPH-generating systems
* NADP-dependent IDH2:  eversible reaction ruled by Michaelis-Menten kinetics with two-substrates according to the mechanism proposed by O’Leary and Limburg
* proton-coupled THD: The THD activity was modeled according to the mechanism proposed by Hoek and Rydstrom[^Hoek1988] and Sasanov and Jackson[^Sazanov1994]

### Exp methods
* guinea pig heart mitochondria

### Assay of mitochondrial respiration
* mitochondrial respiration: Seahorse[^Aon2012]
* bioenergetic variables and ROS detection: wavelength scanning fluorometer (Quantamaster)
    * NAD(P)H: 340nm -> 450nm
    * ΔΨm: TMRM; 100 nM
    * H2O2: Amplex Red
### Results
![image](https://user-images.githubusercontent.com/40054455/125474155-7d0f57b5-1fcb-4b31-b3bb-c4d83670a8be.png "Energetic-redox transitions: time-dependent and steady-state behavior")
* EXP: NADH and ΔΨm attain maximal values of 100% reduction and ∼170 mV, respectively.
* Model: 96% NADH and ΔΨm ∼193 mV

#### Experimental and modeling results of respiration, maximal H2O2 emission (after inhibition of GSH/Trx systems), ΔΨm and NADH in isolated heart mitochondria from guinea pig
Table2: https://www.cell.com/action/showFullTableHTML?isHtml=true&tableId=tbl2&pii=S0006-3495%2812%2905055-2

![image](https://user-images.githubusercontent.com/40054455/125474487-656a8cbd-ad46-4f87-963a-a23883a2ef1e.png "Dynamic response")

* EXP: As a caveat, the range of ΔΨm monitored by TMRM extends from 130–140 mV to ∼220 mV
* Model: Following ADP addition, ΔΨm depolarizes 20 mV (from 170 to 150 mV) and NADH oxidizes, able to reproduce the overall dynamic profile of NADH and ΔΨm observed experimentally

![image](https://user-images.githubusercontent.com/40054455/125474536-41c7acc9-9d50-4370-bda3-23795e689aca.png "Dynamic response to ADP pulses")

![image](https://user-images.githubusercontent.com/40054455/125474613-2ec944f8-0f99-4711-b73c-64ba340a604f.png "Uncoupler-elicited transitions")

Increase vO2, decrease in ΔΨm and NADH

### ROS and antioxidant systems
GSH/Trx systems continuously scavenge ROS produced in the respiratory chain, thereby **decreasing the rate of H2O2 emission** typically observed in isolated mitochondrial studies under conditions of forward electron transport (FET).

![image](https://user-images.githubusercontent.com/40054455/125474681-8589661c-6dfa-4693-85fe-dce63cfa3a69.png "Dose-response relationships")

Selective inhibition of TrxR with auranofin (AF) (42), or depletion of GSH with 2,4 dinitrochlorobenzene (DNCB)

### Steady-state behavior of the redox environment
![image](https://user-images.githubusercontent.com/40054455/125474767-ec76bf66-a97f-41aa-aa6f-8ae0ef519b50.png)

* NADH/NAD+, NADPH/NADP+, GSH/GSSG, and Trx(SH)2/ TrxSS
* relationships between redox couples and substrates:
    ![image](https://user-images.githubusercontent.com/40054455/125475118-a5ca4c08-64e4-4094-a7e5-c2248cad34ad.png)
* In our model, the total GSH concentration has been adjusted to the mM range (1–3 mM) in the matrix. NADH/NAD+ is mainly to fuel energy provision through the respiratory chain, whereas NADPH/NADP+ contributes electrons to the antioxidant system, however, αKG/ISOC ratio linked to NADPH via IDH2, and THD.

## Discussion
* a two-compartment computational model of energetic-redox-ROS metabolism, combined with experimental validation.

### Able to:
1. steady-state behavior of ΔΨm and NADH during transitions from deenergized to energized states elicited by gradual **G/M** addition
2. The transient ΔΨm and NADH dynamics accompanying the state 4 to 3 transition in mitochondrial respiration by single and mutiple **ADP** addition
3. The response of mitochondrial respiration and energetic-redox variables (ΔΨm, NADH) upon titration with an **uncoupler**
4. The overall kinetics of H2O2 emission rates after titration experiments performed in mitochondrial suspensions with inhibitors of the GSH/Trx scavenging systems
5. The model is able to simulate oscillatory dynamics (RIRR) in agreement with the mechanism described previously
6. Duplication of antioxidant defense systems in multiple compartments can be viewed as an efficient salvage mechanism in response to oxidative bursts

### Compartmentation, dynamics, and interdependence of redox metabolism
Redox couples are interdependent systems
* NADH <-> NADPH -> GSH -> Trx
* GSH and Trx scavenging systems exhibit a well-orchestrated interaction, functionally relieving each other when the antioxidant capacity of either is overwhelmed
* SOX generation at electron carriers will be kinetically controlled, most SOX production takes place in the mitochondrial electron transfer chain and is restricted to the complexes that handle the most reduced thermodynamic potentials (complex I and III)
* The present ME-R model with antioxidant arrays in both compartments renders O2⋅− and H2O2 levels in the pM to nM range
* In different cellular compartments, different redox states are present. The bulk of NADP is present as NADPH in liver mitochondria.

* Prev EXP: partial GSH depletion triggers cell-wide mitochondrial oscillations in intact cardiomyocytes.

### The redox environment and energy metabolism
Redox-optimized ROS Balance model: under high energy demand, and despite large respiratory rates, ROS emission levels are kept to a minimum by ROS scavenging systems.
* extends the role of **NADH** beyond its well-known function as an intermediary between substrate catabolism and ΔΨm.

### Previous modeling and model limitations
* SOX generation = a fraction of vO2 (shunt) => unable to simulate the increase in ROS levels when mitochondria evolve into state 4 respiration (high pmf)
* K+ movements are not taken into account
* a linear instead of an exponential dependence of the leak current on ΔΨm
* experimental system corresponds to the average behavior of a heterogeneous mitochondrial population
* does not consider NADH transfer from the cytoplasm into mitochondria or the flow of NADPH from mitochondria (no shuttle for these)
* deterministic model: simple, law of big numbers prevails over stochastic fluctuations
