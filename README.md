# Ganga bathing-water fecal indicators, PHRQ and illness risk: data and code

Data and code for the article **"Linking fecal indicator limits to gastrointestinal illness risk for ritual bathing in the Ganga at Varanasi, India"** by Ararso Beshea Tekile and Prabhat Kumar Singh (Department of Civil Engineering, Indian Institute of Technology (BHU), Varanasi).

<!-- Replace ArarsoBeshea/ganga-qmra and XXXXXXX once the repository and the Zenodo record exist. -->
[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/ArarsoBeshea/ganga-qmra/blob/main/notebooks/Ganga_QMRA_reproducible_analysis.ipynb)
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.XXXXXXX.svg)](https://doi.org/10.5281/zenodo.XXXXXXX)

## What is here

```
.
├── README.md
├── LICENSE                      CC BY 4.0
├── CITATION.cff                 how to cite
├── requirements.txt             Python packages
├── data/
│   ├── ganga_dataset.csv        44 samples x 5 fecal indicators (= Table S1 of the article)
│   └── DATA_DICTIONARY.md       columns, units, sites, methods
└── notebooks/
    └── Ganga_QMRA_reproducible_analysis.ipynb   the analysis, step by step, with its results
```

* **Data:** 44 water samples (4 sites x 11 monthly occasions, 17 June 2025 to 15 May 2026), each with total coliforms, fecal coliforms, *E. coli*, fecal streptococci and enterococci (MPN per 100 mL).
* **Code:** one self-contained Python notebook. It recomputes the statistics, the Public Health Risk Quotient (PHRQ), the quantitative microbial risk model, the sensitivity analyses, and the figures and tables of the article. The dataset is embedded in the notebook, so nothing has to be uploaded; `data/ganga_dataset.csv` is the same dataset as a file, and the notebook confirms that the two are identical.

## Run it

**Google Colab (nothing to install).** Open the notebook with the badge above (or *File > Upload notebook* in Colab) and choose *Runtime > Run all*. It takes about 2 to 5 minutes.

**On your own computer.**

```bash
pip install -r requirements.txt
jupyter nbconvert --to notebook --execute notebooks/Ganga_QMRA_reproducible_analysis.ipynb --output-dir executed
```

Tables (CSV) and figures (PNG) are written to an `outputs/` folder next to the notebook and zipped as `ganga_outputs.zip`. The notebook as stored here already contains the results of one complete run, so you can read it without running anything.

## What the notebook reproduces

| Step | Content | Article section |
|---|---|---|
| 1-4 | Data, indicator concentrations, relationships between indicators, FC/FS ratio, PHRQ and tiers | 2.1-2.5, 3.1-3.5 |
| 5-8 | Risk model (inputs, dose-response, ingestion), distribution fits, calibration of the scaling factor kappa, per-event illness at the sites | 2.6-2.7, 3.6-3.7 |
| 9-11 | PHRQ-to-risk map, sensitivity analysis, dose-response alternatives (subset) | 3.8-3.9 |
| 12 | Statistics quoted in the text: Spearman correlations, indicator ratios, PHRQ by site and season, exceedance with Wilson intervals, monthly compliance, mixed models and rank tests, annual illness probability | 2.3, 3.1-3.4, 3.7 |
| 13-14 | Workflow diagram; scoreboard and export | n/a |

## Built-in check

The scoreboard at the end of the notebook compares 24 headline quantities (for example the calibrated scaling factors, per-event illness probabilities, mixed-model p-values and annual risk) with the values reported in the article and prints a tick or a warning for each. In the tested environment all 24 agree within the stated tolerances (3 to 5 % for simulation-based quantities, which carry Monte Carlo error; the precision printed in the article for the statistics).

## What the notebook does not reproduce

* **Fig. 1** (study-area map) and **Fig. S1** (laboratory flowchart): see the article and its Supplementary Information.
* **Eight of the twelve dose-response alternatives of Table 2.** The primary set and four alternatives are reproduced (Step 11). The *Campylobacter* pair with its own illness model, the approximate beta-Poisson form, the disaggregated and aggregation-adjusted norovirus models, and the three adenovirus variants and the combined set need model code that is not part of this notebook.
* **Digit-for-digit agreement.** The calibration of kappa uses 1,000,000 Monte Carlo draws here (400,000 in the article) to reduce simulation noise. Results agree with the article within simulation error, not to the last digit. All random seeds are fixed (`SEED = 20261026`).

## Software

Python 3.12 or later with numpy, scipy, pandas, matplotlib, mpmath and statsmodels (`requirements.txt`). Tested with Python 3.12.3, numpy 2.5.4, scipy 1.18.1, pandas 3.0.6, matplotlib 3.11.2, mpmath 1.3.0 and statsmodels 0.15.0; a full run took about one minute.

## License

Data, code and documentation are released under the Creative Commons Attribution 4.0 International license (CC BY 4.0; see `LICENSE`). Please cite the article and this record.

## How to cite

* Article: Tekile, A.B., Singh, P.K. (2026). Linking fecal indicator limits to gastrointestinal illness risk for ritual bathing in the Ganga at Varanasi, India. *[journal, volume, DOI: add when published]*.
* Data and code: Tekile, A.B., Singh, P.K. (2026). Data and code for "Linking fecal indicator limits to gastrointestinal illness risk for ritual bathing in the Ganga at Varanasi, India" (version 1.0.0) [Data set and software]. Zenodo. https://doi.org/10.5281/zenodo.XXXXXXX

## Notes

Generative-AI assistance in writing and checking the analysis code is declared in the article; the authors are responsible for the code and the results. The corresponding author is Prabhat Kumar Singh (see the article for contact details).
