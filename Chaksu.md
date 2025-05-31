# Dataset Card for Chaksu

## Table of Contents
- [Dataset Card for Chaksu](#dataset-card-for-chaksu)
  - [Table of Contents](#table-of-contents)
  - [Dataset Description](#dataset-description)
    - [Dataset Summary](#dataset-summary)
    - [Supported Tasks and Leaderboards](#supported-tasks-and-leaderboards)
    - [Languages](#languages)
  - [Dataset Structure](#dataset-structure)
    - [Data Instances](#data-instances)
    - [Data Fields](#data-fields)
      - [Original Images](#original-images)
      - [Glaucoma Diagnosis](#glaucoma-diagnosis)
      - [Disc \& Cup Segmentation](#disc--cup-segmentation)
    - [Data Splits](#data-splits)
    - [Data Folder](#data-folder)

## Dataset Description

- **Homepage:** NA
- **Repository:** https://figshare.com/articles/dataset/Ch_k_u_A_glaucoma_specific_fundus_image_database/20123135?file=38944805
- **Paper:** https://www.nature.com/articles/s41597-023-01943-4

### Dataset Summary

Chaksu is a dataset from India composed of 1345 color fundus images acquired using three brands of commercially available fundus cameras: Remidio, Forus, and Bosch. All images have annotations from five experts of Disc & Cup area and normal versus glaucoma decisions. In addition, segmentation ground-truths of the OD and OC are provided by fusing the expert annotations using the mean, median, majority, and Simultaneous Truth and Performance Level Estimation (STAPLE) algorithm. Vertical, horizontal, and area cup-to-disc ratios are provided based on the expert annotations.


The Bosch images are in shape 1920x1440, with oval-shape field of view. There are 145 images from it.

The Forus images are in shape 2048x1536, with slightly oval-shape field of view, the upper and lower arches are clipped. There are 126 images from it.

The Remidio images are in shape 2448x3264, with circle shape field of view. There are 1074 images from it.

### Supported Tasks and Leaderboards

- Classification
- Segmentation

### Languages

Not Applicable

## Dataset Structure

### Data Instances

1345 color fundus images in JPG/PNG format. Disc & Cup masks are in TIF format.

### Data Fields

#### Original Images

The original images can be found in the `{split}/1.0_Original_Fundus_Images/{device}`, where the `{split}` can be either `Train` or `Test`, and the `{device}` can be `Bosch`, `Forus`, or `Remidio`.

#### Glaucoma Diagnosis

Note that the `{split}` can be either `Train` or `Test`, and the `{device}` can be `Bosch`, `Forus`, or `Remidio`.

In `{split}/6.0_Glaucoma_Decision/Glaucoma_Decision_Comparison_{device}.csv`:

```
Images
Expert 1
Expert 2
Expert 3
Expert 4
Expert 5
```

Where `Images` is the (transformed) name of image file. For example, `Image101.jpg` becomes `Image101.jpg-Image101-1.jpg` in this column. `Expert n` contains the decision of the `n`-th expert of whether the image has glaucoma or not. The value is either `GLAUCOMA SUSPECT` or `NORMAL`.

Additionally, `{split}/6.0_Glaucoma_Decision/Glaucoma_Decision_Comparison_{device}_majority.csv` contains one more column: `Majority Decision`, which is the majority decision among the 5 experts. Moreover, the `Expert n` column is renamed as `Expert.n`.

Note that for `Bosch` device, the two files in the `Train` subfolder is the same as those in the `Test` subfolder, but for the other devices, the two files in two subfolders are different.

#### Disc & Cup Segmentation

Basic annotation of segmentation lies in the `2.0_Doctors_Annotations` and `3.0_Doctors_Annotations_Binary_OD_OC` subfolders. Images in `2.0` are original image overlaid with expert-annotated contour of Disc or Cup, while images in `3.0` are binary
masks of Disc or Cup.

`4.0_OD_CO_Fusion_Images` and `5.0_OD_OC_Mean_Median_Majority_STAPLE` contains the processed mask from raw expert annotations. In addition to the results from each expert, four aggregation methods are used to define the final ground truth: mean, median, majority, and STAPLE algorithm. In `4.0`, the masks contains both Disc and Cup, with Disc has grayscale pixel values around 127 and Cup around 255, and it contains both single expert annotations and aggregated masks. On the other hand, `5.0` contains the aggregated mask for Disc and Cup respectively, with additional `overlay` aggregation, in which each expert contribute roughly 255/5 grayscale pixel value to the mask.

In addition to the masks, The dataset also contains the calculated measurements from the masks, they are included in `{split}/6.0_Glaucoma_Decision/{source}/{device}.csv`. Here, the `{split}` can be either `Train` or `Test`, and the `{device}` can be `Bosch`, `Forus`, or `Remidio`, and the `{source}` can be `Expert 1` to `Expert 5`, `Mean`, `Majority`, or `Median`. Within each file, the columns are:

```
Images
Disc Area
Cup Area
Rim Area
Cup Height
Cup Width
Disc Height
Disc Width
ACDR              // Cup-Disc Ratio w.r.t Area
VCDR              // Vertical Cup-Disc Ratio
HCDR              // Horizontal Cup-Disc Ratio
Glaucoma Decision
```

Where `Images` is the (transformed) name of image file. For example, `Image101.jpg` becomes `Image101.jpg-Image101-1.jpg` in this column. The unit of area/length here is pixels.

With in the training set, there are comparison between single expert annotated masks and aggregated masks. They are in `Train/6.0_Glaucoma_Decision/Expert {1..5}/{device}Vs{agg_method}{target}.csv`. Here, `{device}` can be `Bosch`, `Forus`, or `Remidio`; `{agg_method}` can be `Mean`, `Median`, or `Majority`; and `{target}` can be `Disc` or `Cup`. With in each file, the columns are 

```
ImageX
ImageY
Dice
Jaccard
Sensitivity
Specificity
Error Rate
Accuracy
Precision
False Positive Rate
```

Where `ImageX` is the actual name of image file, and `ImageY` is the transformed name of the image file, for example, `Image101.tif` becomes `Image101-1.tif`. The other columns are the distance/similarity metrics between the two masks.

### Data Splits

1009 images for training and 336 images for testing, they are in `Train` and `Test` subfolders.

### Data Folder

```
Chaksu
├── Readme_Chaksu IMAGE Database.pdf
├── Test
│   ├── 1.0_Original_Fundus_Images
│   │   ├── Bosch
│   │   ├── Forus
│   │   └── Remidio
│   ├── 2.0_Doctors_Annotations
│   │   └── Expert {1..5}
│   │       ├── Bosch
│   │       │   ├── Cup
│   │       │   └── Disc
│   │       ├── Forus
│   │       │   ├── Cup
│   │       │   └── Disc
│   │       └── Remidio
│   │           ├── Cup
│   │           └── Disc
│   ├── 3.0_Doctors_Annotations_Binary_OD_OC
│   │   └── ... // same structure as 2.0_Doctors_Annotations
│   ├── 4.0_OD_CO_Fusion_Images
│   │   ├── Expert {1..5}
│   │   │   ├── Bosch
│   │   │   ├── Forus
│   │   │   └── Remidio
│   │   ├── Bosch
│   │   │   ├── Majority
│   │   │   ├── Mean
│   │   │   ├── Median
│   │   │   └── STAPLE
│   │   ├── Forus
│   │   │   └── ... // same structure as Bosch
│   │   └── Remedio
│   │       └── ... // same structure as Bosch
│   ├── 5.0_OD_OC_Mean_Median_Majority_STAPLE
│   │   ├── Bosch
│   │   │   ├── Cup
│   │   │   │   ├── Majority
│   │   │   │   ├── Mean
│   │   │   │   ├── Median
│   │   │   │   ├── Overlay
│   │   │   │   └── STAPLE
│   │   │   └── Disc
│   │   │       └── ... // same structure as Cup
│   │   ├── Forus
│   │   │   └── ... // same structure as other folder in this directory
│   │   └── Remidio
│   │       └── ... // same structure as other folder in this directory
│   └── 6.0_Glaucoma_Decision
│       ├── Expert {1..5}
│       │   ├── Bosch.csv
│       │   ├── Forus.csv
│       │   └── Remidio.csv
│       ├── Majority
│       │   └── ... // same structure as Expert n
│       ├── Mean
│       │   └── ... // same structure as Expert n
│       ├── Median
│       │   └── ... // same structure as Expert n
│       ├── Glaucoma_Decision_Comparison_Bosch.csv
│       ├── Glaucoma_Decision_Comparison_Bosch_majority.csv
│       ├── Glaucoma_Decision_Majority_Forus.csv
│       ├── Glaucoma_Decision_Comparison_Forus_majority.csv
│       ├── Glaucoma_Decision_Majority_Remidio.csv
│       └── Glaucoma_Decision_Comparison_Remidio_majority.csv
└── Train
    ├── ... // same structure as Test counter part
    └── 6.0_Glaucoma_Decision
        ├── Expert {1..5}
        │   ├── Bosch.csv
        │   ├── BoschVsMajorityCup.csv
        │   ├── BoschVsMajorityDisc.csv
        │   ├── BoschVsMeanCup.csv
        │   ├── BoschVsMeanDisc.csv
        │   ├── BoschVsMedianCup.csv
        │   ├── BoschVsMedianDisc.csv
        │   ├── Forus.csv
        │   ├── ForusVsMajorityCup.csv
        │   ├── ForusVsMajorityDisc.csv
        │   ├── ForusVsMeanCup.csv
        │   ├── ForusVsMeanDisc.csv
        │   ├── ForusVsMedianCup.csv
        │   ├── ForusVsMedianDisc.csv
        │   ├── Remidio.csv
        │   ├── RemidioVsMajorityCup.csv
        │   ├── RemidioVsMajorityDisc.csv
        │   ├── RemidioVsMeanCup.csv
        │   ├── RemidioVsMeanDisc.csv
        │   ├── RemidioVsMedianCup.csv
        │   ├── RemidioVsMedianDisc.csv
        │   ├── MajorityVsMeanVsMedian.pdf
        │   ├── STAPLE_E1_Bosch_Cup.xls
        │   ├── STAPLE_E1_Bosch_Disc.xls
        │   ├── STAPLE_E1_Remedio_Cup.xls
        │   ├── STAPLE_E1_Remedio_Disc.xls
        │   ├── STAPLE_Forus_E1_Cup.xls
        │   └── STAPLE_Forus_E1_Disc.xls
        ├── ... // same structure as Test counter part
        ├── Glaucoma_Decision_Comparison_Bosch.csv
        ├── Glaucoma_Decision_Comparison_Bosch_majority.csv
        ├── Glaucoma_Decision_Comparison_Forus.csv
        ├── Glaucoma_Decision_Comparison_Forus_majority.csv
        ├── Glaucoma_Decision_Comparison_Remidio.csv
        └── Glaucoma_Decision_Comparison_Remidio_majority.csv

    
```
