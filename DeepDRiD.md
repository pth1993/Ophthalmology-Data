# Dataset Card for DeepDRiD

## Table of Contents
- [Dataset Card for DeepDRiD](#dataset-card-for-deepdrid)
  - [Table of Contents](#table-of-contents)
  - [Dataset Description](#dataset-description)
    - [Dataset Summary](#dataset-summary)
    - [Supported Tasks and Leaderboards](#supported-tasks-and-leaderboards)
    - [Languages](#languages)
  - [Dataset Structure](#dataset-structure)
    - [Data Instances](#data-instances)
    - [Data Fields](#data-fields)
      - [Patient source](#patient-source)
      - [DR grading](#dr-grading)
      - [Image quality assessment](#image-quality-assessment)
    - [Data Splits](#data-splits)
    - [Data Folder](#data-folder)

## Dataset Description

- **Homepage:** https://github.com/deepdrdoc/DeepDRiD
- **Repository:** https://zenodo.org/records/6452623
- **Paper:** https://www.sciencedirect.com/science/article/pii/S2666389922001040

### Dataset Summary

The DeepDRiD dataset is constructed by including patients from different projects in Shanghai, including participants in the Shanghai Diabetic Complication Screening Project, Nicheng Diabetes Screening Project, and Nation-wide Screening for Complications of Diabetes, for regular fundus images. They collect regular fundus images and ultra-widefield (UWF) fundus images. They collected 2000 fundus images from 500 patients for regular fundus images, with 4 images per patient, 2 for each eye. For UWF images, they collect 256 images from another 128 patients. Diabetic Retinopathy (DR) grade and image quality labels are annotated for regular fundus images, but UWF images have only DR grades.

### Supported Tasks and Leaderboards

- Classification (DR grade and image quality)
- Fairness (source of image)
- Domain adaptation or generalization

### Languages

Not Applicable

## Dataset Structure

### Data Instances

2000 regular fundus images in various sizes in JPG format, 256 UWF fundus image (3900x3072) in JPG format.

### Data Fields

#### Patient source

For the training and validation set of regular fundus image, the source of patient can be found in `regular_fundus_images/regular-fundus-{split}/regular-fundus-source-{split}.csv`. The split can be `training` or `validation`. In this file there are several columns

```
patient_id
image_id
image_path
Source
```

`image_id` is the image filename without extension. Note that `image_path` Here is **NOT CORRECT**.

`Source` is the source of the patient. It can be `Nicheng`, `Shanghai`, or `Nation` denoting different project the patient comes from.

#### DR grading

DR grades for the dataset has five levels based on the International Clinical DR (ICDR) 4 classification scale: (1) no apparent retinopathy (grade 0), (2) mild NPDR (grade 1), (3) moderate NPDR (grade 2), (4) severe NPDR (grade 3), and (5) PDR (grade 4).

For training and validation set, the DR labels can be found in `regular_fundus_images/regular-fundus-{split}/regular-fundus-{split}.csv` for regular fundus images and `ultra-widefield_images/ultra-widefield-{split}/ultra-widefield-{split}.csv` for UWF images. For test set, the DR labels are in `regular_fundus_images/Online-Challenge1&2-Evaluation/Challenge1_labels.xlsx` and `ultra-widefield_images/Online-Challenge3-Evaluation/Challenge3_labels.xlsx`. 

The training and validation of the regular fundus images labels consists of three columns in the metadata:
```
left_eye_DR_Level
right_eye_DR_Level
patient_DR_Level
``` 
While each row in the metadata corresponds to image for just one eye, the field for the other eye is left blank. `patient_DR_Level` is the maximum grade of the two eyes.

For other metadata file, there's only one column for DR grade, which is `DR_level`.

#### Image quality assessment

The scoring system for image quality has 4 sections: Artifact, Clarity, Field definition, and Overall quality.

| Type             | Image quality specification                                                                                     | Score |
|------------------|------------------------------------------------------------------------------------------------------------------|-------|
| Artifact         | no artifacts                                                                                                     | 0     |
|                  | artifacts are outside the aortic arch with scope less than ¼ of the image                                        | 1     |
|                  | artifacts do not affect the macular area with range less than ¼                                                  | 4     |
|                  | artifacts cover more than ¼ but less than ½ of the image                                                         | 6     |
|                  | artifacts cover more than ½ without fully covering the posterior pole                                            | 8     |
|                  | cover the entire posterior pole                                                                                  | 10    |
| Clarity          | clarity only level I vascular arch is visible                                                                    | 1     |
|                  | level II vascular arch and a small number of lesions are visible                                                 | 4     |
|                  | level III vascular arch and some lesions are visible                                                             | 6     |
|                  | level III vascular arch and most lesions are visible                                                             | 8     |
|                  | level III vascular arch and all lesions are visible                                                              | 10    |
| Field definition | field definition do not include the optic disc and macula                                                        | 1     |
|                  | only contain either optic disc or macula                                                                         | 4     |
|                  | contain optic disc and macula                                                                                    | 6     |
|                  | the optic disc or macula is outside the 1 papillary diameter and within the 2 papillary diameter range of center | 8     |
|                  | the optic disc and macula are within 1 papillary diameter of the center                                          | 10    |
| Overall quality  | quality is not good enough for the diagnosis of retinal diseases                                                 | 0     |
|                  | quality is good enough for the diagnosis of retinal diseases                                                     | 1     |

Only regular fundus images have the 4 section quality annotations. They are in the corresponding columns in the metadata file.

### Data Splits

The dataset have 1200 regular fundus images for training, 400 for validation, and 400 for testing. For UWF images, they have 154 for training, 50 for validation, and 52 for testing. Note that test set do not have any label.

### Data Folder

```
DeepDRiD
├── regular_fundus_images
│   ├── Online-Challenge1&2-Evaluation
│   │   ├── Challenge1_upload.csv
│   │   ├── Challenge2_upload.csv
│   │   ├── Challenge1_labels.xlsx
│   │   ├── Challenge1_labels.xlsx
│   │   ├── Images
│   │   └── Readme.docx
│   ├── regular-fundus-training
│   │   ├── Images
│   │   ├── Readme.docx
│   │   └── regular-fundus-training.csv
│   └── regular-fundus-validation
│       ├── Images
│       ├── Readme.docx
│       └── regular-fundus-validation.csv
└── ultra-widefield_images
    ├── Online-Challenge3-Evaluation
    │   ├── Challenge3_upload.csv
    │   ├── Challenge3_labels.xlsx
    │   ├── Images
    │   └── Readme.docx
    ├── ultra-widefield-training
    │   ├── Images
    │   ├── Readme.txt
    │   └── ultra-widefield-training.csv
    └── ultra-widefield-validation
        ├── Images
        ├── Readme.txt
        └── ultra-widefield-validation.csv
```
