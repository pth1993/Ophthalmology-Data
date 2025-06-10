# Dataset Card for RFMiD

## Table of Contents
- [Dataset Card for RFMiD](#dataset-card-for-rfmid)
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
- **Repository:** https://ieee-dataport.org/open-access/retinal-fundus-multi-disease-image-dataset-rfmid
- **Paper:** https://www.sciencedirect.com/science/article/pii/S1361841524002901, https://doi.org/10.3390/data6020014

### Dataset Summary

The RFMiD dataset consists of 3200 fundus images captured using three different fundus cameras with 46 conditions annotated through adjudicated consensus of two senior retinal experts. The retinal images were acquired using three different digital fundus cameras, TOPCON 3D OCT-2000, Kowa VX-10𝛼, and TOPCON TRC-NW300 during the period 2009–2020. They are centered either on the macula or the optic disc (OD). These images are acquired at an Eye Clinic, Sushrusha Hospital, and Center of Excellence in Signal and Image Processing, SGGS Institute of Engineering and Technology both located in Nanded, (M.S.), India.

### Supported Tasks and Leaderboards

- Classification

### Languages

## Dataset Structure

### Data Instances

### Data Fields

| Abbreviation | Full Name                                 |
| ------------ | ----------------------------------------- |
| NL           | Normal                                    |
| DR           | Diabetic Retinopathy                      |
| ARMD         | Age-Related Macular Degeneration          |
| MH           | Media Haze                                |
| DN           | Drusen                                    |
| MYA          | Myopia                                    |
| BRVO         | Branch Retinal Vein Occlusion             |
| TSLN         | Tessellation                              |
| ERM          | Epiretinal Membrane                       |
| LS           | Laser Scars                               |
| MS           | Macular Scar                              |
| CSR          | Central Serous Retinopathy                |
| ODC          | Optic Disc Cupping                        |
| CRVO         | Central Retinal Vein Occlusion            |
| TV           | Tortuous Vessels                          |
| AH           | Asteroid Hyalosis                         |
| ODP          | Optic Disc Pallor                         |
| ODE          | Optic Disc Edema                          |
| ST           | Optociliary Shunt                         |
| AION         | Anterior Ischemic Optic Neuropathy        |
| PT           | Parafoveal Telangiectasia                 |
| RT           | Retinal Traction                          |
| RS           | Retinitis                                 |
| CRS          | Chorioretinitis                           |
| EDN          | Exudation                                 |
| RPEC         | Retinal Pigment Epithelium Changes        |
| MHL          | Macular Hole                              |
| RP           | Retinitis Pigmentosa                      |
| CWS          | Cotton Wool Spots                         |
| CB           | Coloboma                                  |
| ODPM         | Optic Disc Pit Maculopathy                |
| PRH          | Preretinal Hemorrhage                     |
| MNF          | Myelinated Nerve Fibers                   |
| HR           | Hemorrhagic Retinopathy                   |
| CRAO         | Central Retinal Artery Occlusion          |
| TD           | Tilted Disc                               |
| CME          | Cystoid Macular Edema                     |
| PTCR         | Post-Traumatic Choroidal Rupture          |
| CF           | Choroidal Folds                           |
| VH           | Vitreous Hemorrhage                       |
| MCA          | Macroaneurysm                             |
| VS           | Vasculitis                                |
| BRAO         | Branch Retinal Artery Occlusion           |
| PLQ          | Plaque                                    |
| HPED         | Hemorrhagic Pigment Epithelial Detachment |
| CL           | Collateral                                |


### Data Splits

3200 images divided into a training set (1920 images), validation (640 images), and testing set (640 images)

### Data Folder
