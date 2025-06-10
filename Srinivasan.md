# Dataset Card for Srinivasan

## Table of Contents
- [Dataset Card for Srinivasan](#dataset-card-for-srinivasan)
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

- **Homepage:** https://people.duke.edu/~sf59/Srinivasan_BOE_2014_dataset.htm
- **Repository:** https://people.duke.edu/~sf59/Srinivasan_BOE_2014_dataset.htm
- **Paper:** https://opg.optica.org/boe/fulltext.cfm?uri=boe-5-10-3568&id=301172

### Dataset Summary

This dataset consists of volumetric scans acquired from 45 patients: 15 normal patients, 15 patients with dry AMD, and 15 patients with DME using Spectralis SD-OCT (Heidelberg Engineering Inc.). There are 3231 2D OCT slices in total. The images seem to undergo affine transformations to and padded with white background to be 512x496 in size.

### Supported Tasks and Leaderboards

- classification

### Languages

Not applicable

## Dataset Structure

### Data Instances

3231 2D OCT slices from 45 patients of 512x496 size.

### Data Fields

Images can be categorized as AMD, DME, and normal. Subfolders denote different patient, named as `{label}{seq}` where label could be `AMD`, `DME`, or `NORMAL`, and `seq` runs from 1 to 15.

### Data Splits

No official splits

### Data Folder

```
Srinivasan
├── AMD1
│   └── TIFFs
│       └── 8bitTIFFs
├── AMD10
│   └── ... // same as above
├── AMD11
├── AMD12
├── AMD13
├── AMD14
├── AMD15
├── AMD2
├── AMD3
├── AMD4
├── AMD5
├── AMD6
├── AMD7
├── AMD8
├── AMD9
├── DME1
├── DME10
├── DME11
├── DME12
├── DME13
├── DME14
├── DME15
├── DME2
├── DME3
├── DME4
├── DME5
├── DME6
├── DME7
├── DME8
├── DME9
├── NORMAL1
├── NORMAL10
├── NORMAL11
├── NORMAL12
├── NORMAL13
├── NORMAL14
├── NORMAL15
├── NORMAL2
├── NORMAL3
├── NORMAL4
├── NORMAL5
├── NORMAL6
├── NORMAL7
├── NORMAL8
└── NORMAL9
```
