# Dataset Card for JSIEC

## Table of Contents
- [Dataset Card for JSIEC](#dataset-card-for-jsiec)
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
- **Repository:** https://www.kaggle.com/datasets/linchundan/fundusimage1000
- **Paper:** https://www.nature.com/articles/s41467-021-25138-w

### Dataset Summary

The dataset contains 1000 fundus images which belong to 39 classes are come from the Joint Shantou International Eye Center (JSIEC), Shantou city, Guangdong province, China. The JSIEC data set was collected from PACS JSIEC between September 2009 and December 2018. The images were taken by a ZEISS FF450 Plus IR Fundus Camera (2009–2013) and Topcon TRC-50DX Mydriatic Retinal Camera (2013–2018) in a 35–50° field setting.

### Supported Tasks and Leaderboards

- Classification

### Languages

Not applicable

## Dataset Structure

### Data Instances

1000 fundus images which belong to 39 eye disease categories. The images are in various sizes in JPG format.

### Data Fields

The images are put into 39 subfolders corresponding to 39 disease categories. No further metadata is available.

### Data Splits

No official splits

### Data Folder

```
JSIEC
├── 0.0.Normal
├── 0.1.Tessellated fundus
├── 0.2.Large optic cup
├── 0.3.DR1
├── 10.0.Possible glaucoma
├── 10.1.Optic atrophy
├── 1.0.DR2
├── 1.1.DR3
├── 11.Severe hypertensive retinopathy
├── 12.Disc swelling and elevation
├── 13.Dragged Disc
├── 14.Congenital disc abnormality
├── 15.0.Retinitis pigmentosa
├── 15.1.Bietti crystalline dystrophy
├── 16.Peripheral retinal degeneration and break
├── 17.Myelinated nerve fiber
├── 18.Vitreous particles
├── 19.Fundus neoplasm
├── 2.0.BRVO
├── 20.Massive hard exudates
├── 2.1.CRVO
├── 21.Yellow-white spots-flecks
├── 22.Cotton-wool spots
├── 23.Vessel tortuosity
├── 24.Chorioretinal atrophy-coloboma
├── 25.Preretinal hemorrhage
├── 26.Fibrosis
├── 27.Laser Spots
├── 28.Silicon oil in eye
├── 29.0.Blur fundus without PDR
├── 29.1.Blur fundus with suspected PDR
├── 3.RAO
├── 4.Rhegmatogenous RD
├── 5.0.CSCR
├── 5.1.VKH disease
├── 6.Maculopathy
├── 7.ERM
├── 8.MH
└── 9.Pathological myopia
```
