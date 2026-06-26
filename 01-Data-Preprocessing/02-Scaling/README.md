# 📊 Data Scaling Techniques for Machine Learning

This repository provides a comprehensive implementation and comparison of various **data scaling and normalization techniques** used in Machine Learning.

Feature scaling is a critical preprocessing step that ensures all features contribute equally to model performance and helps improve the convergence speed of gradient-based algorithms.

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

## 📌 Overview

In most Machine Learning workflows, features often have different units and value ranges. 

For example:

- Age may range from `0 - 100`
- Income may range from `20,000 - 200,000`
- Temperature may range from `-10 - 40`

These differences can negatively affect model performance because some features may dominate others.

This project demonstrates four common techniques for bringing features into a comparable scale using **Python** and **Scikit-learn**.

---

# 🚀 Implemented Methods

## 1. Manual Max Scaling

Manual Max Scaling is the simplest scaling approach.

Each data point is divided by the maximum value in the dataset:

\[
X_{scaled} = \frac{X}{X_{max}}
\]

### Example:

The largest value in the dataset becomes `1.0`, and all other values are transformed proportionally.

### ✅ Best For:

- Quick transformations
- Comparing values relative to the maximum value

---

## 2. Min-Max Scaler

The **Min-Max Scaler** transforms features into a fixed range, usually between `0` and `1`.

Formula:

\[
X_{scaled} = \frac{X - X_{min}}{X_{max}-X_{min}}
\]

### How It Works:

- Subtracts the minimum value of each feature
- Divides by the feature range

### Advantages:

✅ Keeps the original distribution  
✅ Produces values between 0 and 1  
✅ Works well with algorithms that do not assume a specific data distribution

### Common Use Cases:

- K-Nearest Neighbors (KNN)
- Neural Networks
- Distance-based algorithms

---

## 3. Standard Scaler (Standardization)

Standardization transforms the data so that:

- Mean = `0`
- Standard Deviation = `1`

Formula:

\[
X_{scaled} = \frac{X-\mu}{\sigma}
\]

Where:

- `μ` = Mean of the feature
- `σ` = Standard deviation

### How It Works:

1. Centers data by subtracting the mean
2. Scales values using standard deviation

### Advantages:

✅ Suitable for normally distributed data  
✅ Handles features with different units  
✅ Does not limit values to a fixed range

### Common Use Cases:

- Support Vector Machines (SVM)
- Linear Regression
- Principal Component Analysis (PCA)

---

## 4. Normalizer

Unlike the previous techniques that scale **features (columns)**, the Normalizer scales **individual samples (rows)**.

Each sample is transformed so that its vector length becomes equal to `1`.

Supported norms:

- L1 Norm
- L2 Norm
- Max Norm

### How It Works:

Each row is normalized independently:

\[
X_{scaled} = \frac{X}{||X||}
\]

### Advantages:

✅ Useful when vector direction is more important than magnitude  
✅ Commonly used in text and document processing

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
