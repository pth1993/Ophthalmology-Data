# Dataset Card for OCTID

## Table of Contents
- [Dataset Card for OCTID](#dataset-card-for-octid)
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

- **Homepage:** NA
- **Repository:** https://borealisdata.ca/dataverse/OCTID
- **Paper:** https://www.sciencedirect.com/science/article/pii/S0045790618330842

### Dataset Summary

The Optical Coherence Tomography Image Database (OCTID) contains 573 instances of 2D slices of retinal OCT scans. The images are in various sizes, typically 879x586 or 700x500. Images are categorized according to disease type: Normal, Central Serous Retinopathy (CSR), Age-related Macular Degeneration (AMD), Macular Hole (MH), and Diabetic retinopathy (DR). The images cover multiple disease stages, but there's no label for the disease stage.

### Supported Tasks and Leaderboards

- Classification

### Languages

Not applicable

## Dataset Structure

### Data Instances

572 images in JPEG format in total.

### Data Fields

No metadata nor demographic info. Images are grouped in subfolders: `{split}/{disease}/{image_name}.jpeg`

### Data Splits

Train, validation, test in separate folders. 316 for training, 82 for validation, and 174 for testing.

|Disease|# train|# val|# test|# total|
|----|----|----|----|----|
|Normal|115|29|62|206|
|AMD|30|8|17|55|
|CSR|56|15|31|102|
|DR|59|15|33|107|
|MH|56|15|31|102|
|Total|316|82|174|572|

### Data Folder

```
OCTID
├── readme.txt
├── test
│   ├── ANormal
│   ├── ARMD
│   ├── CSR
│   ├── Diabetic_retinopathy
│   └── Macular_Hole
├── train
│   ├── ANormal
│   ├── ARMD
│   ├── CSR
│   ├── Diabetic_retinopathy
│   └── Macular_Hole
└── val
    ├── ANormal
    ├── ARMD
    ├── CSR
    ├── Diabetic_retinopathy
    └── Macular_Hole
```
