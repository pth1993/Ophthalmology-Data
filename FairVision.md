# Dataset Card for FairCLIP

## Table of Contents
- [Dataset Description](#dataset-description)
  - [Dataset Summary](#dataset-summary)
  - [Supported Tasks](#supported-tasks-and-leaderboards)
  - [Languages](#languages)
- [Dataset Structure](#dataset-structure)
  - [Data Instances](#data-instances)
  - [Data Fields](#data-instances)
  - [Data Splits](#data-instances)

## Dataset Description

- **Homepage:** https://github.com/Harvard-Ophthalmology-AI-Lab/FairVision
- **Repository:** https://drive.google.com/drive/folders/1sLX2O_0AlrjY6JmdKijiV1zducsOsd0m?usp=drive_link
- **Paper:** https://arxiv.org/pdf/2310.02492

### Dataset Summary

The FairVision dataset includes 10,000 subjects for Age-Related Macular Degeneration (AMD), Diabetic Retinopathy (DR), and glaucoma separately, totaling 30,000 subjects with comprehensive demographic identity attributes including age, gender, race, ethnicity, preferred language, and marital status. Each subject has one Scanning Laser Ophthalmoscopy (SLO) fundus photo and one sample of Optical Coherence Tomography (OCT) B-scans. The size of OCT B-scans is 200 x 200 x 200 in glaucoma. The size of OCT B-scans is 128 x 200 x 200 in AMD and DR.

### Supported Tasks and Leaderboards

- Classification
- Fairness

### Languages

Not applicable.

## Dataset Structure

### Data Instances

10,000 OCT B-scans (128 * 200 * 200) and 10,000 SLO images (200 * 200) in npz format for AMD.
10,000 OCT B-scans (128 * 200 * 200) and 10,000 SLO images (200 * 200) in npz format for DR.
10,000 OCT B-scans (200 * 200 * 200) and 10,000 SLO images (200 * 200) in npz format for Glaucoma.

### Data Fields

- AMD

  - In data_summary.csv

  ```
  - filename
  - age
  - gender
  - race
  - ethnicity
  - language
  - maritalstatus
  - amd
  - use
  ```

  - In .npz files

  ```
  - oct_bscans: images of OCT B-scans
  - slo_fundus: image of SLO fundus
  - race: 0 - Asian, 1 - Black, 2 - White
  - male: 0 - Female, 1 - Male
  - hispanic: 0 - Non-Hispanic, 1 - Hispanic
  - maritalstatus: 0 - Married, 1 - Single, 2 - Divorced, 3 - Widowed, 4 - Leg-Sep
  - language: 0 - English, 1 - Spanish, 2 - Others
  - amd_condition: AMD conditions - {'not.in.icd.table', 'no.amd.diagnosis', 'early.dry', 'intermediate.dry', 'advanced.atrophic.dry.with.subfoveal.involvement', 'advanced.atrophic.dry.without.subfoveal.involvement', 'wet.amd.active.choroidal.neovascularization', 'wet.amd.inactive.choroidal.neovascularization', 'wet.amd.inactive.scar'}
  ```
  The condition would be converted into the label of AMD by the condition-disease mapping.
  ```
  condition_disease_mapping = {'not.in.icd.table': 0.,
                          'no.amd.diagnosis': 0.,
                          'early.dry': 1.,
                          'intermediate.dry': 2.,
                          'advanced.atrophic.dry.with.subfoveal.involvement': 3.,
                          'advanced.atrophic.dry.without.subfoveal.involvement': 3.,
                          'wet.amd.active.choroidal.neovascularization': 3.,
                          'wet.amd.inactive.choroidal.neovascularization': 3.,
                          'wet.amd.inactive.scar': 3.}
  ```

- DR

  - In data_summary.csv

  ```
  - filename
  - age
  - gender
  - race
  - ethnicity
  - language
  - maritalstatus
  - dr
  - use
  ```

  - In .npz files

  ```
  - oct_bscans: images of OCT B-scans
  - slo_fundus: image of SLO fundus
  - race: 0 - Asian, 1 - Black, 2 - White
  - male: 0 - Female, 1 - Male
  - hispanic: 0 - Non-Hispanic, 1 - Hispanic
  - maritalstatus: 0 - Married, 1 - Single, 2 - Divorced, 3 - Widowed, 4 - Leg-Sep
  - language: 0 - English, 1 - Spanish, 2 - Others
  - dr_class: 0 - no DR, 1 -  DR
  - dr_subtype: DR conditions - {'not.in.icd.table', 'no.dr.diagnosis', 'mild.npdr', 'moderate.npdr', 'severe.npdr', 'pdr'}
  ```

  The condition would be converted into the label of vision-threatening DR by the condition-disease mapping.

  ```
  condition_disease_mapping = {'not.in.icd.table': 0.,
                      'no.dr.diagnosis': 0.,
                      'mild.npdr': 0.,
                      'moderate.npdr': 0.,
                      'severe.npdr': 1.,
                      'pdr': 1.}
  ```

- Glaucoma

  - In data_summary.csv

  ```
  - filename
  - age
  - gender
  - race
  - ethnicity
  - language
  - maritalstatus
  - md
  - glaucoma
  - use
  ```

  - In .npz files

  ```
  - oct_bscans: images of OCT B-scans
  - slo_fundus: image of SLO fundus
  - race: 0 - Asian, 1 - Black, 2 - White
  - male: 0 - Female, 1 - Male
  - hispanic: 0 - Non-Hispanic, 1 - Hispanic
  - maritalstatus: 0 - Married, 1 - Single, 2 - Divorced, 3 - Widowed, 4 - Leg-Sep
  - language: 0 - English, 1 - Spanish, 2 - Others
  - glaucoma: the label of glaucoma disease, 0 - non-glaucoma, 1 - glaucoma
  ```

### Data Splits

For each disease (i.e., AMD, DR, Glaucoma), data is divided into 7,000 training, 1,000 validation, and 2,000 test samples. The file data_summary.csv details the division of data into training, validation, and testing sets. 

### Data Folder
```
FairVision
├── AMD
├──── ReadMe
├────── data_description_amd.txt
├────── data_summary_amd.csv
├──── Training
├──── Validation
├──── Test
├── DR
├──── ReadMe
├────── data_description_amd.txt
├────── data_summary_amd.csv
├──── Training
├──── Validation
├──── Test
├── Glaucmoa
├──── ReadMe
├────── data_description_amd.txt
├────── data_summary_amd.csv
├──── Training
├──── Validation
└──── Test
```