# Deep Learning with mIF Images to Enhance T Cell Identification for Tumor - Automation of Infiltrating Lymphocytes (TILs) Scoring on H&E Images

**Project ID**: MAE24017  
**Supervisor**: Assoc. Prof. Cai Yiyu
**University**: Nanyang Technological University, Singapore  

---

## Table of Contents

- [Overview](#overview)
- [Objective](#objective)
- [Background](#background)
- [Methodology](#methodology)
- [Progress and Key Achievements](#progress-and-key-achievements)
- [Next Steps](#next-steps)
- [How to Use](#how-to-use)
- [Contributors](#contributors)

---

## Overview

This project explores the application of deep learning to **Hematoxylin & Eosin (H&E) images** with the aim of enhancing T Cell identification in tumor regions through automated scoring of Tumor Infiltrating Lymphocytes (TILs). Our goal is to create a robust and accessible approach for TIL scoring directly on H&E-stained images, utilizing advanced image segmentation and clustering methods to approximate the specificity of **Multiplex Immunofluorescence (mIF)** imaging. By focusing on models such as **SAM (Segment Anything Model)**, **K-means**, and **DBSCAN**, we aim to develop a framework that can perform accurate TIL scoring in settings without access to costly mIF imaging.

---

## Objective

This research aims to leverage H&E images to infer information that traditionally requires mIF imaging, allowing for:
- Efficient and automated TIL scoring in resource-limited settings.
- Enhanced cancer diagnostic insights by understanding tumor-immune interactions.
- Reduced reliance on costly imaging techniques by approximating TIL identification directly from H&E slides.

---

## Background

- **Hematoxylin & Eosin (H&E) Imaging**: A widely used and cost-effective staining technique in pathology, H&E provides key information about tissue morphology but lacks the cell-type specificity of mIF.
  
- **Multiplex Immunofluorescence (mIF) Imaging**: A technique that provides detailed insights into immune cell types, like TILs, and their interactions with tumor cells. While highly specific, mIF requires advanced infrastructure and is costly, limiting its accessibility.

- **Research Motivation**: TIL density and spatial distribution play a critical role in immunotherapy efficacy, especially in cancers responsive to immune modulation. By using deep learning to extract similar insights from H&E images, this project seeks to provide a scalable, accessible alternative to mIF for tumor diagnostics.

---

## Methodology

### 1. Data Acquisition and Preprocessing
- Collected Whole Slide Images (WSIs) stained with H&E.
- **Normalization of Stains**: Preprocessed the WSIs using stain normalization techniques to standardize color variations and improve segmentation consistency.

### 2. Model Exploration
- **Segment Anything Model (SAM)**:
  - SAM was used for multi-scale segmentation of WSIs, generating three distinct types of masks for each image:
    - A **broad, pixelated mask** covering eosin-stained areas.
    - A **highly localized mask** focusing on specific regions of interest.
    - A **comprehensive mask** outlining the entire tissue structure.
  - SAM’s versatility made it the most effective model so far in identifying TIL-rich regions within the tissue.
  
- **K-means and DBSCAN Clustering**:
  - Applied clustering models to identify distinct tissue patterns and localize TILs. K-means and DBSCAN were explored to detect cell clusters indicative of TILs within the SAM-generated masks.
  - While effective in certain cases, SAM was found to outperform these clustering techniques for our specific segmentation needs.

### 3. Cross-Validation with mIF Data
- Used mIF data as a ground truth for validating the accuracy of TIL detection in H&E images.
- Compared segmentation and scoring results across models to improve the SAM pipeline.

---

## Progress and Key Achievements

- **Segmentation and Mask Generation**: Developed a robust pipeline using SAM to generate multi-level segmentation masks for each WSI, enabling flexible analysis of tissue regions at different levels of specificity.
- **Normalization of H&E Stains**: Implemented a stain normalization step to standardize color variations, enhancing the accuracy and consistency of segmentation results.
- **Model Comparison**: Explored multiple models, including K-means, DBSCAN, and SAM, with SAM demonstrating the most promising results for accurate segmentation and TIL detection.
- **TIL Detection Pipeline**: Established a proof-of-concept TIL detection workflow using SAM-generated masks and validated it against mIF images.

### Sample Output

Below are examples of the original WSI and SAM-generated segmentation masks:

#### Original H&E-Stained WSI
![Original WSI](path_to_original_wsi_image)

#### SAM-Generated Masks
1. **Whole Tissue Segment Mask**
   ![Whole Tissue Mask](path_to_whole_tissue_mask_image)
   
2. **Broad Pixelated Mask Covering Eosin-Stained Region**
   ![Broad Mask](path_to_broad_mask_image)

3. **Highly Localized Mask (Potential ROI)**
   ![Localized Mask](path_to_localized_mask_image)

---

## Next Steps

- **Further Model Refinement**: Continue refining SAM’s segmentation capabilities and explore advanced clustering for more nuanced TIL detection.
- **Enhanced TIL Scoring Algorithm**: Develop an automated scoring system based on segmented regions to quantify TIL density.
- **Dataset Expansion**: Increase the diversity and volume of H&E and mIF image pairs for model training and validation, ensuring robustness across different tissue types and cancer profiles.
- **Comparative Analysis**: Conduct a comprehensive evaluation to measure the effectiveness of the SAM pipeline compared to traditional mIF-based TIL scoring.
