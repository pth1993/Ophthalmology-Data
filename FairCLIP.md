# Dataset Card for FairCLIP

## Table of Contents
- [Dataset Card for FairCLIP](#dataset-card-for-fairclip)
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

- **Homepage:** https://github.com/Harvard-Ophthalmology-AI-Lab/FairCLIP
- **Repository:** https://drive.google.com/drive/folders/1bkeifigwOAfnsLvup9mJOSNeA3WsvA2l
- **Paper:** https://openaccess.thecvf.com/content/CVPR2024/papers/Luo_FairCLIP_Harnessing_Fairness_in_Vision-Language_Learning_CVPR_2024_paper.pdf

### Dataset Summary

The FairCLIP dataset comprises 10,000 SLO images from 10,000 subjects. The file split_files.csv details the division of data into training, validation, and testing sets. The data folder contains 10,000 NPZ files named in the format "data_xxxxx.npz", where "xxxxx" (e.g., 06691) is a unique numeric ID. The file meta_all.csv provides metadata (such as race, gender, ethnicity, marital status, age, and preferred language) for each NPZ file. Moreover, the files original_notes.csv and gpt-4_summarized_notes.csv contain original notes and notes summarized by GPT-4, respectively.

### Supported Tasks and Leaderboards

- Classification
- Retrieval
- Fairness

### Languages

The text in the dataset is in English.

## Dataset Structure

### Data Instances

10,000 SLO images in npz format (664 * 512).

### Data Fields

In data_summary.csv

```
- filename
- age
- gender
- race
- ethnicity
- language
- maritalstatus
- note
- gpt4_summary
- glaucoma
- use
```

In .npz files

```
- slo_fundus: slo fundus image
- age: patient age
- gender: Female (0), Male (1)
- race: Asian (0), Black (1), White (2)
- ethnicity: non-Hispanic (0), Hispanic (1), Unknown (-1)
- language: English (0), Spanish (1), Other (2), Unknown (-1)
- maritalstatus: Marriage or Partnered (0), Single (1), Divorced (2), Widoled (3), Legally Separated (4), Unknown (-1)
- glaucoma: Non-Glaucoma (0) or Glaucoma (1)
```

### Data Splits

It is divided into 7,000 training, 1,000 validation, and 2,000 test samples. The file data_summary.csv details the division of data into training, validation, and testing sets. 

### Data Folder
```
FairCLIP
├── ReadMe
├──── data_description.txt
├──── data_summary.csv
├──── gpt-4_summarized_notes.csv
├── Training
├── Validation
└── Test
```