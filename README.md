# Bayesian Network Analysis of *Streptococcus suis* Antimicrobial Resistance

This repository contains reproducible code, a simplified de-identified dataset, and documentation for the Bayesian network analysis conducted to examine patterns of phenotypic antimicrobial resistance (AMR) in *Streptococcus suis* isolates originating from U.S. swine production systems.

This repository accompanies the manuscript:

**Bayesian network models to assess antimicrobial resistance patterns of Streptococcus suis isolated from swine production systems in the United States between 2014-2021.**  
Authors: Ruwini Rupasinghe#, Brittany L Morgan Bustamante#, Rebecca C Robbins, Maria J Clavijo, Beatriz Martínez-López+

+Corresponding author
E-mail: beamartinezlopez@ucdavis.edu

#These authors contributed equally to this work.

## Overview of the Analysis

This project uses Bayesian network analysis (BNA) to:

- identify conditional dependencies among phenotypic AMR classifications,
- quantify co-resistance and co-susceptibility patterns,
- assess structural robustness using bootstrap resampling (10,000 iterations),
- evaluate the effect of alternative intermediate classification through sensitivity analysis.

The analysis is implemented using the **bnlearn** R package and includes:

1. Data cleaning and preprocessing  
2. Structure learning using tabu search  
3. Bootstrap arc strength estimation  
4. Consensus DAG construction  
5. Conditional probability querying (`cpquery`)  
6. Sensitivity analysis  
7. Network visualization

## Data

The file `ssuis_simplified.csv` contains a de-identified dataset for demonstration and reproducibility. It includes:

- phenotypic AMR classifications (S, I, R),
- year of the sample

This dataset is intended to illustrate the workflow and will not reproduce the exact results presented in the manuscript.

## How to Run the Analysis

### 1. Clone the repository

```bash
git clone https://github.com/yourusername/ssuis-bayesian-network.git
cd ssuis-bayesian-network
```

### 2. Install required R packages

```r
install.packages(c(
  "bnlearn", "dplyr", "tidyr", "ggplot2",
  "ggraph", "igraph", "writexl"
))
```

### 3. Run the main analysis script

```r
source("scripts/01_bn_analysis.R")
```

Or knit the full analysis:

```r
rmarkdown::render("manuscript/analysis_markdown.Rmd")
```

## Outputs

The analysis generates:

- a consensus Bayesian network DAG,
- bootstrap-strength plots,
- conditional probability summaries,
- a sensitivity analysis DAG (intermediate→resistant),
- all figures presented in the manuscript and supplemental material

## Notes and Limitations

- The underlying surveillance data do not include animal-level or farm-level risk factor variables; therefore, these were not modeled.  
- All data provided here are de-identified and simplified to preserve confidentiality and enable reproducibility.  
- Results from the simplified dataset will differ from those in the manuscript but preserve the analytical workflow and structure.
