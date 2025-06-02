# Dataset Card for REFUGE

## Table of Contents
- [Dataset Card for REFUGE](#dataset-card-for-refuge)
  - [Table of Contents](#table-of-contents)
  - [Dataset Description](#dataset-description)
    - [Dataset Summary](#dataset-summary)
    - [Supported Tasks and Leaderboards](#supported-tasks-and-leaderboards)
    - [Languages](#languages)
  - [Dataset Structure](#dataset-structure)
    - [Data Instances](#data-instances)
    - [Data Fields](#data-fields)
      - [Metadata](#metadata)
      - [Glaucoma diagnosis](#glaucoma-diagnosis)
      - [Disc \& Cup segmentation](#disc--cup-segmentation)
    - [Data Splits](#data-splits)
    - [Data Folder](#data-folder)

## Dataset Description

- **Homepage:** https://refuge.grand-challenge.org/Home2020/
- **Repository:** https://figshare.com/articles/figure/Refuge/26049574?file=47095942
- **Paper:** https://www.sciencedirect.com/science/article/pii/S1361841519301100

### Dataset Summary

The REFUGE dataset is sourced from the MICCAI 2018 Juzhong Retinal Glaucoma Challenge. It contains 1200 colored fundus images for glaucoma diagnosis and optic disc and cup segmentation. The images are split into 400 for training, 400 for validation, and 400 for testing. It is worth noting that the validation and test set do not have ground truth for glaucoma. 

### Supported Tasks and Leaderboards

- Classification
- Segmentation

### Languages

Not applicable

## Dataset Structure

### Data Instances

1200 images in JPG format with size 2124x2056 for training, 1634x1634 for validation and test. There are also Disc-cropped versions of the images. Masks are in PNG format.

### Data Fields

#### Metadata

Image metadata can be found in `{split}/index.json` where `{split}` can be `train`, `val`, or `test`. For the training set, there are 6 fields:

```
ImgName
Fovea_X
Fovea_Y
Size_X
Size_Y
Label
```

`ImgName` is the image filename, while `Fovea_X`, `Fovea_Y` denotes the coordinates of the fovea. `Size_X` and `size_Y` denote image width and height. For validation and test sets, they just have `ImgName`, `Size_X` and `size_Y` fields.

The original image can be found at `{split}/Images`. Additionally, the training set have an `illustrations` folder with annotated fovea point and disc & cup contours. The `{split}/Images_Cropped` folder holds the images cropped to the disc area.

#### Glaucoma diagnosis

Only the 400 images in the training set have glaucoma labels. It can be from the image filename. Images which names start with "g" are glaucoma images and "n" are normal. 

#### Disc & Cup segmentation

The ground truth mask in PNG format lies in the `{split}/Masks` folder and `{split}/Masks_Cropped` corresponds to `{split}/Images` and `{split}/Images_Cropped`. It has pixel values 0, 1, 2 denoting background, disc, and cup. `{split}/gts` folder also contains disc and cup mask, with 0, 128, 255 pixel values denoting cup, disc, and background.

### Data Splits

400 for training, 400 for validation, and 400 for testing, they lie in separate folders. The validation and test set do not have glaucoma label available.

In the training set, there are 40 glaucoma instances and 360 normal instances.

### Data Folder

```
REFUGE
├── Images_Square       // flat folder containing all images
├── Masks_Square        // flat folder containing all images
├── test
│   ├── gts
│   ├── Images
│   ├── Images_Cropped
│   ├── Masks
│   └── Masks_Cropped
├── train
│   ├── gts
│   ├── illustrations
│   ├── Images
│   ├── Images_Cropped
│   ├── Masks
│   └── Masks_Cropped
└── val
    ├── gts
    ├── Images
    ├── Images_Cropped
    ├── Masks
    └── Masks_Cropped
```
