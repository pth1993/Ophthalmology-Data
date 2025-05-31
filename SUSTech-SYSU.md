# Dataset Card for SUSTech-SYSU

## Table of Contents
- [Dataset Card for SUSTech-SYSU](#dataset-card-for-sustech-sysu)
  - [Table of Contents](#table-of-contents)
  - [Dataset Description](#dataset-description)
    - [Dataset Summary](#dataset-summary)
    - [Supported Tasks and Leaderboards](#supported-tasks-and-leaderboards)
    - [Languages](#languages)
  - [Dataset Structure](#dataset-structure)
    - [Data Instances](#data-instances)
    - [Data Fields](#data-fields)
      - [DR grading](#dr-grading)
      - [Exudates detection](#exudates-detection)
      - [Optic Disc and fovea location](#optic-disc-and-fovea-location)
    - [Data Splits](#data-splits)
    - [Data Folder](#data-folder)

## Dataset Description

- **Homepage:** NA
- **Repository:** https://figshare.com/s/792d1b02f65be0c08214?file=25320596
- **Paper:** https://www.nature.com/articles/s41597-020-00755-0

### Dataset Summary

This is a dataset with 1219 colored fundus images collected from Diabetic Retinopathy patients and health controls with annotations of exudate lesions, left-versus-right eye label, DR grade (severity scale) from three different grading protocols (International Clinical DR Severity Scale, American Academy of Ophthalmology, and Scottish DR grading protocol), and the bounding box of the optic disc (OD), and fovea location. Files are named as `n.jpg`, with n ranging between 0001 and 1219 indicating the `n`-th sample. 

### Supported Tasks and Leaderboards

- Classification
- Object Detection: Optic Disc and fovea

### Languages

Not applicable

## Dataset Structure

### Data Instances

1219 colored fundus images in JPG format. The size is 2880x2136. The upper and lower arches are cropped, a small left arch is also cropped.

### Data Fields

#### DR grading

The DR grades from three grading protocols are in `images/originalImages/drLables.csv`, with columns:

```
Fundus_images
left_versus_right_eye(left_0_right_1)
DR_grade(International_Clinical_DR_Severity_Scale)
DR_grade(American_Academy_of_Ophthalmology)
DR_grade(Scottish_DR_grading_protocol)
```
Here `Fundus_images` is the file name in `images/originalImages`. The grades scores run from 0 to 5, with 0 representing normal healthy, and 1 to 5 respectively representing mild non-proliferative DR, moderate non-proliferative DR, severe non-proliferative DR, proliferative DR, and DR with laser spots or scars. Another CSV file named `images/originalImages/c5_DR_reclassified.csv` provides the DR labels for images belonging to category 5 assessed via the three protocols, it has the same columns as `drLables.csv` except `left_versus_right_eye`.

#### Exudates detection

Exudates bounding boxes are available for 564 images start from `0656.jpg`, they are named as `images/exudatesLabels/n.xml`, with `n` from 0656 to 1219.

In each XML file, there's a `<size>` tag specifying the size of the image:

```xml
...
<size>
	<width>2880</width>
	<height>2136</height>
	<depth>3</depth>
</size>
...
```

And a series of `<objects>` specifying the type and location of exudates.

```xml
...
<object>
	<name>ex</name>
	<pose>Unspecified</pose>
	<truncated>0</truncated>
	<difficult>0</difficult>
	<bndbox>
		<xmin>2262</xmin>
		<ymin>1940</ymin>
		<xmax>2317</xmax>
		<ymax>1985</ymax>
	</bndbox>
</object>
...
```

Here `ex` in `<name>` stands for hard exudates and `se` for soft exudates. `<bndbox>` is the bounding box.

#### Optic Disc and fovea location

The location of Optic Disc and fovea are in `images/odFoveaLabels/n.xml` for all images. It has the same structure as files in `exudatesLabels`, but each of them contains only two objects:

```xml
...
<object>
	<name>OD</name>
	<pose>Unspecified</pose>
	<truncated>0</truncated>
	<difficult>0</difficult>
	<bndbox>
		<xmin>143</xmin>
		<ymin>991</ymin>
		<xmax>537</xmax>
		<ymax>1419</ymax>
	</bndbox>
</object>
<object>
	<name>fovea</name>
	<pose>Unspecified</pose>
	<truncated>0</truncated>
	<difficult>0</difficult>
	<bndbox>
		<xmin>1401</xmin>
		<ymin>1404</ymin>
		<xmax>1402</xmax>
		<ymax>1405</ymax>
	</bndbox>
</object>
```

### Data Splits

No official splits for this dataset.

### Data Folder
```
SUSTech-SYSU
├── LICENSE.txt
├── README.txt
└── images
    ├── exudatesLabels
    ├── odFoveaLabels
    └── originalImages
        ├── {0000-1219}.jpg
        ├── drLables.csv
        └── c5_DR_reclassified.csv
```