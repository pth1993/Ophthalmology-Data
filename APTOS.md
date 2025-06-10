# Dataset Card for APTOS2019

## Table of Contents
- [Dataset Card for APTOS2019](#dataset-card-for-aptos2019)
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

- **Homepage:** https://www.kaggle.com/competitions/aptos2019-blindness-detection/data
- **Repository:** https://www.kaggle.com/competitions/aptos2019-blindness-detection/data
- **Paper:** NA

### Dataset Summary

The data consists of 3662 colored fundus images (training set of the competition) preprocessed with AutoMorph (https://github.com/rmaphoh/AutoMorph). The images are cropped to FOV and resized to 256x256. The images were gathered from multiple clinics using a variety of cameras over an extended period of time to introduce more variation. A clinician has rated each image for the severity of diabetic retinopathy on a scale of 0 to 4.

### Supported Tasks and Leaderboards

- Classification

### Languages

Not applicable

## Dataset Structure

### Data Instances

3662 colored fundus images in PNG format with shape 256x256

### Data Fields

Each image is labeled with 0-4 DR grade:
```
0 - No DR
1 - Mild
2 - Moderate
3 - Severe
4 - Proliferative DR
```
Images are stored under different folders for each grade.

### Data Splits

2049 training, 515 validation, 1101 test.

### Data Folder

```
.
├── test
│   ├── anodr
│   ├── bmilddr
│   ├── cmoderatedr
│   ├── dseveredr
│   └── eproliferativedr
├── train
│   └── ... // The same as test
└── val
    └── ... // The same as test
```
