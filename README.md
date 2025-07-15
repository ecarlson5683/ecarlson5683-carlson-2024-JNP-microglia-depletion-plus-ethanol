# carlson-2024-JNP-plx-ethanol

## Overview 
This repository contains data and code used for the analyses presented in the manuscript titled "Pharmacological depletion of microglia protects from alcohol-induced corticolimbic neurodegeneration in male rats" (Carlson, Melbourne, and Nixon, 2025, *Journal of Neuroimmune Pharmacology*).

The RMarkdown document titled "MGD_Analyses.Rmd" includes R code to:
- Read cell count (Iba1+ for microglia or FJB+ for dying neurons) data
- Conduct two-way ANOVA on cell count data with drug (PLX5622 vs vehicle) and diet (ethanol vs control) as between-subjects factors along with pairwise comparisons of simple effects with Bonferroni correction when appropriate.
- Read data related to intoxication behavior, ethanol dose, and blood ethanol concentrations and conduct Welch t-tests.

## Dependencies
The following packages are required to run this code and can be installed using `install.packages("<package>")`:
- {tidyverse}
- {afex}
- {emmeans}
- {rstatix}

## ***data*** Directory
The ***data*** directory includes the following files:
- **intoxication.csv**: Contains behavioral intoxication scores for each dosing session (every 8 h) with the following variables (n = 18, 8 PLX-EtOH and 10 VEH-EtOH):
  - Subject: individual id number
  - Condition: treatment group in drug-diet format; vehicle (VEH), PLX5622 (PLX), ethanol diet (EtOH), control diet (CON); e.g., PLX-EtOH
  - Sex
  - Study: cohort id
  - PLX_admin: route of administration for vehicle or PLX
  - dose_01 to dose_12: behavioral intoxication scores for each dosing session
- **dose.csv**: Contains ethanol dose (g/kg) given in each dosing session (every 8 h) with the following variables (n = 18, 8 PLX-EtOH and 10 VEH-EtOH):
  - Subject: individual id number
  - Condition: treatment group in drug-diet format; vehicle (VEH), PLX5622 (PLX), ethanol diet (EtOH), control diet (CON); e.g., PLX-EtOH
  - Sex
  - Study: cohort id
  - PLX_admin: route of administration for vehicle or PLX
  - dose_01 to dose_12: ethanol dose (g/kg) for each dosing session
- **BEC.csv**: Contains blood ethanol concentrations determined from tail blood collected 90 min following the 7th dose of ethanol (n = 18, 8 PLX-EtOH and 10 VEH-EtOH):
  - Subject: individual id number
  - Condition: treatment group in drug-diet format; vehicle (VEH), PLX5622 (PLX), ethanol diet (EtOH), control diet (CON); e.g., PLX-EtOH
  - Sex
  - Study: cohort id
  - PLX_admin: route of administration for vehicle or PLX
  - run_01, run_02: BEC measurements run in duplicate
- **Iba1_raw_ERC.csv**: Contains output of ImageJ macro (Iba1+ cell counts; ERC naming convention) with the following variables:
  - Slice: Image name
  - Count: Iba1+ cell count
  - Total Area: 
  - Average Size:
  - %Area:
- **Iba1_raw_JM.csv**: Contains output of ImageJ macro (Iba1+ cell counts; JM naming convention) with the following variables:
  - Slice: Image name
  - Count: Iba1+ cell count
  - Total Area:
  - Average Size:
  - %Area:
- **MGD_subjects.csv**: Contains meta data for Iba1 analysis with the following variables:
  - Subject: individual id number
  - Condition: treatment group in drug-diet format; vehicle (VEH), PLX5622 (PLX), ethanol diet (EtOH), control diet (CON); e.g., PLX-EtOH
  - Sex
  - Study: cohort id
  - PLX_admin: route of administration for vehicle or PLX
  - Region: brain region
- **FJB.csv**: Contains FJB+ cell counts averaged across brain-region-containing slice (section) with the following variables:
  - Subject: individual id number
  - Condition: treatment group in drug-diet format; vehicle (VEH), PLX5622 (PLX), ethanol diet (EtOH), control diet (CON); e.g., PLX-EtOH
  - Study: cohort id
  - Hippo: average FJB+ cell count per hippocampus section
  - Rhinal: average FJB+ cell count per rhinal cortex section

NOTES:
- All data files are in comma separated value (".csv") format.

## ***data/results*** Directory
The ***data/results*** directory contains summary statistics and Welch's t-tests conducted comparing the effects of drug (PLX5622 vs vehicle) on the following ethanol binge metrics: blood ethanol concentration (bec), dose of ethanol (dose), and behavioral intoxication (intoxication) using {rstatix}. It also has the results of two-way ANOVAs and pairwise comparisons conducted on the effects of drug (PLX5622 vs vehicle) and diet (ethanol vs control) on Iba1+ (microglia) cell counts and FJB+ (dying neurons) cell counts using {rstatix}, {emmeans}, and {afex}. Finally, the percentage difference between drug treatment within diet for Iba1+ cell counts is included. These files have the following self explanatory names:
- **bec_summary.csv**
- **bec_ttest.csv**
- **dose_summary.csv**
- **dose_ttest.csv**
- **FJB_counts_hippo_aov2_posthoc.csv**
- **FJB_counts_hippo_aov2.csv**
- **FJB_counts_rhinal_aov2_posthoc.csv**
- **FJB_counts_rhinal_aov2.csv**
- **FJB_summary.csv**
- **Iba1_counts_hippo_aov2.csv**
- **Iba1_counts_hippo_pwc.csv**
- **Iba1_counts_rhinal_aov2.csv**
- **Iba1_counts_rhinal_pwc.csv**
- **Iba1_counts.csv**
- **Iba1_percentdiff.csv**
- **intoxication_summary.csv**
- **intoxication_ttest.csv**

## References
Data analysis was conducted in RStudio v2023.12.1.402 (Posit team, 2024) with R v4.2.2 (R Core Team, 2022) using rstatix (Kassambara, 2022), afex (Singmann et al., 2023), and emmeans (Lenth, 2022) packages with visualization in Prism v10.0.3 (GraphPad).
- Kassambara A (2022). _rstatix: Pipe-Friendly Framework for Basic
  Statistical Tests_. R package version 0.7.1,
  <https://CRAN.R-project.org/package=rstatix>.
- Lenth R (2022). _emmeans: Estimated Marginal Means, aka Least-Squares
  Means_. R package version 1.8.3,
  <https://CRAN.R-project.org/package=emmeans>.
- Posit team (2024). RStudio: Integrated Development Environment for R.
  Posit Software, PBC, Boston, MA. URL http://www.posit.co/.
- R Core Team (2022). R: A language and environment for statistical
  computing. R Foundation for Statistical Computing, Vienna, Austria. URL
  https://www.R-project.org/.
- Singmann H, Bolker B, Westfall J, Aust F, Ben-Shachar M (2023). _afex:
  Analysis of Factorial Experiments_. R package version 1.3-0,
  <https://CRAN.R-project.org/package=afex>.
  
