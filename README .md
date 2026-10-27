# A Multispectral Texture-Feature Machine Learning Framework for Cotton Bacterial Blight Severity Classification

**Authors:** Hafiz Muhammad Ijaz ([ORCID: 0009-0002-5249-0622](https://orcid.org/0009-0002-5249-0622)), Muhammad Asadullah (corresponding author)
**Affiliation:** Department of Information Technology, The Islamia University of Bahawalpur, Pakistan

---

## 1. Description

This project classifies the severity of cotton bacterial blight (*Xanthomonas campestris* pv. *malvacearum*) from leaf images with a feature-based machine-vision pipeline.

The framework integrates four main components:
1. **Image pre-processing:** resizing, grayscale conversion (CVIPtools), and contrast enhancement with noise reduction.
2. **ROI segmentation and feature extraction:** regions of interest (ROIs) are segmented at different pixel sizes (16 × 16 up to 256 × 256). **55 candidate features** (first-order histogram, GLCM/Haralick texture, binary shape, and rotation-scale-translation (RST) invariant features) are extracted from each ROI with CVIPtools.
3. **Feature selection:** **Correlation-based Feature Selection (CFS)** reduces the 55 features to a compact subset (19 features plus the class label = a 20-attribute file).
4. **Classification:** **twelve machine learning classifiers** and **four deep learning models** are trained and evaluated in Weka with **10-fold cross-validation**.

The task is a three-class severity problem:

| Class | Meaning |
|-------|---------|
| Low infection | Small affected leaf area, early and mild symptoms |
| Normal infection | Moderate, clearly visible portion of the leaf shows blight symptoms |
| High infection | Extensive necrotic and water-soaked lesions |

---

## 2. Dataset Information

| Item | Details |
|------|---------|
| Name | A Multispectral Texture-Feature Machine Learning Framework for Cotton Bacterial Blight Severity Classification |
| Repository | GitHub: https://github.com/ijazhafiz7-gif/Cotton-Bacterial-Blight-Classification |
| DOI | [10.5281/zenodo.23682983](https://doi.org/10.5281/zenodo.23682983) (Zenodo) |
| Origin | Cotton leaf images collected from fields in Ahmedpur East, Punjab, Pakistan, captured under natural field lighting and checked manually before processing |
| Ethics approval | Not applicable: plant images, no human or animal subjects |
| Modality | RGB photographs of cotton leaves, provided as 256 × 256 pixel JPEG images |
| Size | 900 leaf images (300 per class) |
| Annotation | Each image was manually assigned to Low, Normal or High infection before image processing |
| License | Creative Commons Attribution 4.0 International (CC BY 4.0) |

**Images per category:**

| Category | Images | Proportion |
|----------|--------|------------|
| Low infection | 300 | 33.33% |
| Normal infection | 300 | 33.33% |
| High infection | 300 | 33.33% |
| **Total** | **900** | **100%** |

The dataset is balanced on purpose, so that accuracy and F-measure are not dominated by an over-represented class. Feature extraction produces 900 ROI instances per class (2,700 instances in total), which are the instances used in cross-validation.

### Dataset Source
The dataset is hosted in the GitHub repository https://github.com/ijazhafiz7-gif/Cotton-Bacterial-Blight-Classification and archived on Zenodo with the DOI https://doi.org/10.5281/zenodo.23682983.

---

## 3. Project Structure / Code Information

| File / tool | Purpose | Main outputs |
|-------------|---------|--------------|
| CVIPtools | **Step 1.** Image preprocessing, ROI extraction and extraction of the 55 candidate features | Feature file (ARFF) |
| Weka (ARFF files) | **Step 2.** CFS feature selection, training and 10-fold cross-validation of 16 classifiers | Accuracy, confusion matrices, per-class metrics |
| `features/Cotton_Balanced_900.arff` | Selected 20-attribute feature set (2,700 instances) used to train and evaluate all classifiers | |
| `manifest.csv` | Lists every image with its unique ID and infection class | |
| `results/*.docx` | Weka output for each of the 12 machine learning classifiers (10-fold cross-validation, 2,700 instances) | Accuracy, per-class metrics, confusion matrix |
| `README.md` | This file | |

---

## 4. Requirements

### Software Requirements
| Software | Version |
|----------|---------|
| CVIPtools | 3.9 |
| Weka | 3.6.2 |

### Computing Infrastructure
| Component | Specification |
|-----------|---------------|
| Device | Acer TravelMate 8571 laptop |
| Operating system | Windows 10 Pro, 64-bit (version 20H2, OS build 19042.1706) |
| CPU | Intel(R) Core(TM)2 Duo CPU U9400 @ 1.40 GHz (x64-based processor) |
| RAM | 6.00 GB |
| GPU | Not required (CVIPtools and Weka were run on the CPU) |

---

## 5. Dataset Preparation

### Data layout
```text
cotton_blight_dataset/
├── README.md
├── manifest.csv
├── Low_Infection/       (300 images: 1.jpg ... 300.jpg)
├── Normal_Infection/    (300 images: 1.jpg ... 300.jpg)
├── High_Infection/      (300 images: 1.jpg ... 300.jpg)
├── features/
│   └── Cotton_Balanced_900.arff
└── results/
    └── 12 Weka output files (.docx), one per classifier
```

All images are 256 × 256 pixel RGB JPEG files. File names repeat across the three class folders (each has 1.jpg to 300.jpg), so use the `image_id` column of `manifest.csv` as the unique identifier.

### manifest.csv
`manifest.csv` has one row per image (900 rows):

| Column | Meaning |
|--------|---------|
| `path` | Relative path of the image inside the dataset folder |
| `image_id` | Unique image ID (class name + number, e.g. `Low_1`) |
| `class` | Infection severity: `Low`, `Normal` or `High` |

### Feature file (ARFF)
The ARFF file `features/Cotton_Balanced_900.arff` has 2,700 rows (900 per class). Each row holds the **19 selected features** and the class label (20 attributes). The class values in the file are `Lowinfection`, `Normalinfection` and `HighInfection`:

| Feature group | Selected features | Count |
|---------------|-------------------|-------|
| Shape / binary | Object row coordinate, object column coordinate, area, centroid (row), centroid (column), second moment, perimeter, Euler number | 8 |
| Projection | Projections 1-11 (normalized row and column projection profiles) | 11 |
| **Total** | | **19** |

---

## 6. Usage Instructions

### Step 1: Download the Dataset
Download the dataset from GitHub (https://github.com/ijazhafiz7-gif/Cotton-Bacterial-Blight-Classification) and unzip it.

### Step 2: Pre-process the Images
Open CVIPtools and load the images. Resize, convert to grayscale, and apply contrast enhancement and noise reduction.

### Step 3: Segment ROIs
Segment ROIs at the sizes used in the study (16 × 16 and 256 × 256 pixels).

### Step 4: Extract Features
Extract features (histogram, texture, binary and RST invariant) for each ROI and save them in ARFF format.

### Step 5: Feature Selection
Open the ARFF file in Weka. Apply Correlation-based Feature Selection (CFS) to keep the 20-attribute subset.

### Step 6: Run the Classifiers
Run the classifiers in the Weka Classify tab with *10-fold cross-validation* and note the weighted-average results.

### Fixed Settings
| Setting | Value |
|---------|-------|
| Images | 900 (300 per class) |
| Resized image / ROI sizes | 256 × 256 and 16 × 16 pixels |
| Candidate features | 55 |
| Selected features | 19 + class label = 20 attributes |
| Feature selection | Correlation-based Feature Selection (CFS) |
| Evaluation | 10-fold cross-validation |
| Machine learning classifiers | Lazy.IB1, Lazy.IBK, Trees.RandomTree, Meta.RandomCommittee, Trees.RandomForest, Rules.NNge, Meta.RotationForest, Meta.Decorate, Trees.SimpleCart, Trees.J48, Trees.J48graft, Trees.BFTree |
| Deep learning models | CNN, LSTM, Bi-LSTM, MLP (on feature vectors, not raw pixels) |
| Classifier parameters | Weka 3.6.2 settings as recorded in the result files in `results/`, e.g. IBk -K 1; RandomForest -I 10 -K 0 -S 1; RandomTree -K 0 -M 1.0 -S 1; J48 -C 0.25 -M 2; RandomCommittee -S 1 -I 10 |
| Random seed | 1 (as recorded in the Weka settings, `-S 1`) |

---

## 7. Methodology

The complete workflow follows the sequence:

```text
Cotton Leaf Images (Low / Normal / High)
        ↓
Pre-processing (Resizing, Grayscale, Enhancement)
        ↓
ROI Segmentation (16×16 to 256×256)
        ↓
Feature Extraction (55 features, CVIPtools)
        ↓
Correlation-based Feature Selection (20 attributes)
        ↓
Classification (12 ML classifiers + 4 deep learning models, Weka)
        ↓
10-fold Cross-Validation and Performance Evaluation
```

### 7.1 Pre-processing
1. **Resizing:** every image is resized to a fixed size so that ROI segments are comparable.
2. **Grayscale conversion:** a luminance-weighted transformation of the R, G and B channels (CVIPtools).
3. **Enhancement:** contrast enhancement and noise-reduction filters, to suppress background noise and normalize brightness.

### 7.2 ROI Segmentation
The infected leaf region is separated from the background. ROIs are produced at several pixel resolutions, from 16 × 16 to 256 × 256, to test how ROI size affects accuracy. Small ROIs emphasize local texture and early lesions, large ROIs keep more spatial context.

### 7.3 Feature Extraction (CVIPtools)
55 features per ROI from four families:
- First-order histogram features (mean, standard deviation, skewness, energy, entropy).
- Second-order GLCM (Haralick) texture features.
- Binary shape features (area, centroid, moments, perimeter, Euler number, thinness ratio, aspect ratio, projections).
- Seven RST invariant moments.

### 7.4 Feature Selection
CFS keeps features that correlate strongly with the class and weakly with each other. The merit of a subset S with k features is Merit_S = k · r_cf / sqrt(k + k(k-1) · r_ff), where r_cf is the mean feature-class correlation and r_ff the mean feature-feature correlation. The final set is dominated by shape descriptors and projection profiles.

### 7.5 Classification
12 machine learning classifiers and 4 deep learning models run in Weka on the 20-attribute feature file.

### 7.6 Evaluation Method
10-fold cross-validation: the data is split into ten nearly equal subsets, nine are used for training and one for testing, ten times, and the scores are averaged. The evaluation covers:
- **Per-class and weighted-average results** for Low, Normal and High infection.
- **Confusion matrices** for the best classifiers.
- **Classifier comparison:** all 12 machine learning classifiers on the 16 × 16 ROI feature set, plus deep learning models and a Naive Bayes baseline.
- **ROI size analysis:** 256 × 256 versus 16 × 16 pixels.
- **Comparison with published methods:** Anwar, Rahim Kolachi et al. (2023), Kumar Gudela et al. (2023), Islam et al. (2023), M. Shao et al. (2023), Y. Shao et al. (2024), Akbar et al. (2024), Anwar, Soomro et al. (2023) and Suleman Memon et al. (2022) (Table 10 of the article).

### 7.7 Assessment Metrics
| Metric | Why it is used |
|--------|----------------|
| Accuracy | Overall proportion of correctly classified instances. |
| TP rate (recall / sensitivity) | Share of each class that is correctly recognized. |
| FP rate | How often samples of other classes are wrongly assigned to a class. |
| Precision | Of the instances predicted as a class, the fraction that truly belong to it. |
| F-measure | Harmonic mean of precision and recall. |
| ROC area | Threshold-independent discrimination ability. |
| Cohen's kappa | Agreement beyond chance. |
| MAE / RAE / RMSE | Size of the prediction error. |
| MCC | Single balanced score for multi-class results (Gorodkin's generalization). |
| Confusion matrix | Shows which classes are confused with each other. |

---

## 8. Performance Summary

### Main results (Lazy.IB1, ROI 16 × 16, 10-fold cross-validation)

| Class | TP Rate | FP Rate | Precision | Recall | F-Measure | ROC Area |
|-------|---------|---------|-----------|--------|-----------|----------|
| Low infection | 0.913 | 0.037 | 0.925 | 0.913 | 0.919 | 0.938 |
| Normal infection | 0.940 | 0.038 | 0.926 | 0.940 | 0.933 | 0.951 |
| High infection | 0.947 | 0.025 | 0.950 | 0.947 | 0.948 | 0.961 |
| **Weighted average** | **0.933** | **0.033** | **0.933** | **0.933** | **0.933** | **0.950** |

**Confusion matrix (rows = actual, columns = predicted):**

| Actual \ Predicted | Low | Normal | High | Total |
|--------------------|-----|--------|------|-------|
| Low | 822 | 50 | 28 | 900 |
| Normal | 37 | 846 | 17 | 900 |
| High | 30 | 18 | 852 | 900 |
| **Total** | 889 | 914 | 897 | 2,700 |

### All machine learning classifiers (ROI 16 × 16, weighted averages)

| Classifier | Kappa | MAE | RAE (%) | TP Rate | FP Rate | F-Score | MCC | ROC | Accuracy (%) |
|------------|-------|-----|---------|---------|---------|---------|-----|-----|--------------|
| IB1 | 0.900 | 0.0444 | 10.00 | 0.933 | 0.033 | 0.933 | 0.900 | 0.950 | **93.33** |
| IBK | 0.898 | 0.0451 | 10.16 | 0.932 | 0.034 | 0.932 | 0.898 | 0.970 | 93.22 |
| RandomTree | 0.895 | 0.0468 | 10.53 | 0.930 | 0.035 | 0.930 | 0.895 | 0.947 | 93.00 |
| Random Committee | 0.894 | 0.0471 | 10.60 | 0.930 | 0.035 | 0.930 | 0.894 | 0.974 | 92.96 |
| RandomForest | 0.893 | 0.0645 | 14.52 | 0.929 | 0.036 | 0.928 | 0.893 | 0.976 | 92.85 |
| NNge | 0.890 | 0.0489 | 11.00 | 0.927 | 0.037 | 0.927 | 0.890 | 0.945 | 92.67 |
| Rotation Forest | 0.863 | 0.0900 | 20.24 | 0.909 | 0.046 | 0.909 | 0.863 | 0.979 | 90.89 |
| Decorate | 0.815 | 0.1505 | 33.86 | 0.877 | 0.062 | 0.876 | 0.815 | 0.957 | 87.67 |
| SimpleCart | 0.798 | 0.1043 | 23.46 | 0.866 | 0.067 | 0.865 | 0.799 | 0.947 | 86.56 |
| J48 | 0.782 | 0.1113 | 25.05 | 0.855 | 0.073 | 0.854 | 0.783 | 0.946 | 85.48 |
| J48graft | 0.782 | 0.1113 | 25.05 | 0.855 | 0.073 | 0.854 | 0.783 | 0.946 | 85.48 |
| BFTree | 0.748 | 0.1225 | 27.56 | 0.832 | 0.084 | 0.831 | 0.749 | 0.942 | 83.19 |

Among the deep learning models, CNN and MLP reached only about 33.33% accuracy, and a Naive Bayes baseline reached 63.75%.

### Effect of ROI size

| ROI size | Lazy.IB1 (%) | Lazy.IBK (%) | Best ensemble classifier (%) |
|----------|--------------|--------------|------------------------------|
| 256 × 256 | 93.22 | 93.22 | 92.93 (Random Committee) |
| 16 × 16 | **93.33** | 93.22 | 92.93 (Random Committee) |

---

## 9. Outputs Generated
The project provides the following outputs:
- Weka result file for each of the 12 machine learning classifiers (`results/*.docx`)
- Per-class metrics (TP rate, FP rate, precision, recall, F-measure, ROC area)
- Weighted-average results and overall accuracy
- Confusion matrices for the best classifiers
- Classifier comparison (12 machine learning classifiers, deep learning models, Naive Bayes baseline)
- ROI size comparison (256 × 256 versus 16 × 16)
- Comparison with published methods (Table 10 of the article)

---

## 10. Evaluation Environment
The framework was developed and tested using:
- **Operating System:** Windows 10 Pro, 64-bit (version 20H2, OS build 19042.1706)
- **Device:** Acer TravelMate 8571 laptop
- **CPU / RAM:** Intel(R) Core(TM)2 Duo CPU U9400 @ 1.40 GHz / 6.00 GB
- **GPU:** Not required (CPU only)
- **Software:** CVIPtools 3.9, Weka 3.6.2
- **Validation:** 10-fold cross-validation, random seed 1

---

## 11. Results and Discussion
The instance-based **Lazy.IB1** classifier gave the best result: **93.33% weighted-average accuracy** on the 16 × 16 ROI feature set, ahead of Lazy.IBK (93.22%), Random Tree (93.00%), Random Committee (92.93%) and Random Forest (92.85%).

Every one of the twelve machine learning classifiers outperformed the CNN and MLP models, which reached only about 33.33% on the same pre-extracted features. Most errors occur between Low and Normal infection, which have the most similar textures. High infection is recognized best (TP rate 0.947).

The 16 × 16 ROI performed slightly better than 256 × 256 (93.33% versus 93.22%), so the features carry disease information at both scales. The approach is interpretable and light enough for low-cost decision support in agriculture. A formal timing benchmark was not performed.

---

## 12. Limitations
- **Three severity levels only:** completely healthy leaves are not included in the classification.
- **Limited data source:** images come from a relatively small number of fields and locations with specific lighting, so results may differ for other climates, cotton varieties, fields or cameras.
- **Visible symptoms only:** other foliar diseases can look similar, and temperature, humidity and rainfall were not considered.
- **No independent test set:** results come from 10-fold cross-validation on one dataset, with no external validation.
- **No timing benchmark:** claims about computational efficiency are based on model and input size, not measured run time.

---

## 13. Citations

**Code / paper:**
```
Ijaz, H. M., & Asadullah, M. (2026). A Multispectral Texture-Feature Machine Learning
Framework for Cotton Bacterial Blight Severity Classification. PeerJ Computer Science.
Data and code: https://doi.org/10.5281/zenodo.23682983
```

**Dataset:**
```
Ijaz, H. M., & Asadullah, M. (2026). A Multispectral Texture-Feature Machine Learning Framework for Cotton
Bacterial Blight Severity Classification [Dataset]. Zenodo. https://doi.org/10.5281/zenodo.23682983
```

---

## 14. Conclusion
The proposed framework integrates:
- Image pre-processing and ROI segmentation at several pixel sizes
- Texture, histogram, binary and RST feature extraction (55 features) with CVIPtools
- Correlation-based Feature Selection (reduced to 20 attributes)
- Twelve machine learning classifiers and four deep learning models evaluated in Weka
- 10-fold cross-validation with per-class, weighted-average and confusion-matrix analysis

The framework provides a compact, interpretable pipeline for classifying Low, Normal and High bacterial blight severity in cotton leaves, with the best accuracy of 93.33% (Lazy.IB1, 16 × 16 ROI).

---

## 15. License and Contribution Guidelines
- **README and feature files:** CC BY 4.0, same as the dataset.
- **Dataset:** Creative Commons Attribution 4.0 International (CC BY 4.0).

