# Dataset Card for OCTglaucoma

## Table of Contents
- [Dataset Card for OCTglaucoma](#dataset-card-for-octglaucoma)
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
- **Repository:** https://zenodo.org/records/1481223#.Xr06Q2gzbIU
- **Paper:** https://arxiv.org/abs/1807.04855

### Dataset Summary

OCT scans centered on the optic nerve head (ONH) were acquired from 624 patients on a Cirrus SD-OCT Scanner (Zeiss, Dublin, CA, USA). Scans with signal strength less than 7 were discarded, resulting in a total of 1110 scans for the experiments. The scans were kept in their original laterality (no flipping of left into right eye). 263 of the 1110 scans were diagnosed as healthy and 847 with primary open angle glaucoma (POAG). Glaucomatous eyes were defined as those with glaucomatous visual field defects and at least 2 consecutive abnormal test results. The scans had physical dimensions of 6x6x2 mm with a corresponding size of 200x200x1024 voxels per volume, they are down-sampled to 64x64x128 in the repo and the dimensions are reorganized to 64x128x64 (slices, height, width). 

### Supported Tasks and Leaderboards

- Classification

### Languages

Not applicable

## Dataset Structure

### Data Instances

1110 3D OCT scans in the NPY format. Each contains a scan in shape 64x128x64 (slices, height, width). The file names are in format `{label}-{pid}-{date}-{eye}.npy`, `{label}` can be either `Normal` or `POAG` (primary open angle glaucoma); `{eye}` can be `OD` for the right eye or `OS` for the left eye.

### Data Fields

There's no additional metadata for the dataset, all metadata are encoded in the file name.

### Data Splits

No official split 

### Data Folder

```
OCTglaucoma
└── {label}-{pid}-{date}-{eye}.npy
```
