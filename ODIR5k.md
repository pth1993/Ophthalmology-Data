# Dataset Card for ODIR5k

## Table of Contents
- [Dataset Card for ODIR5k](#dataset-card-for-odir5k)
  - [Table of Contents](#table-of-contents)
  - [Dataset Description](#dataset-description)
    - [Dataset Summary](#dataset-summary)
    - [Supported Tasks and Leaderboards](#supported-tasks-and-leaderboards)
    - [Languages](#languages)
  - [Dataset Structure](#dataset-structure)
    - [Data Instances](#data-instances)
    - [Data Fields](#data-fields)
      - [Original dataset metadata](#original-dataset-metadata)
      - [Preprocessed dataset metadata](#preprocessed-dataset-metadata)
    - [Data Splits](#data-splits)
    - [Data Folder](#data-folder)

## Dataset Description

- **Homepage:** https://odir2019.grand-challenge.org/dataset/
- **Repository:** https://www.kaggle.com/datasets/andrewmvd/ocular-disease-recognition-odir5k
- **Paper:** https://arxiv.org/pdf/2102.07978

### Dataset Summary

ODIR5k is constructed from a structured ophthalmic database of 5,000 patients with age, color fundus photographs from left and right eyes and doctors' diagnostic keywords from doctors (in short, ODIR-5K). This dataset is "real-life" set of patient information collected by Shanggong Medical Technology Co., Ltd. from different hospitals/medical centers in China. In these institutions, fundus images are captured by various cameras in the market, such as Canon, Zeiss and Kowa, resulting into varied image resolutions. Annotations are labeled by trained human readers with quality control management. They classify patient into eight labels including normal (N), diabetes (D), glaucoma (G), cataract (C), AMD (A), hypertension (H), myopia (M) and other diseases/abnormalities (O) based on both eye images and additionally patient age. The publishing of this dataset follows the ethical and privacy rules of China.

### Supported Tasks and Leaderboards

- Classification
- Fairness (Age, Sex)

### Languages

English for diagnostic keywords.

## Dataset Structure

### Data Instances

There are 8000 images in total in JPG format. The size of images varies. There's a preprocessed version of ODIR5k, which contains 6392 center cropped images in the training set resized to 512x512.

### Data Fields

#### Original dataset metadata

The original metadata of the dataset is in `ODIR-5K/ODIR-5K/data.xlsx`. The metadata only contain the 3500 patients in the training set, with each row denotes one patient (two images). It includes the following columns:

```
ID
Patient Age
Patient Sex
Left-Fundus
Right-Fundus
Left-Diagnostic Keywords
Right-Diagnostic Keywords
N
D
G
C
A
H
M
O
```

`Left-Fundus` and `Right-Fundus` contains the filename of the image, it is always in format `{ID}_{eye}.jpg` where `ID` is the ID number of the patient and `eye` could be either `left` or `right`. Both eyes have a `Diagnostic Keywords` column, containing a short free text for the diagnosis of the image. Here are some examples:

```
laser spot, moderate non proliferative retinopathy
moderate non proliferative retinopathy, hypertensive retinopathy
normal fundus
...
```

The following eight columns contains binary indicators of eye conditions, including normal (N), diabetic retinopathy (D), glaucoma (G), cataract (C), AMD (A), hypertension (H), myopia (M) and other diseases/abnormalities (O). The label is at patient level, it can be seen as the label union of both eyes. Normal (N) will only be 1 of the patient do not have any disease in both eyes. For example, if a patient has a normal eye and glaucoma in the other eye, the label would be 1 for glaucoma and 0 for others; if a patient has glaucoma in one eye and diabetic retinopathy in the other eye, the label would be 1 for glaucoma, 1 for diabetic retinopathy, and 0 for others.

#### Preprocessed dataset metadata

Based on the original images and metadata, there is a processed metadata containing 6392 images from 3358 patients in the training set. The inclusion criteria are unknown. 

The processed images lie in `preprocessed_images` folder, they are created by cropping the FOV of the original image and resize it to 512x512.

The metadata of processed images is in `full_df.csv`. Each row in this file denotes one image instead of one patient. First, it keeps all columns from the `ODIR-5K/ODIR-5K/data.xlsx`, with the patient-level information and label. It also has additional columns:

```
filepath
labels
target
filename
```

`filepath` here is **NOT** the correct path and should be ignored. `filename` is the corresponding file name of the row, it would be one of the `Left-Fundus` and `Right-Fundus` depending on the eye. The `N,D,G,C,A,H,M,O` columns still contain patient-level labels, and the `labels` column contains the eye-level label, the value is in the form of `List[Str]`, which is the list of columns that have value 1 in `N,D,G,C,A,H,M,O` for the given eye, based on the `Diagnostic Keywords`. `target` is the multi-hot list version of `label`, in the string format.

For example, a patient have a normal right eye and cataract in her left eye. She has one row in `ODIR-5K/ODIR-5K/data.xlsx`:

```
ID: 294
Patient Age: 69
Patient Sex: Female
Left-Fundus: 294_left.jpg
Right-Fundus: 294_right.jpg
Left-Diagnostic Keywords: cataract
Right-Diagnostic Keywords: normal fundus
N: 0
D: 0
G: 0
C: 1
A: 0
H: 0
M: 0
O: 0
```

Then she has two rows in `full_df.csv`:

```
ID: 294
Patient Age: 69
Patient Sex: Female
Left-Fundus: 294_left.jpg
Right-Fundus: 294_right.jpg
Left-Diagnostic Keywords: cataract
Right-Diagnostic Keywords: normal fundus
N: 0
D: 0
G: 0
C: 1
A: 0
H: 0
M: 0
O: 0
filepath: ...
labels: ['C']
target: "[0, 0, 0, 1, 0, 0, 0, 0]"
filename: 294_left.jpg
```
and
```
ID: 294
Patient Age: 69
Patient Sex: Female
Left-Fundus: 294_left.jpg
Right-Fundus: 294_right.jpg
Left-Diagnostic Keywords: cataract
Right-Diagnostic Keywords: normal fundus
N: 0
D: 0
G: 0
C: 1
A: 0
H: 0
M: 0
O: 0
filepath: ...
labels: ['N']
target: "[1, 0, 0, 0, 0, 0, 0, 0]"
filename: 294_right.jpg
```

Note that the difference only lies in the last 3 columns.

### Data Splits

There are 7000 images in the training set and 1000 images in the test set. Note that images in the test set do not have annotations. The 6392 preprocessed images are all from the training set.

### Data Folder

```
ODIR-5K
├── ODIR-5K
│   └── ODIR-5K
│       ├── data.xlsx       // original metadata
│       ├── Testing Images
│       └── Training Images
├── full_df.csv             // processed metadata
└── preprocessed_images
```
