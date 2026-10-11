# K-Nearest Neighbors: From-Scratch Implementation and Experimental Study

## Overview

This project explores the K-Nearest Neighbors (KNN) algorithm from both an implementation and experimental perspective.

Instead of only using a machine learning library, the project focuses on understanding how KNN behaves under different conditions, implementing the algorithm from scratch, and validating the custom implementation against scikit-learn.

The Breast Cancer Wisconsin dataset is used for binary classification:

- **B** — Benign
- **M** — Malignant

---

## Project Objectives

The project investigates:

- Effect of feature scaling on KNN
- Effect of different values of K
- Euclidean vs Manhattan distance
- KNN implementation from scratch
- Validation against scikit-learn
- Effect of irrelevant/noisy features
- Evaluation beyond accuracy using precision, recall, F1-score, and confusion matrices

---

## Dataset

The dataset contains:

- 569 samples
- 30 numerical input features
- 2 target classes

The features describe characteristics such as:

- Radius
- Texture
- Perimeter
- Area
- Smoothness
- Compactness
- Concavity
- Concave points
- Symmetry
- Fractal dimension

The dataset is stored inside the `data/` directory so the notebook can be reproduced without relying on temporary Google Colab storage.

---

## Experimental Workflow

The project follows this sequence:

1. Dataset understanding and preprocessing
2. Baseline KNN
3. Feature scaling experiment
4. Effect of K
5. Distance metric comparison
6. KNN implementation from scratch
7. Validation against scikit-learn
8. Irrelevant-feature experiment
9. Final analysis and limitations

---

## Key Results

### Feature Scaling

Feature scaling produced a clear improvement in KNN performance.

| Metric | Unscaled | Scaled |
|---|---:|---:|
| Accuracy | ~0.91 | ~0.96 |
| Recall (M) | ~0.79 | ~0.90 |
| F1-score (M) | ~0.87 | ~0.94 |

This demonstrates the importance of scaling for distance-based algorithms.

---

### Effect of K

The strongest overall performance was observed around:

- **K = 5**
- **K = 7**

Both achieved approximately:

- Accuracy: **95.61%**
- Malignant Recall: **90.48%**
- Malignant F1-score: **93.83%**

---

### Distance Metrics

Euclidean and Manhattan distance were compared under the same experimental conditions.

Both produced similar results on this dataset.

---

## KNN From Scratch

A custom KNN classifier was implemented using Python and NumPy.

The implementation includes:

- Euclidean distance calculation
- Neighbor search
- K-nearest neighbor selection
- Majority voting
- Prediction for unseen samples

The custom implementation was validated against scikit-learn's `KNeighborsClassifier`.

### Validation Result

The custom implementation achieved:

- **95.61% test accuracy**
- **100% prediction agreement with scikit-learn**

under the same experimental conditions.

---

## Effect of Irrelevant Features

Random noise features were added to investigate how irrelevant dimensions affect KNN.

| Noise Features | Accuracy | Recall M | F1 M |
|---:|---:|---:|---:|
| 0 | 0.9561 | 0.9048 | 0.9383 |
| 2 | 0.9386 | 0.8571 | 0.9114 |
| 5 | 0.9211 | 0.8333 | 0.8861 |
| 10 | 0.9386 | 0.8571 | 0.9114 |
| 20 | 0.9211 | 0.8333 | 0.8861 |
| 30 | 0.9386 | 0.8810 | 0.9136 |

Overall, irrelevant features generally reduced performance, although the degradation was not strictly monotonic.

---

## Main Findings

- Feature scaling is very important for KNN.
- Small K values can be sensitive to noise.
- Moderate K values gave better generalization in this dataset.
- Euclidean and Manhattan distance behaved similarly in this experiment.
- A correct from-scratch implementation can reproduce scikit-learn predictions.
- Irrelevant dimensions can distort neighborhood relationships.
- Accuracy alone is not enough when class performance differs.

---

## Limitations

- Only one dataset was used.
- Most experiments used a single fixed train-test split.
- K values were explored using the test set during the learning phase.
- Only Euclidean and Manhattan distance were compared.
- Noise features were randomly generated.
- The custom KNN implementation does not use optimized nearest-neighbor search structures.
- No independent external validation dataset was used.

---

## Technologies Used

- Python
- NumPy
- Pandas
- Matplotlib
- scikit-learn
- Google Colab

---

## Repository Structure

```text
knn-from-scratch-experimental-study/
│
├── README.md
├── requirements.txt
├── KNN_Experimental_Study.ipynb
└── data/
    └── breast_cancer.xls
