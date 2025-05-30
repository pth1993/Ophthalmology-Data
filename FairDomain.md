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

- **Homepage:** https://github.com/Harvard-Ophthalmology-AI-Lab/FairDomain
- **Download:** https://drive.google.com/drive/folders/1huH93JVeXMj9rK6p1OZRub868vv0UK0O?usp=drive_link
- **Paper:** https://arxiv.org/pdf/2407.08813

### Dataset Summary

FairDomain dataset includes data for both segmentation and classification tasks for studying fairness in domain shift. For the segmentation task, 10,000 samples from 10,000 patients are included. For the classification task, 10,000 samples from 10,000 patients are included. The samples from FairDomain dataset are derived from FairSeg and FairCLIP with an added imaging modality of en-face fundus image in addition to the imaging modality of scanning laser ophthalmoscopy (SLO) fundus image originally in the two datasets.

### Supported Tasks and Leaderboards

- Segmentation
- Classification
- Fairness
- Domain adaptation

### Languages

Not applicable.

## Dataset Structure

### Data Instances

- Classification: 10,000 SLO and 10,000 en-face images in npz format (224 * 224).
- Segmentation: 10,000 SLO and 10,000 en-face images in npz format (224 * 224).

### Data Fields

- Classification

  - In data_summary.csv

    ```
    - filename
    - age
    - gender
    - race
    - ethnicity
    - language
    - maritalstatus
    - md
    - glaucoma
    - use
    ```

  - In .npz files

    ```
    oct_fundus: En-face fundus image    
    slo_fundus: Scanning laser ophthalmoscopy (SLO) fundus image
    age: patient's age
    gender: 0 - Female, 1 - Male
    race: 0 - Asian, 1 - Black, 2 - White
    ethnicity: 0 - Non-Hispanic, 1 - Hispanic, -1 - Unknown
    language: 0 - English, 1 - Spanish, 2 - Others, -1 - Unknown
    maritalstatus: 0 - Married or Partnered, 1 - Single, 2 - Divorced, 3 - Widowed, 4 - Legally Separated, -1 - Unknown
    md: visual field mean deviation
    glaucoma: Non-Glaucoma (0) or Glaucoma (1)
    ```

- Segmentation

  - In data_summary.csv

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

  - In .npz files

    ```
    oct_fundus: En-face fundus image    
    slo_fundus: Scanning laser ophthalmoscopy (SLO) fundus image
    oct_disc_cup: disc and cup masks for the corresponding en-face fundus image
    slo_disc_cup: disc and cup masks for the corresponding SLO image
    age: patient's age
    gender: 0 - Female, 1 - Male
    race: 0 - Asian, 1 - Black, 2 - White
    ethnicity: 0 - Non-Hispanic, 1 - Hispanic, -1 - Unknown
    language: 0 - English, 1 - Spanish, 2 - Others, -1 - Unknown
    maritalstatus: 0 - Married or Partnered, 1 - Single, 2 - Divorced, 3 - Widowed, 4 - Legally Separated, -1 - Unknown
    ```



### Data Splits

It is divided into 8,000 training and 2,000 test samples (for each classification and segmentation tasks). The file data_summary.csv details the division of data into training and testing sets. 


### Data Folder
```
FairSeg
├── Classification
├──── ReadMe
├────── data_description.txt
├────── data_summary.csv
├──── Dataset
├── Segmentation
├──── ReadMe
├────── data_description.txt
├────── data_summary.csv
├──── Dataset
```