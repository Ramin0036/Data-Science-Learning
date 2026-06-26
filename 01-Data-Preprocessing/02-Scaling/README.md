# 📊 Data Scaling Techniques for Machine Learning

This repository provides a comprehensive implementation and comparison of various **data scaling and normalization techniques** used in Machine Learning.

Feature scaling is a critical preprocessing step that ensures all features contribute equally to model performance and improves the convergence speed of gradient-based algorithms.

---

## 📋 Table of Contents

- [Overview](#overview)
- [Implemented Methods](#implemented-methods)
  - [Manual Max Scaling](#1-manual-max-scaling)
  - [Min-Max Scaler](#2-min-max-scaler)
  - [Standard Scaler](#3-standard-scaler-standardization)
  - [Normalizer](#4-normalizer)
- [Installation & Usage](#installation--usage)
- [Requirements](#requirements)

---

# 📌 Overview

In most Machine Learning workflows, features often have different units and value ranges.

For example:

- Age may range from `0 - 100`
- Income may range from `20,000 - 200,000`
- Temperature may range from `-10 - 40`

These differences can negatively affect model performance because some features may dominate others.

This repository demonstrates four common techniques for bringing features into a comparable scale using **Python** and **Scikit-learn**.

---

# 🚀 Implemented Methods

## 1. Manual Max Scaling

Manual Max Scaling is the simplest scaling approach.

Each data point is divided by the maximum value found in the dataset.

Formula:

$$
X_{scaled} = \frac{X}{X_{max}}
$$

### How It Works:

- Finds the maximum value in the dataset.
- Divides every value by that maximum value.
- The largest value becomes `1.0`.

### Example:

Original values:

```
[10, 20, 40]
```

After scaling:

```
[0.25, 0.5, 1.0]
```

### ✅ Best For:

- Quick transformations
- Comparing values relative to the maximum value

---

# 2. Min-Max Scaler

The **Min-Max Scaler** transforms features into a fixed range, usually between `0` and `1`.

Formula:

$$
X_{scaled} = \frac{X - X_{min}}{X_{max} - X_{min}}
$$

### How It Works:

- Subtracts the minimum value of each feature.
- Divides by the feature range (`max - min`).
- Maps values into a fixed interval.

### Advantages:

✅ Keeps the original distribution  
✅ Produces values between `0` and `1`  
✅ Prevents features with larger values from dominating

### Common Use Cases:

- K-Nearest Neighbors (KNN)
- Neural Networks
- Distance-based algorithms

---

# 3. Standard Scaler (Standardization)

Standardization transforms data so that it has:

- Mean = `0`
- Standard Deviation = `1`

Formula:

$$
X_{scaled} = \frac{X - \mu}{\sigma}
$$

Where:

- $\mu$ = Mean of the feature
- $\sigma$ = Standard deviation

### How It Works:

1. Calculates the mean of each feature.
2. Subtracts the mean from every value.
3. Divides by the standard deviation.

### Advantages:

✅ Suitable for normally distributed data  
✅ Handles features with different units  
✅ Does not restrict values to a fixed range  
✅ Less affected by scale differences

### Common Use Cases:

- Support Vector Machines (SVM)
- Linear Regression
- Principal Component Analysis (PCA)

---

# 4. Normalizer

Unlike previous scaling methods that operate on **features (columns)**, the Normalizer works on **individual samples (rows)**.

It scales each sample independently so that the vector length becomes equal to `1`.

Formula:

$$
X_{scaled} = \frac{X}{||X||}
$$

Where:

- `||X||` represents the norm of the vector.

### Supported Norms:

- L1 Norm
- L2 Norm
- Max Norm

### How It Works:

Each row is normalized independently without considering other samples.

### Advantages:

✅ Useful when vector direction is more important than magnitude  
✅ Commonly used in text and document processing  
✅ Works well with sparse data

### Common Use Cases:

- Text Classification
- Clustering
- Latent Semantic Analysis (LSA)

---

# ⚙️ Installation & Usage

## Prerequisites

Make sure you have Python installed.

Install the required libraries:

```bash
pip install numpy pandas scikit-learn
# 📄 License

This project is open-source and available under the MIT License.
