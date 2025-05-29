# Dataset Card for FairCLIP

## Table of Contents
- [Dataset Description](#dataset-description)
  - [Dataset Summary](#dataset-summary)
  - [Supported Tasks](#supported-tasks-and-leaderboards)
  - [Languages](#languages)
- [Dataset Structure](#dataset-structure)
  - [Data Instances](#data-instances)
  - [Data Fields](#data-instances)
  - [Data Splits](#data-instances)
- [Dataset Creation](#dataset-creation)
  - [Curation Rationale](#curation-rationale)
  - [Source Data](#source-data)
  - [Annotations](#annotations)
  - [Personal and Sensitive Information](#personal-and-sensitive-information)
- [Considerations for Using the Data](#considerations-for-using-the-data)
  - [Social Impact of Dataset](#social-impact-of-dataset)
  - [Discussion of Biases](#discussion-of-biases)
  - [Other Known Limitations](#other-known-limitations)
- [Additional Information](#additional-information)
  - [Dataset Curators](#dataset-curators)
  - [Licensing Information](#licensing-information)
  - [Citation Information](#citation-information)

## Dataset Description

- **Homepage:** https://github.com/Harvard-Ophthalmology-AI-Lab/FairCLIP
- **Repository:** https://drive.google.com/drive/folders/1bkeifigwOAfnsLvup9mJOSNeA3WsvA2l
- **Paper:** https://openaccess.thecvf.com/content/CVPR2024/papers/Luo_FairCLIP_Harnessing_Fairness_in_Vision-Language_Learning_CVPR_2024_paper.pdf
- **Leaderboard:** [Needs More Information]
- **Point of Contact:** [Needs More Information]

### Dataset Summary

The FairCLIP dataset comprises 10,000 SLO images from 10,000 subjects. The file split_files.csv details the division of data into training, validation, and testing sets. The data folder contains 10,000 NPZ files named in the format "data_xxxxx.npz", where "xxxxx" (e.g., 06691) is a unique numeric ID. The file meta_all.csv provides metadata (such as race, gender, ethnicity, marital status, age, and preferred language) for each NPZ file. Moreover, the files original_notes.csv and gpt-4_summarized_notes.csv contain original notes and notes summarized by GPT-4, respectively.

### Supported Tasks and Leaderboards

[Needs More Information]

### Languages

The text in the dataset is in English.

## Dataset Structure

### Data Instances

10,000 SLO images in npz format (664 * 512).

### Data Fields

In data_summary.csv

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

In .npz files

- slo_fundus
- maritalstatus
- ethnicity
- language
- gender
- race
- age
- glaucoma

### Data Splits

It is divided into 7,000 training, 1,000 validation, and 2,000 test samples. The file split_files.csv details the division of data into training, validation, and testing sets. 

Harvard-FairVLMed
├── data_summary.csv
├── gpt-4_summarized_notes.csv
├── Training
├── Validation
└── Test

## Dataset Creation

### Curation Rationale

[Needs More Information]

### Source Data

#### Initial Data Collection and Normalization

[Needs More Information]

#### Who are the source language producers?

[Needs More Information]

### Annotations

#### Annotation process

[Needs More Information]

#### Who are the annotators?

[Needs More Information]

### Personal and Sensitive Information

[Needs More Information]

## Considerations for Using the Data

### Social Impact of Dataset

[Needs More Information]

### Discussion of Biases

[Needs More Information]

### Other Known Limitations

[Needs More Information]

## Additional Information

### Dataset Curators

[Needs More Information]

### Licensing Information

[Needs More Information]

### Citation Information

[Needs More Information]