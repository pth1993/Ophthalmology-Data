# Dataset Card for LAG

## Table of Contents
- [Dataset Card for LAG](#dataset-card-for-lag)
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

- **Homepage:** https://github.com/smilell/AG-CNN
- **Repository:** https://www.dropbox.com/scl/fi/x7vbgeezo5rqlw4rwaucn/LAG_database_part_1.rar?rlkey=m4i5qzjt1f9pelhx1ad2t4boh&e=1&dl=0
- **Paper:** https://ieeexplore.ieee.org/document/8756196

### Dataset Summary

The LAG database contains 11,760 fundus images corresponding to 4,878 suspicious and 6,882 negative glaucoma samples. All the samples are labelled with the diagnosis results (0 refers to negative glaucoma and 1 refers to suspicious glaucoma). 5,824 fundus images are further labelled with attention regions based on an alternative method for eye tracking, in which 2,392 are positive glaucoma and the rest 3,432 are negative glaucoma.

### Supported Tasks and Leaderboards

- Classification

### Languages

Not applicable

## Dataset Structure

### Data Instances

11,760 fundus images corresponding to 4,878 suspicious and 6,882 negative glaucoma samples. The images are in 500x500 size and JPG format. There are 5,824 fundus images further labelled with attention regions, the attention map are in the size of 112x112 and JPG format.

### Data Fields

The images have only glaucoma label. With the negative samples lies in `non_glaucoma/image` and positive samples in `suspicious_glaucoma/image` folder. The attention maps lie in `{label}/attention_map` folder. There's also a `{label}/label` folder, the files in this folder are text files (TXT format), they correspond to the images with the same filename, containing 1 for suspicious glaucoma and 0 for negative glaucoma.

### Data Splits

No official split.

### Data Folder

```
LAG
├── non_glaucoma
│   ├── attention_map
│   ├── image
│   └── label
└── suspicious_glaucoma
    ├── attention_map
    ├── image
    └── label
```
