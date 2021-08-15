---
title: "Goldberg 2017 : Emerging whole-cell modeling principles and methods"
subtitle: ""
date: 2021-04-08T16:53:04+08:00
author: "Goldberg et al."

series: ["review"]
categories: ["Reading"]

hiddenFromHomePage: false
hiddenFromSearch: false

featuredImage: ""
featuredImagePreview: ""

toc:
  enable: true
lightgallery: false
---

[Sciwheel](https://sciwheel.com/work/#/items/4651953/) [^1]

[^1]: Goldberg AP, Szigeti B, Chew YH, Sekar JA, Roth YD, Karr JR. Emerging whole-cell modeling principles and methods. Curr Opin Biotechnol. 2018;51:97–102.[PMC5997489](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5997489/)

Whole-cell (WC) computational models aim to predict cellular phenotypes from genotype and the environment by representing the function of each gene, gene product, and metabolite.

<!--more-->

We propose that WC models aim to represent all of the chemical reactions in a cell and all of the physical processes that influence their rates

- the **sequence** of each chromosome, RNA, and protein
- the **structure** of each molecule
- the **subcellular organization** of cells into organelles and microdomains
- the participants and effect of each **molecular interaction**
- the **kinetic parameters** of each interaction
- the **concentration** of each species in each organelle and microdomain
- the concentration of each species in the **extracellular environment**

The things WC models aim to proedict:

- **stochastic dynamics** of each molecular interaction
- **temporal dynamics** of the concentration of each species
- **spatial dynamics** of the concentration of each species in each organelle and microdomain
- complex **phenotypes** such as cell shape, growth rate, motility, and fate, as well as the **variation** in the behavior of single cells within clonal populations

enables WC models to generate predictions that could be embedded into higher-order multiscale models.

![Fig 1](https://user-images.githubusercontent.com/40054455/113998198-69553500-988b-11eb-8512-b84feb08c3db.png)

## AVAILABLE RESOURCES

WC models require a ton of parameters.

### Measurement methods

single-cell and genomic measurement

- Meth-Seq ([genomewide DNA methylation analysis](https://pubmed.ncbi.nlm.nih.gov/20125086/).)
- Hi-C ([chromosome structures](https://pubmed.ncbi.nlm.nih.gov/23657480/))
- ChIP-seq ([protein-DNA interactions](https://pubmed.ncbi.nlm.nih.gov/19736561/))
- fluorescence microscopy: protein localizations
- mass-spectrometry: metabolite and protein concentrations
- FISH and scRNA-seq: dynamics and single-cell variation of RNA abundances

### Data repositories

[A list of public repositories](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5997489/bin/NIHMS928198-supplement.xlsx) (in Excel file).

### Prediction tools

However, many current prediction tools lack sufficient accuracy for WC modeling.

### Published models

[A list of public model repos](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5997489/bin/NIHMS928198-supplement.xlsx) (in Excel file).

### Emerging methods and tools, Data aggregation and organization

![Fig2](https://user-images.githubusercontent.com/40054455/113999412-9bb36200-988c-11eb-81be-ac4fbc4a6f23.png)

- (a) Data should be aggregated from thousands of publications, repositories, and prediction tools and organized into a PGDB. (e.g.  [Pathway Tools](https://pubmed.ncbi.nlm.nih.gov/26454094/), [Whole Cell KB](https://pubmed.ncbi.nlm.nih.gov/23175606/))
- (b) Models should be designed, calibrated, and validated from PGDBs and described using rules.
- (c) Models should be simulated using parallel, network-free, multi-algorithmic simulators and their results should be stored in a database.
- (d) Simulation results should be visualized and analyzed.
- (e) Results should be validated by comparison to experimental measurements. Importantly, all of these steps should be collaborative.

### Scalable model design

- [Cell Collective](https://pubmed.ncbi.nlm.nih.gov/23549147/)
- [MetaFlux](https://pubmed.ncbi.nlm.nih.gov/22262672/)
- [PySB](https://pubmed.ncbi.nlm.nih.gov/23423320/)
- [SEEK](https://www.ncbi.nlm.nih.gov/pubmed/26160520/)
- [Virtual Cell](https://www.ncbi.nlm.nih.gov/pubmed/22139996/)

### Model languages

- [SBML](https://www.ncbi.nlm.nih.gov/pubmed/12611808/)
- [BioNetGen](https://www.ncbi.nlm.nih.gov/pubmed/27402907/)

### Simulation tools

- [COPASI](https://www.ncbi.nlm.nih.gov/pubmed/19399433/)
- [Virtual cell](https://www.ncbi.nlm.nih.gov/pubmed/22139996/)
- [COBRAPy](https://www.ncbi.nlm.nih.gov/pubmed/23927696/)
- [E-Cell](https://scholar.google.com/scholar_lookup?journal=Rev+Cell+Biol+Mol+Med&title=E-Cell:+Computer+simulation+of+the+cell&author=PK+Dhar&author=K+Takahashi&author=Y+Nakayama&author=M+Tomita&publication_year=2012&)


### Calibration

- [saCeSS](https://www.ncbi.nlm.nih.gov/pubmed/28109249/) : distributed calibration of large biochemical models
- surrogate models to calibrate large models

### Verification

- [BioLab](https://scholar.google.com/scholar_lookup?journal=Int+Conf+Comput+Meth+Syst+Biol&title=Statistical+model+checking+in+BioLab:+Applications+to+the+automated+analysis+of+T-cell+receptor+signaling+pathway&author=EM+Clarke&author=JR+Faeder&author=CJ+Langmead&author=LA+Harris&author=SK+Jha&publication_year=2008&pages=231-250&)
- [PRISM](https://scholar.google.com/scholar_lookup?journal=Computer+Aided+Verification&title=PRISM+4.0:+Verification+of+probabilistic+real-time+systems&author=M+Kwiatkowska&author=G+Norman&author=D+Parker&publication_year=2011&pages=585-591&)

### Simulation results analysis

- COPASI
- Virtual Cell
- WholeCellSimDB and WholeCellViz

## TECHNOLOGICAL CHALLENGES

- Experimental measurement: Measuring kinetic parameters at the interactome scale.
- Prediction tools: Accurately predict the molecular effects of insertions, deletions, and structural variants.
- Data aggregation
- Scalable, data-driven model design
- Rule-based model representation: No existing language supports all of the biological processes that WC models must represent.
- Scalable multi-algorithmic simulation
- Calibration and verification
- Simulation analysis
- Collaboration

## Highlights

- Whole-cell models predict phenotype from genotype by representing each gene function
- Whole-cell models could transform bioscience, bioengineering, and medicine
- There are many challenges to achieve whole-cell models
- New measurement and modeling technologies are rapidly enabling whole-cell modeling
- Ongoing efforts to build scalable modeling tools will accelerate whole-cell modeling
