# Dataset Card for OCTDL

## Table of Contents
- [Dataset Card for OCTDL](#dataset-card-for-octdl)
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

- **Homepage:** https://ieee-dataport.org/documents/octdl-optical-coherence-tomography-dataset-image-based-deep-learning-methods
- **Repository:** https://github.com/MikhailKulyabin/OCTDL
- **Paper:** https://www.nature.com/articles/s41597-024-03182-7

### Dataset Summary

The Optical Coherence Tomography Dataset for Image-Based Deep Learning Methods (OCTDL) dataset comprising over 2000 high-resolution OCT images labeled according to disease group and retinal pathology. The images have the naming convention as: `{disease}/{disease}_{patient_id}_{seq_num}.jpg`. The dataset consists of the following categories and images:

- Age-Related Macular Degeneration (AMD) - 1231 images;
- Diabetic Macular Edema (DME) - 147 images;
- Epiretinal Membrane (ERM) - 155 images;
- Normal (NO) - 332 images;
- Retinal Artery Occlusion (RAO) - 22 images;
- Retinal Vein Occlusion (RVO) - 101 images;
- Vitreomacular Interface Disease (VID) - 76 images.

### Supported Tasks and Leaderboards

- Classification
- Fairness (gender as sensitive attribute, but the missing rate is high)

### Languages

Not applicable

## Dataset Structure

### Data Instances

The dataset contains 2064 images in JPG format.

### Data Fields

The metadata is in `OCTDL_labels.csv`:

```
file_name
disease
subcategory
condition
patient_id
eye
sex
year
image_width
image_hight
```

Here `file_name` is the file name without extension. `disease` indicates the underlying disease of the image, corresponding to the disease categories in the data summary. `subcategory` and `condition` contains the stage/level of the disease, it takes different sets of values for different diseases:

```
AMD: normal-early-intermediate-late subcategory, with drusen-MNV_suspected-MNV conditions
DME: no subcategory, with DRIL-ME-DME conditions
ERM: no subcategory, with ERM condition
NO: no subcategory, with emmetropia-myopia conditions
RAO: no subcategory nor condition
RVO: KME-late subcategory, with DRIL-ME conditions 
VID: LH-MH-VMT subcategory, with MH condition
```

`eye` denotes the left-or-right eye of the image, with `OS` for left and `OD` for right eye, and `0` for unknown.

`sex` could be `F` or `M`, with `0` as unknown.

`year` is the year of image, with `0` as unknown.

`eye`, `sex`, and `year` have high missing rate.

### Data Splits

No official split.

### Data Folder

```
OCTDL
├── OCTDL_labels.csv
└── OCTDL
    ├── AMD
    ├── DME
    ├── ERM
    ├── NO
    ├── RAO
    ├── RVO
    └── VID
```
