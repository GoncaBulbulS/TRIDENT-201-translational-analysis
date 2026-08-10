# TRIDENT-201 Translational Biomarker Analysis

End-to-end translational biomarker analysis of a **fictional Phase II oncology clinical trial** using Python.

## Project Overview

TRIDENT-201 is a synthetic clinical trial dataset designed to simulate a translational research workflow in oncology.

The project integrates clinical outcomes, circulating protein biomarkers, laboratory measurements, genomic alterations, adverse events, and RNA-expression data to explore how biomarker information can be connected with clinical outcomes and treatment response.

The analysis is organized as a series of reproducible Jupyter notebooks that progress from data quality control and exploratory biomarker analysis toward clinical outcome modeling.

## Current Analysis

### Baseline Protein Biomarker Analysis

The current analysis evaluates baseline relationships among:

* IL-6
* CRP
* TNF-α
* IFN-γ
* VEGF
* PD-L1
* circulating tumor DNA (ctDNA)

The workflow includes:

* clinical and biomarker quality control
* data cleaning and harmonization
* exploratory data analysis
* biomarker distributions and log transformation
* Pearson and Spearman correlation analysis
* pairwise sample-size assessment
* confidence intervals for correlation coefficients
* multiple-testing correction using Benjamini–Hochberg False Discovery Rate (FDR)
* biological interpretation of exploratory biomarker findings

## Key Findings

The strongest baseline biomarker relationship was observed between **IL-6 and CRP**:

**Spearman r = 0.780, 95% CI: 0.722–0.828, FDR-adjusted p < 0.001**

This strong positive association is consistent with the known relationship between **IL-6 signaling and hepatic CRP production**.

Weak negative associations between TNF-α and both IL-6 and CRP reached nominal statistical significance but did not remain significant after FDR correction.

No clear baseline association was detected between IFN-γ and PD-L1 in this dataset despite the biological rationale connecting IFN-γ signaling with PD-L1 expression and adaptive immune resistance.

These analyses are exploratory and require independent validation before confirmatory biological or clinical conclusions can be drawn.

## Repository Structure

```text
TRIDENT-201-translational-analysis/
├── data/
│   └── raw/                 # Synthetic source datasets
├── notebooks/
│   └── 03_baseline_biomarker_analysis.ipynb
├── figures/                 # Portfolio-ready analysis figures
├── results/                 # Reproducible statistical outputs
├── requirements.txt
└── README.md
```

## Next Steps

The next stage of the project will evaluate relationships between baseline biomarkers and clinical outcomes, including:

* objective response
* progression-free survival (PFS)
* overall survival (OS)
* prognostic versus predictive biomarker effects
* Kaplan–Meier survival analysis
* Cox proportional hazards models
* multivariable biomarker modeling

## Disclaimer

TRIDENT-201 is a **fictional/synthetic clinical trial created for educational and portfolio purposes**. It does not contain real patient data and should not be interpreted as evidence from an actual clinical study.

