# Dataset Card for Messidor2

## Table of Contents
- [Dataset Card for Messidor2](#dataset-card-for-messidor2)
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

- **Homepage:** https://www.adcis.net/en/third-party/messidor2/
- **Repository:** https://www.adcis.net/en/third-party/messidor2/
- **Paper:** http://www.ias-iss.org/ojs/IAS/article/view/1155; https://doi.org/10.1001/jamaophthalmol.2013.1743

### Dataset Summary

The Messidor-2 dataset is a collection of Diabetic Retinopathy (DR) examinations, consisting of 1748 macula-centered eye fundus images. Messidor-2 contains images from both eyes. It is composed by combining an extension set with all image pairs from the original Messidor dataset, that is 529 examinations (1058 images, saved in PNG format).

In order to populate Messidor-Extension, diabetic patients were recruited in the Ophthalmology department of Brest University Hospital (France) between October 16, 2009 and September 6, 2010. Eye fundi were imaged, without pharmacological dilation, using a Topcon TRC NW6 non-mydriatic fundus camera with a 45 degree field of view. Only macula-centered images were included in the dataset. Messidor-Extension contains 345 examinations (690 images).

The dataset we have is not the original one. As a result, we have only 1744 images without pairing information indicating which images are from the same patient. Additionally, the DR label in this dataset is not official, as the Messidor-2 team do not provide DR labels.

### Supported Tasks and Leaderboards

- Classification

### Languages

Not applicable

## Dataset Structure

### Data Instances

1744 fundus images in various sizes. All images are in PNG format.

### Data Fields

The images have DR grades as:

```
no dr
mild dr
moderate dr
severe dr
proliferative dr
```

### Data Splits

The 1744 images are split into 972 for training, 246 for validation, and 526 for testing.

### Data Folder

```
Messidor2
├── train
│   ├── anodr
│   ├── bmilddr
│   ├── cmoderatedr
│   ├── dseveredr
│   └── eproliferativedr
├── test
│   └── ... // the same as train
└── val
    └── ... // the same as train
```
