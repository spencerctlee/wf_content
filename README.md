# Wildfire Public Health Guidance Content Analysis

## Overview

This repository contains the data-processing and analysis code for a quantitative content analysis of wildfire smoke public health guidance documents.

The analysis examines whether wildfire smoke guidance documents include specific information relevant to individual-level health-protective actions and evidence-informed decision-making. The coding framework was informed by principles from GRADE and the Evidence-to-Decision (EtD) framework.

The unit of analysis is the individual wildfire smoke guidance document. Documents are coded primarily using structured binary indicators representing the presence or absence of predefined content. Selected free-text fields capture additional details when applicable.

## Objectives

The analysis aims to describe the extent to which wildfire smoke public health guidance includes:

- individual-level health-protective actions;
- identification of target populations;
- explicit guidance goals;
- information about authorship and development processes;
- multilingual availability;
- potential benefits and burdens of recommended actions;
- quantitative estimates of benefits and burdens;
- statements about evidence quality; and
- scientific references supporting recommendations.

## Coding and Inter-Coder Reliability

Guidance documents were independently coded by two reviewers using a prespecified coding manual and structured codebook.

Inter-coder reliability is assessed using:

- observed percent agreement; and
- nominal Krippendorff's alpha for structured categorical variables.

Consistent with the prespecified coding protocol, the primary reliability analysis evaluates agreement across eligible binary coding decisions. Variable-level reliability statistics are also calculated as diagnostic analyses.

Free-text extraction fields are assessed separately. Because independently extracted text may differ lexically while conveying the same information, agreement is manually assessed based on substantive equivalence and summarized using percent substantive agreement.

## Repository Structure

```text
.
├── data/
│   └── 20260908/
│       ├── s_content_analysis.csv
│       ├── m_content_analysis.csv
│       └── text_agreement.csv
│
├── analysis/
│   └── wildfire_public_health_guidance_content_analysis.qmd
│
├── README.md
└── .gitignore
```

The exact directory structure may evolve as the analysis progresses.

## Key Files

- `s_content_analysis.csv` — independent coding completed by SL.
- `m_content_analysis.csv` — independent coding completed by MB.
- `text_agreement.csv` — comparison and manual assessment of free-text extraction fields.
- `wildfire_public_health_guidance_content_analysis.qmd` — reproducible data cleaning, inter-coder reliability analysis, and results generation.

## Analysis Workflow

The analysis script performs the following steps:

1. Imports independently coded datasets.
2. Standardizes binary coding values.
3. Removes free-text fields from the structured reliability analysis.
4. Aligns coding decisions by document identifier and coding variable.
5. Calculates overall percent agreement and Krippendorff's alpha.
6. Calculates variable-level agreement and Krippendorff's alpha.
7. Identifies variables for which alpha cannot be estimated because of insufficient variation.
8. Processes manually assessed free-text fields.
9. Calculates overall and field-specific substantive agreement for free-text extraction.
10. Generates reproducible summary tables.

## Software

Analyses are conducted in R using Quarto.

Key R packages include:

```r
dplyr
tidyr
stringr
readxl
janitor
irr
gt
```

## Reproducing the Analysis

From the project root, render the Quarto analysis file using RStudio or:

```bash
quarto render analysis/wildfire_public_health_guidance_content_analysis.qmd
```

File paths in the analysis are relative to the project root.

## Data Notes

The coding datasets contain research-generated abstractions from publicly available wildfire smoke guidance documents.

Binary fields are standardized as:

- `1` = content present;
- `0` = content absent; and
- `NA` = missing or non-substantive placeholder where applicable.

Free-text placeholders such as `N/A`, blank cells, and non-substantive `0` values are standardized as missing for the free-text agreement analysis.

## Coding Manual

Coding decisions are governed by the project coding manual:

**Wildfire Smoke Guidance Content Analysis: Coding Manual**

The manual defines each code, inclusion and exclusion criteria, and decision rules used during coding. Decision rules may be refined following coder training and reliability assessment.

## Status

This repository contains ongoing analysis materials. Coding, adjudication, and analytic outputs may be updated as the project progresses.

## Contributors

- Spencer Lee (SL)
- MB
- SH
