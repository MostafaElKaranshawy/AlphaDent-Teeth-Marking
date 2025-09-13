# AlphaDent: Teeth Marking

**Competition / Dataset**: AlphaDent – Teeth marking

## Overview

AlphaDent is a dataset / competition focused on **automated tooth pathology detection** using photographs of the oral cavity. The goal is to build models that can identify and segment different dental pathologies from images.

---

## Key Details

| Aspect | Detail |
|---|---|
| **Data Source** | Intraoral photographs taken with a DSLR camera (high resolution) from 295 patients.  |
| **Number of Images** | Over 1,200 images for training/validation; additional unseen test images. |
| **Task Type** | Instance segmentation of pathology / abnormal areas on teeth.  |
| **Number of Classes** | 9 pathology classes. |

---

## Pathology Classes

The nine classes include (but are not limited to):  

- Abrasion (mechanical wear of hard tissue)
- Filling (restorations)
- Crown (types like metal-ceramic, ceramic, zirconium)  
- Multiple types of caries (varying by location and severity)

---

## Data Splits & Labeling

- Training / validation split is done **by patient** (so images from same patient are not split across train/valid).
- Test data: Images are from new time period; labels are withheld (used for leaderboard evaluation).
- Labeling format: Masks / polygons per instance; also text-files with normalized boundary coordinates.

---

## Evaluation Metric

- The main metric is **mean Average Precision at IoU threshold 0.50** (mAP@50) across all pathology classes.
- Other metrics (e.g. for more strict IoU thresholds) may also be reported.

---

## Baseline & Results (from Paper)

- Using **YOLOv8 (v8x-Large)** architecture with augmentations.
- For 9 classes, trained over ~100 epochs.
- Example mAP@50 on validation: in some classes quite good (e.g. Abrasion, Crown), in others lower (especially rare caries types).  
- They also ran experiments merging all caries types into a single class to address class imbalance.

---

## Challenges / Things to Watch Out For

- **Class imbalance**: Some classes have far fewer examples (rare caries types) which makes detection harder.
- **High resolution images** mean that memory/computation might be heavy.  
- **Generalization**: dataset collected mostly using one camera, similar settings. Models may perform worse on data with different lighting, cameras, etc.
- **Annotation quality**: As with many medical imaging datasets, domain expertise is required to label accurately; multi-annotator consistency may vary.  

---

## License & Access

- The dataset is published under an **open license**.
- Code for training, inference, and pre-trained model weights are released.
- Ethics / consent: Study approved by ethical committee; informed consent was obtained.

---

## How to Get Started

1. Download dataset from Kaggle (train/valid images + labels) and separate test set.  
2. Analyze class distributions; decide whether to merge rare classes or apply class weightings.  
3. Preprocess images (resize, normalization, augmentations).  
4. Choose model architecture (e.g. Mask R-CNN, YOLO-v8, etc.) for instance segmentation.  
5. Train, validate (using mAP@50), tune hyperparameters.  
6. Test on withheld test set; submit predictions to Kaggle leaderboard.

---

## References

- “AlphaDent: A dataset for automated tooth pathology detection” (Evgeniy I. Sosnin et al., 2025)
- Kaggle: AlphaDent: Teeth marking – problem statement.

---
