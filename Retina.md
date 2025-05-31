# Dataset Card for Retina

## Table of Contents
- [Dataset Card for Retina](#dataset-card-for-retina)
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
- **Repository:** https://www.kaggle.com/datasets/jr2ngb/cataractdataset
- **Paper:** NA

### Dataset Summary

Retina is a dataset on Kaggle containing cataract and normal eye image for cataract detection. It contains 601 colored fundus images covering 3 diseases: cataract, glaucoma, and retina disease. The images in our repo is preprocessed by the AutoMorph tool (https://github.com/rmaphoh/AutoMorph), they are cropped to FOV and resized to 256x256. However, the source of the images is unknown.

### Supported Tasks and Leaderboards

- Classification

### Languages

Not applicable

## Dataset Structure

### Data Instances

All 601 images are 256x256, in PNG format.

### Data Fields

No metadata nor demographic info. Images are grouped in subfolders: `{split}/{disease}/{image_name}.png`

### Data Splits

Train, validation, test in separate folders. 336 for training, 84 for validation, and 181 for testing.

|Disease|# train|# val|# test|# total|
|----|----|----|----|----|
|normal|168|42|90|300|
|cataract|56|14|30|100|
|glaucoma|56|14|31|101|
|retina disease|56|14|30|100|
|Total|336|84|181|601|

### Data Folder

```
Retina
├── readme.txt
├── test
│   ├── anormal
│   ├── bcataract
│   ├── cglaucoma
│   └── ddretina_disease
├── train
│   ├── anormal
│   ├── bcataract
│   ├── cglaucoma
│   └── ddretina_disease
└── val
    ├── anormal
    ├── bcataract
    ├── cglaucoma
    └── ddretina_disease
```
