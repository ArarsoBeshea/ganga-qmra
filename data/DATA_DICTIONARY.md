# Data dictionary: `ganga_dataset.csv`

**What it is.** Fecal indicator counts in grab samples of surface water from four bathing sites at Varanasi, India: 4 sites × 11 monthly sampling occasions = 44 samples, collected between 17 June 2025 and 15 May 2026 (no sample was collected in March 2026). The file is identical to Table S1 of the article's Supplementary Information.

**Format.** Comma-separated values, UTF-8, one header row, 44 data rows, no missing values.

| Column | Type | Values / unit | Meaning |
|---|---|---|---|
| `date` | date (YYYY-MM-DD) | 2025-06-17 to 2026-05-15 | Sampling date (11 occasions) |
| `site_code` | text | A, B, C, D | Site code |
| `site` | text | U/S Assi Ghat, Assi Ghat, Dashashwamedh Ghat, Kardameshwar Pond | Site name |
| `season` | text | Monsoon (June–September, 16 samples); Post-monsoon (October–November, 8); Dry (December–May, 20) | Season of the sampling date |
| `total_coliform` | integer | MPN per 100 mL | Total coliforms (TC) |
| `fecal_coliform` | integer | MPN per 100 mL | Fecal coliforms (FC). CPCB limits: maximum permissible 2,500, desirable 500 MPN per 100 mL |
| `e_coli` | integer | MPN per 100 mL | *Escherichia coli* |
| `fecal_streptococci` | integer | MPN per 100 mL | Fecal streptococci (FS). CPCB limits: maximum permissible 500, desirable 100 MPN per 100 mL |
| `enterococci` | integer | MPN per 100 mL | Enterococci (the subset of FS that grew in BHI broth with and without 6.5 % NaCl) |

Derived quantities (PHRQ, FC/FS ratio, risk estimates) are not stored in this file; the notebook computes them.

## Sites

| Code | Site | Description |
|---|---|---|
| A | U/S Assi Ghat | Reference site upstream of Assi Ghat, above the confluence of the Assi River with the Ganga |
| B | Assi Ghat | Ghat used daily by thousands of bathers |
| C | Dashashwamedh Ghat | Ghat used daily by thousands of bathers |
| D | Kardameshwar Pond | Ritual pond at the head of the roughly 8 km urban stretch of the Assi River, away from the Ganga main channel |

## Sampling and laboratory method (summary; full description in Section 2 of the article)

* Grab samples were taken at waist level, 20–30 cm below the surface, in autoclaved 1000 mL capped bottles, transported on ice and held at 4 °C; culture began within 6 h of collection.
* Counts were obtained by the multiple-tube fermentation technique (Standard Methods) in the Environmental Engineering Laboratory, Department of Civil Engineering, IIT (BHU) Varanasi, and were read from MPN tables. All counts are most probable numbers (MPN) per 100 mL.

## Note on individual values

On 2026-04-15 at site D, the values for `total_coliform` (17,333), `fecal_coliform` (2,933), and `e_coli` (687) are not entries in the MPN table; unlike all other values in the file, these are the averages of 5 replicates.
