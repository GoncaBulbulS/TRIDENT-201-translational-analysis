# TRIDENT-201 Translational Biomarker Analysis

End-to-end translational biomarker analysis of a **fictional Phase II oncology clinical trial** using Python.

## Project Overview

TRIDENT-201 is a synthetic oncology clinical trial designed to demonstrate a reproducible translational research workflow connecting baseline biomarkers with clinical outcomes and treatment response.

The project integrates clinical outcomes, circulating protein biomarkers, laboratory measurements, genomic alterations, adverse events, and RNA-expression data. Analyses progress from data quality control and exploratory biomarker characterization to response modeling, treatment-effect evaluation, and formal predictive-biomarker assessment.

## Biomarkers Evaluated

- IL-6
- CRP
- TNF-α
- IFN-γ
- VEGF
- PD-L1 tumor proportion score (TPS)
- Circulating tumor DNA (ctDNA) fraction

## Analysis Workflow

The completed workflow includes:

- Clinical and biomarker quality control
- Data cleaning, harmonization, and reproducible merging
- Biomarker distribution assessment
- Prespecified transformations and standardization
- Pearson and Spearman correlation analysis
- Confidence intervals and sensitivity analyses
- Objective response analysis
- Overall treatment-effect estimation
- Logistic regression with biomarker-by-treatment interactions
- Prognostic versus predictive biomarker interpretation
- Benjamini–Hochberg false-discovery-rate correction
- Portfolio-quality statistical tables and figures
- Biological and pharmaceutical interpretation

## Key Findings

### Baseline biomarker relationships

The strongest baseline biomarker relationship was observed between IL-6 and CRP:

**Spearman r = 0.780; 95% CI: 0.722–0.828; FDR-adjusted p < 0.001**

This positive association is consistent with the biological relationship between IL-6 signaling and hepatic CRP production.

Weak negative associations between TNF-α and both IL-6 and CRP reached nominal significance but did not remain significant after FDR correction.

### Baseline biomarkers and objective response

Univariate responder-versus-non-responder analyses did not identify a baseline biomarker significantly associated with objective response after FDR correction.

These analyses evaluated overall outcome associations and did not establish treatment-specific predictive value.

### Overall treatment effect

Objective response rates were:

- **SOC:** 24/122 responders (19.7%)
- **TRIDENT + SOC:** 43/124 responders (34.7%)
- **Absolute ORR difference:** 15.0 percentage points
- **Bootstrap 95% CI:** 4.3–25.6 percentage points
- **Chi-square p-value:** 0.0124

TRIDENT + SOC demonstrated a higher objective response rate in the overall analysis population. This overall treatment effect does not by itself establish predictive biomarker value.

### Treatment-specific biomarker interactions

Seven baseline biomarkers were evaluated using logistic regression models containing treatment, standardized biomarker, and biomarker-by-treatment interaction terms.

No biomarker demonstrated statistically supported treatment-specific predictive value after FDR correction.

ctDNA produced the strongest hypothesis-generating interaction signal:

- **SOC biomarker OR per SD:** 0.782
- **TRIDENT + SOC biomarker OR per SD:** 1.316
- **Interaction OR:** 1.682
- **95% CI:** 0.931–3.036
- **Raw p-value:** 0.085
- **FDR-adjusted p-value:** 0.566

A sensitivity analysis excluding one extreme but biologically possible ctDNA value produced a similar interaction estimate:

**Interaction OR = 1.627; 95% CI: 0.907–2.921; raw p = 0.103**

The direction and approximate magnitude of the ctDNA result were reasonably robust to this exclusion, but the evidence remained insufficient to establish predictive value.

## Main Conclusion

TRIDENT + SOC improved objective response in the overall study population, but none of the seven evaluated baseline biomarkers reliably identified patients with greater relative treatment benefit.

The ctDNA result may warrant further hypothesis-driven evaluation in a larger independent dataset. These exploratory findings should not be used for treatment selection.

## Repository Structure

```text
TRIDENT-201-translational-analysis/
├── data/
│   └── raw/                       # Synthetic source datasets
├── notebooks/
│   ├── 03_baseline_biomarker_analysis.ipynb
│   ├── 04_biomarkers_and_clinical_outcomes.ipynb
│   └── 05_treatment_specific_biomarker_analysis.ipynb
├── results/
│   ├── figures/                   # Portfolio-quality figures
│   └── tables/                    # Reproducible statistical outputs
├── requirements.txt
└── README.md
