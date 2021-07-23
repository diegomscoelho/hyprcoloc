# HyPrColoc
Hypothesis Prioritisation in multi-trait Colocalization (HyPrColoc).

Genome-wide association studies (GWAS) have identified thousands of genomic regions affecting complex diseases. The next challenge is to elucidate the causal genes and mechanisms involved. One approach is to use statistical colocalization to assess shared genetic aetiology across multiple related traits (e.g. molecular traits, metabolic pathways and complex diseases) to identify causal pathways, prioritize causal variants and evaluate pleiotropy.

HyPrColoc is an efficient deterministic Bayesian divisive clustering algorithm using GWAS summary statistics that can detect colocalization across vast numbers of traits simultaneously.

## Functions
* hyprcoloc - identifies clusters of colocalized traits and candidate causal SNPs using the HyPrColoc Bayesian divisive clustering algorithm.

## Installation
1. install.packages("devtools")
2. library(devtools)
3. install_github("jrs95/hyprcoloc", build_opts = c("--resave-data", "--no-manual"), build_vignettes = TRUE)
4. library(hyprcoloc)
5. browseVignettes("hyprcoloc")

## Example
\# Regression coefficients and standard errors from ten GWAS studies (Traits 1-5, 6-8 & 9-10 colocalize)  
betas <- hyprcoloc::test.betas  
head(betas)  
ses <- hyprcoloc::test.ses  
head(ses)  
  
\# Trait names and SNP IDs  
traits <- paste0("T", 1:10)  
rsid <- rownames(betas)  

\# Colocalization analysis  
hyprcoloc(betas, ses, trait.names=traits, snp.id=rsid)  

## Citations
* HyPrColoc: Foley CN, Staley JR, et al. A fast and efficient colocalization algorithm for identifying shared genetic risk factors across multiple traits. Nat Commun 2021; 12(1):764.
* HyPrColoc software: Foley, CN and Staley JR. (2020, November 27). cnfoley/hyprcoloc: First release of software (Version v1.0.0). Zenodo. http://doi.org/10.5281/zenodo.4293559
* LD blocks: Berisa T & Pickrell JK. Approximately independent linkage disequilibrium blocks in human populations. Bioinformatics 2016; 32(2):283-285.
