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

## Dataset Description

- **Homepage:** https://github.com/Harvard-Ophthalmology-AI-Lab/FairSeg
- **Download:** https://drive.google.com/drive/u/1/folders/1tyhEhYHR88gFkVzLkJI4gE1BoOHoHdWZ
- **Paper:** https://openreview.net/pdf?id=qNrJJZAKI3
- **Leaderboard:** [Needs More Information]
- **Point of Contact:** [Needs More Information]

### Dataset Summary

The FairSeg dataset containing 10,000 patients includes 10,000 Scanning laser ophthalmoscopy (SLO) fundus images. The disc and cup masks, patient age, gender, race, ethnicity, language, and marital status information are also included in the data. Under the folder "ReadMe", the file "data_summary.csv" provides an overview of our data.

### Supported Tasks and Leaderboards

- Segmentation

### Languages

The text in the dataset is in English.

## Dataset Structure

### Data Instances

10,000 SLO images in npz format (664 * 798).

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
- use
```

In .npz files

```    
slo_fundus: Scanning laser ophthalmoscopy (SLO) fundus image
disc_cup_mask: disc and cup masks for the corresponding SLO fundus image
age: patient's age
gender: 0 - Female, 1 - Male
race: 0 - Asian, 1 - Black, 2 - White
ethnicity: 0 - Non-Hispanic, 1 - Hispanic, -1 - Unknown
language: 0 - English, 1 - Spanish, 2 - Others, -1 - Unknown
maritalstatus: 0 - Married or Partnered, 1 - Single, 2 - Divorced, 3 - Widowed, 4 - Legally Separated, -1 - Unknown
```

### Data Splits

It is divided into 8,000 training and 2,000 test samples. The file data_summary.csv details the division of data into training and testing sets. 

```
FairSeg
├── ReadMe
├──── data_description.txt
├──── data_summary.csv
├── Training
└── Test
```