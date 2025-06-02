# Dataset Card for UK Biobank

## Table of Contents
- [Dataset Card for UK Biobank](#dataset-card-for-ukbiobank)
  - [Table of Contents](#table-of-contents)
  - [Dataset Description](#dataset-description)
    - [Dataset Summary](#dataset-summary)
    - [Supported Tasks and Leaderboards](#supported-tasks-and-leaderboards)
    - [Languages](#languages)
  - [Dataset Structure](#dataset-structure)
    - [Data Instances](#data-instances)
    - [Data Fields](#data-fields)
    - [Data Splits](#data-splits)
    - [Data Folder](#data-folder)

## Dataset Description

- **Homepage:** https://www.ukbiobank.ac.uk
- **Repository:** https://community.ukbiobank.ac.uk/hc/en-gb/community/posts/19996604847133-Changing-the-way-UK-Biobank-data-is-made-available-to-researchers-around-the-world
- **Paper:** https://research-information.bris.ac.uk/ws/portalfiles/portal/197741298/Full_text_PDF_final_published_version_.pdf

### Dataset Summary

UK Biobank dataset contains approximately 85,000 participants underwent Optical Coherence Tomography imaging of the retina (using the TOPCON 3D OCT 1000 Mk2) at the baseline assessment. The instrument takes a 3D scan and photograph of the retina and also provides a magnified photograph of the fundus. This dataset contains the fundus images of the retina of both the left (21015) and right (21016) eyes. Images are stored in PNG-format, approximately 2MB each. This dataset contains the 3D OCT images of both the left (21017) and right (21018) eyes. Images are stored in zip-format, approximately 27MB each.

### Supported Tasks and Leaderboards

- Classification
- TTE Prediction
- Fairness

### Languages

Not applicable.

## Dataset Structure

### Data Instances

144,542 CFP images (2048 * 1536) in PNG format and 140,659 3D OCT images (128 * 512 * 650) in zip format.

### Data Folder
```
UKBiobank
├── 21015
├── 21016
├── 21017
└── 21018
```