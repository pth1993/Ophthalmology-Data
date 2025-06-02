# Dataset Card for MuReD

## Table of Contents
- [Dataset Card for MuReD](#dataset-card-for-mured)
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
- **Repository:** https://data.mendeley.com/datasets/pc4mb3h8hz/1
- **Paper:** https://arxiv.org/abs/2207.02335

### Dataset Summary

The MuReD dataset is constructed using images collected from three different state-of-the-art sources, i.e., ARIA, STARE, and RFMiD datasets, and performing a sequence of post-processing steps to ensure the quality of the images, a wide range of diseases to classify, and a sufficient number of samples per disease label.
The MuReD dataset consists of 2208 images with 20 different labels, with varying image quality and resolution.

Source datasets are listed below:
1. ARIA dataset (http://www.damianjjfarnell.com/?page_id=276)
2. STARE dataset (https://cecas.clemson.edu/~ahoover/stare/)
3. RFMiD dataset (https://dx.doi.org/10.21227/s3g7-st65)

### Supported Tasks and Leaderboards

- Classification

### Languages

Not applicable

## Dataset Structure

### Data Instances

The dataset contains 2208 images in TIF or PNG format of variant sizes.

### Data Fields

The metadata is stored in `train_data.csv` and `test_data.csv`. There are 21 columns:

```
ID
DR
NORMAL
MH
ODC
TSLN
ARMD
DN
MYA
BRVO
ODP
CRVO
CNV
RS
ODE
LS
CSR
HTR
ASR
CRS
OTHER
```

Here `ID` is the image name without extensions. The other 20 columns contain binary indicator for the corresponding condition of the image. `NORMAL` is 1 when all other conditions have value 0.

The meaning of columns and number of images are shown here:

| Acronym | Full Name                          | Training | Testing    | Total |
|---------|------------------------------------|----------|------------|-------|
| DR      | Diabetic Retinopathy               | 396      | 99         | 495   |
| NORMAL  | Normal Retina                      | 395      | 98         | 493   |
| MH      | Media Haze                         | 135      | 34         | 169   |
| ODC     | Optic Disc Cupping                 | 211      | 52         | 263   |
| TSLN    | Tessellation                       | 125      | 31         | 156   |
| ARMD    | Age-Related Macular Degeneration   | 126      | 32         | 158   |
| DN      | Drusen                             | 130      | 32         | 162   |
| MYA     | Myopia                             | 71       | 18         | 89    |
| BRVO    | Branch Retinal Vein Occlusion      | 63       | 16         | 79    |
| ODP     | Optic Disc Pallor                  | 50       | 12         | 62    |
| CRVO    | Central Retinal Vein Occlusion     | 44       | 11         | 55    |
| CNV     | Choroidal Neovascularization       | 48       | 12         | 60    |
| RS      | Retinitis                          | 47       | 11         | 58    |
| ODE     | Optic Disc Edema                   | 46       | 11         | 57    |
| LS      | Laser Scars                        | 37       | 9          | 46    |
| CSR     | Central Serous Retinopathy         | 29       | 7          | 36    |
| HTR     | Hypertensive Retinopathy           | 28       | 7          | 35    |
| ASR     | Arteriosclerotic Retinopathy       | 26       | 7          | 33    |
| CRS     | Chorioretinitis                    | 24       | 6          | 30    |
| OTHER   | Other Diseases                     | 209      | 52         | 261   |

### Data Splits

444 for testing and 1764 for training. The split is stored in `train_data.csv` and `test_data.csv`.

### Data Folder

```
MURED
├── train_data.csv
├── test_data.csv
└── images
```
