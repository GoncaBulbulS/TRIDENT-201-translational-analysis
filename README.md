# TRIDENT-201 Translational Biomarker Analysis

End-to-end translational biomarker and clinical-outcome analysis of a **fictional Phase II oncology clinical trial** using Python.

## Project Overview

TRIDENT-201 is a synthetic oncology clinical trial designed to demonstrate a reproducible translational research workflow connecting baseline biomarkers with clinical outcomes, treatment response, and time-to-event endpoints.

The project integrates clinical outcomes, circulating protein biomarkers, laboratory measurements, genomic alterations, adverse events, and RNA-expression data. Analyses progress from data quality control and exploratory biomarker characterization to response modeling, predictive-biomarker assessment, survival analysis, and multivariable clinical modeling.

The workflow emphasizes a translational research framework:

**Scientific question → data QC → statistical analysis → model diagnostics → biological interpretation → clinical context**

## Biomarkers Evaluated

* IL-6
* CRP
* TNF-α
* IFN-γ
* VEGF
* PD-L1 tumor proportion score (TPS)
* Circulating tumor DNA (ctDNA) fraction

## Analysis Workflow

The completed workflow includes:

* Clinical and biomarker quality control
* Data cleaning, harmonization, and reproducible merging
* Biomarker distribution assessment
* Prespecified transformations and standardization
* Pearson and Spearman correlation analysis
* Confidence intervals and sensitivity analyses
* Objective response analysis
* Overall treatment-effect estimation
* Logistic regression with biomarker-by-treatment interactions
* Prognostic versus predictive biomarker interpretation
* Benjamini–Hochberg false-discovery-rate correction
* Kaplan–Meier estimation for PFS and OS
* Log-rank survival comparisons
* Cox proportional-hazards regression
* Proportional-hazards diagnostics
* Restricted mean survival time (RMST) analysis
* Multivariable adjustment for baseline clinical covariates
* Sensitivity analyses for potential non-proportional hazards
* Reproducible statistical tables and portfolio-quality figures
* Biological, statistical, and pharmaceutical interpretation

## Key Findings

### Baseline biomarker relationships

The strongest baseline biomarker relationship was observed between IL-6 and CRP:

**Spearman r = 0.780; 95% CI: 0.722–0.828; FDR-adjusted p < 0.001**

This positive association is consistent with the biological relationship between IL-6 signaling and hepatic CRP production.

Weak negative associations between TNF-α and both IL-6 and CRP reached nominal significance but did not remain significant after FDR correction.

### Baseline biomarkers and objective response

Univariate responder-versus-non-responder analyses did not identify a baseline biomarker significantly associated with objective response after FDR correction.

These analyses evaluated overall outcome associations and did not establish treatment-specific predictive value.

### Overall treatment effect on objective response

Objective response rates were:

* **SOC:** 24/122 responders (19.7%)
* **TRIDENT + SOC:** 43/124 responders (34.7%)
* **Absolute ORR difference:** 15.0 percentage points
* **Bootstrap 95% CI:** 4.3–25.6 percentage points
* **Chi-square p-value:** 0.0124

TRIDENT + SOC demonstrated a higher objective response rate in the overall analysis population. This overall treatment effect does not by itself establish predictive biomarker value.

### Treatment-specific biomarker interactions

Seven baseline biomarkers were evaluated using logistic regression models containing treatment, standardized biomarker, and biomarker-by-treatment interaction terms.

No biomarker demonstrated statistically supported treatment-specific predictive value after FDR correction.

ctDNA produced the strongest hypothesis-generating interaction signal:

* **SOC biomarker OR per SD:** 0.782
* **TRIDENT + SOC biomarker OR per SD:** 1.316
* **Interaction OR:** 1.682
* **95% CI:** 0.931–3.036
* **Raw p-value:** 0.085
* **FDR-adjusted p-value:** 0.566

A sensitivity analysis excluding one extreme but biologically possible ctDNA value produced a similar interaction estimate:

**Interaction OR = 1.627; 95% CI: 0.907–2.921; raw p = 0.103**

The direction and approximate magnitude of the ctDNA result were reasonably robust to this exclusion, but the evidence remained insufficient to establish predictive value.

### Progression-free survival

Kaplan–Meier analysis showed longer progression-free survival for TRIDENT + SOC:

* **SOC median PFS:** 251 days
* **TRIDENT + SOC median PFS:** 323 days
* **Log-rank p-value:** approximately 8 × 10⁻⁶

A treatment-only Cox proportional-hazards model estimated:

**HR = 0.515; 95% CI: 0.382–0.693**

Under the proportional-hazards model, this corresponds to an approximately 49% lower estimated instantaneous hazard of progression or death for TRIDENT + SOC relative to SOC.

Because proportional-hazards diagnostics showed borderline evidence that the treatment effect might not remain perfectly constant over time, the hazard ratio was interpreted together with Kaplan–Meier curves and an RMST analysis rather than as a complete description of treatment benefit.

### Restricted mean progression-free survival

At a prespecified 365-day restriction time:

* **SOC RMST:** 235.3 days
* **TRIDENT + SOC RMST:** 296.8 days
* **RMST difference:** +61.4 days
* **Bootstrap 95% CI:** 36.0–85.8 days

Thus, over the first year of follow-up, the TRIDENT + SOC group accumulated approximately 61 additional progression-free days on average in this synthetic dataset.

RMST provides an absolute time-based treatment-effect measure and does not require the proportional-hazards assumption.

### Overall survival

The same magnitude of treatment separation was not observed for overall survival:

* **SOC median OS:** 553 days
* **TRIDENT + SOC median OS:** 567 days
* **Log-rank p-value:** 0.439
* **Cox HR:** 0.869
* **95% CI:** 0.609–1.240
* **Cox p-value:** 0.438

These data do not provide statistical evidence of an OS difference between treatment groups.

The absence of a statistically significant OS difference should not be interpreted as evidence that the treatments are equivalent.

### Multivariable PFS analysis

A multivariable Cox model evaluated whether the PFS treatment association remained after adjustment for baseline clinical characteristics, including:

* Age
* Sex
* Disease stage
* ECOG performance status
* Smoking status
* Histology

The adjusted treatment effect remained substantial:

**Adjusted HR = 0.451; 95% CI: 0.329–0.617**

Model diagnostics identified possible time-dependent behavior for selected baseline covariates, particularly age and disease stage. Sensitivity analyses using stratification, flexible age modeling, and exploratory time-varying effects were therefore used to assess robustness rather than relying on a single Cox specification.

Across these analyses, the estimated treatment association remained directionally consistent.

## Integrated Interpretation

Across multiple clinical endpoints, TRIDENT + SOC demonstrated evidence of improved clinical activity in this synthetic dataset.

The treatment arm showed:

* Higher objective response rate
* Longer progression-free survival
* A substantial reduction in estimated progression/death hazard
* Approximately two additional months of progression-free time during the first year based on RMST

However, an overall-survival benefit was not demonstrated.

None of the seven evaluated baseline biomarkers showed statistically supported treatment-specific predictive value after correction for multiple testing. The ctDNA interaction remained hypothesis-generating and would require independent validation before any claim of predictive utility.

Together, these analyses illustrate the distinction between:

**overall treatment efficacy**,
**prognostic biomarker associations**, and
**predictive biomarkers that identify differential treatment benefit**.

## Repository Structure

```text
TRIDENT-201-translational-analysis/
├── data/
│   └── raw/                       # Synthetic source datasets
├── notebooks/
│   ├── 03_baseline_biomarker_analysis.ipynb
│   ├── 04_biomarkers_and_clinical_outcomes.ipynb
│   ├── 05_treatment_specific_biomarker_analysis.ipynb
│   ├── 06_survival_analysis.ipynb
│   └── 07_multivariable_survival_analysis.ipynb
├── results/
│   ├── figures/                   # Portfolio-quality figures
│   └── tables/                    # Reproducible statistical outputs
├── requirements.txt
└── README.md
```

## Notebook Guide

**03 — Baseline Biomarker Analysis**
Exploratory biomarker characterization, distributions, transformations, correlation analysis, confidence intervals, sensitivity analyses, and multiple-testing correction.

**04 — Biomarkers and Clinical Outcomes**
Baseline biomarker associations with objective response, treatment-level response analysis, effect-size estimation, and logistic regression.

**05 — Treatment-Specific Biomarker Analysis**
Biomarker-by-treatment interaction modeling, prognostic versus predictive interpretation, FDR correction, predicted probabilities, and ctDNA sensitivity analysis.

**06 — Survival Analysis**
PFS and OS data QC, Kaplan–Meier estimation, log-rank testing, treatment-only Cox regression, proportional-hazards assessment, and restricted mean survival time.

**07 — Multivariable Survival Analysis**
Baseline-adjusted Cox modeling, covariate interpretation, proportional-hazards diagnostics, stratified modeling, flexible age modeling, and sensitivity analyses for potential time-varying effects.

## Tools and Methods

**Python:** pandas, NumPy, SciPy, statsmodels, scikit-learn, matplotlib, seaborn, lifelines

**Statistical methods:** correlation analysis, bootstrap confidence intervals, Mann–Whitney U testing, chi-square testing, logistic regression, interaction modeling, Benjamini–Hochberg FDR correction, Kaplan–Meier estimation, log-rank testing, Cox proportional-hazards regression, Schoenfeld-residual diagnostics, and restricted mean survival time.

## Main Conclusion

TRIDENT-201 demonstrates an end-to-end translational biomarker workflow spanning data QC, exploratory biomarker analysis, clinical-response modeling, predictive-biomarker assessment, and survival analysis.

Within this synthetic study, TRIDENT + SOC showed improved objective response and progression-free survival relative to SOC, while an overall-survival benefit was not demonstrated. Baseline biomarker analyses did not identify a statistically supported predictive biomarker after multiple-testing correction.

The project emphasizes reproducible analysis, model diagnostics, effect-size interpretation, uncertainty, and cautious translation of statistical findings into biologically and clinically meaningful conclusions.

## Disclaimer

TRIDENT-201 is a **fictional/synthetic clinical trial created for educational and portfolio purposes**. It contains no real patient data and should not be interpreted as evidence from an actual clinical study or used to guide clinical decision-making.
