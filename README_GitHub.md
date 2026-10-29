# Chinese Cultural Names in English: Reproducibility Data and R Code

Reproducibility materials for the manuscript:

> **Long-Term Textual Visibility of Chinese Cultural Names in English: Naming Pathways, Historical Spellings, and Knowledge Traceability for Cultural Sustainability**

**Authors:** Shanshan Liu, Jinkai Zhang, and Gina S. Rhee (corresponding author)

This repository contains the curated data, coding records, audit files, R scripts, final analytical dataset, model outputs, and figures used to study the long-term textual visibility of Chinese cultural names in English from 1800 to 2022.

The project links corpus-based lexical history with cultural sustainability by asking whether cultural concepts remain identifiable and traceable when English names, spellings, and naming conventions change over time.

## Repository structure

```text
.
├── README.md
├── GITHUB_METADATA.md
├── REPRODUCIBILITY_NOTES.md
├── DATA_DICTIONARY.md
├── CITATION.cff
├── CHECKSUMS_SHA256.txt
├── FILE_INVENTORY.csv
├── data/
│   ├── 00_source_curation/
│   ├── 01_coding/
│   ├── 02_semantic_rebuild/
│   ├── 03_historical_spelling/
│   └── 04_final_analysis/
├── scripts/
│   ├── process/
│   └── final/
├── outputs/
│   └── final/
├── figures/
│   └── main/
├── manuscript/
└── archive/
    ├── intermediate_scripts/
    ├── coding_process/
    ├── output_snapshots/
    └── not_used_for_submission/
```

## What the main folders contain

### `data/00_source_curation/`
The cleaned candidate lexicon and curation records used to build the reproducible core sample.

### `data/01_coding/`
Independent coding files, frozen semantic coding instructions, Round 2 coding, and final semantic adjudication.

### `data/02_semantic_rebuild/`
Files documenting the reconstruction of the final semantic-clean annual dataset after `keep`, `truncate`, and `exclude` decisions were frozen.

### `data/03_historical_spelling/`
Historical-spelling candidates, variant mappings, annual variant series, download logs, and audited spelling-sensitivity results.

### `data/04_final_analysis/`
The final annual analysis data and the pathway/date audit files used in the submission analysis.

### `scripts/process/`
Scripts that document the main workflow stages:
1. independent coding agreement;
2. generation of blind Round 2 semantic coding files;
3. reconstruction of the final semantic-clean annual data.

### `scripts/final/`
The final analysis scripts. For reproducibility from the repository root, use:

```r
source("scripts/final/10_FINAL_SUBMISSION_ANALYSIS_GITHUB.R")
```

The script searches the repository recursively for the required frozen data and writes a fresh `FINAL_SUBMISSION_OUTPUTS/` directory.

### `outputs/final/`
Final tables, diagnostics, model summaries, bootstrap results, session information, and the version manifest corresponding to the manuscript results.

### `figures/main/`
The three main figures used in the manuscript.

### `archive/`
Earlier scripts, intermediate diagnostics, output snapshots, and files that document how the workflow evolved. These files are retained for provenance and should **not** be mixed with the final analysis.

## Recommended reproduction workflow

1. Clone or download the repository.
2. Open R in the repository root.
3. Use R 4.5.1 or a recent compatible R version.
4. Run:

```r
source("scripts/final/10_FINAL_SUBMISSION_ANALYSIS_GITHUB.R")
```

5. Compare the regenerated `FINAL_SUBMISSION_OUTPUTS/` directory with `outputs/final/`.

The final script installs missing CRAN packages when `INSTALL_MISSING <- TRUE`.

## R packages used by the final analysis

`readr`, `dplyr`, `tidyr`, `stringr`, `purrr`, `forcats`, `ggplot2`, `slider`, `broom`, `sandwich`, `lmtest`, `mgcv`, `scales`, `ggrepel`, `tibble`, and `openxlsx`.

See `outputs/final/sessionInfo_FINAL_SUBMISSION.txt` for the recorded analysis environment.

## Analytical sample

The workflow began with **381** candidate records identified from public lexical resources. After curation, **187** reproducible core candidates remained. Following Ngram availability checks, semantic adjudication, and chronological screening, the final annual dataset retained **154** terms:

- 28 source-form borrowings;
- 122 pure calques;
- 4 mixed/partial-calque forms.

The mixed forms are retained for descriptive and case-based analyses but are excluded from the binary source-form vs. pure-calque inferential models.

## Coding and adjudication

The repository keeps the reliability and adjudication stages separate.

- Initial pathway coding agreement: raw agreement 98.9%, Cohen's κ = 0.972 under the initial coding rules.
- Cultural-domain agreement: raw agreement 93.0%, κ = 0.918.
- Second-round semantic coding of 75 high-risk terms: raw agreement 78.7%, κ = 0.610.
- Final semantic decisions were frozen only after the reliability calculation.

The final pathway scheme was subsequently clarified through entry-level etymological adjudication. The initial κ should therefore be interpreted as agreement under the initial coding rules rather than as direct validation of the revised three-way pathway classification.

## Chronological evidence

The final analysis distinguishes:

- **object-formation guardrails**;
- **verified target-sense example years**;
- **official naming/standardization years**;
- **adopted conservative analysis starts**.

These are stored separately in `data/04_final_analysis/DATE_EVIDENCE_MATRIX.csv`.

The sustained-onset outcome is the earliest sustained textual appearance **within the adopted observation range**. It is not treated as an unconditional first English attestation.

## Historical spelling

Historical spelling variants enter the sensitivity analysis only when a historical context supports the intended cultural sense.

The verified spelling analysis is deliberately conservative. Candidate variants with unresolved homography or referential ambiguity are excluded until target-sense evidence is available.

Frequencies from different spellings are not summed. The spelling-family analysis uses yearly presence/absence to avoid combining incomparable n-gram series.

## Data provenance

The project uses public lexical/etymological resources and Google Books Ngram-derived annual series.

This repository provides the study's **curated and derived research files**. It does not redistribute the underlying Google Books corpus. Historical and lexical sources remain subject to their original providers' terms and are cited in the manuscript and audit files.

## Key authoritative files

For the final reported analysis, begin with:

- `data/01_coding/Semantic_75_FINAL.csv`
- `data/02_semantic_rebuild/Semantic_Clean_Annual_Data_FINAL.csv`
- `data/03_historical_spelling/historical_spelling_annual_variants.csv`
- `data/03_historical_spelling/historical_spelling_variant_map_predefined.csv`
- `data/04_final_analysis/FINAL_SUBMISSION_ANNUAL_DATA.csv`
- `data/04_final_analysis/PATHWAY_CODEBOOK_FINAL.csv`
- `data/04_final_analysis/PATHWAY_FINAL_AUDIT.csv`
- `data/04_final_analysis/DATE_EVIDENCE_MATRIX.csv`
- `scripts/final/10_FINAL_SUBMISSION_ANALYSIS_GITHUB.R`

## Versioning

`outputs/final/VERSION_MANIFEST.csv` records the principal files used by the final submission analysis.

`CHECKSUMS_SHA256.txt` provides repository-level file checksums for integrity checking.

Files under `archive/` document earlier analytical stages and are not authoritative for the reported results.

## Manuscript reference copy

`manuscript/Sustainability_English_Manuscript_SUBMISSION_FINAL.docx` is included only as a reference copy that maps the archived outputs to the manuscript version used when this repository package was prepared.

## Citation

Until a journal citation or DOI is available, please cite the manuscript title and this repository. A machine-readable citation template is provided in `CITATION.cff`.

## Contact

**Corresponding author:** Gina S. Rhee  
The Catholic College, The Catholic University of Korea  
Email: ddobyurhee@catholic.ac.kr

For questions about the analysis code and reproducibility workflow, the authors may also be contacted through the associated manuscript.
