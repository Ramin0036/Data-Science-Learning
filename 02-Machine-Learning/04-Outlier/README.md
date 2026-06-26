# Outlier Detection using Statistical and Machine Learning Methods

## Overview

Outlier detection is a fundamental step in data preprocessing and exploratory data analysis (EDA). An **outlier** is an observation that deviates significantly from the rest of the data. Outliers may occur due to measurement errors, data entry mistakes, or naturally rare events.

Identifying and handling outliers can improve the performance of machine learning models, increase prediction accuracy, and provide more reliable statistical analysis.

This project explores both **statistical** and **machine learning** approaches for outlier detection.

---

# Statistical Methods

Statistical methods detect outliers based on the statistical properties of the data. They are generally simple, interpretable, and computationally efficient.

## 1. Box Plot (Interquartile Range - IQR)

The Box Plot method identifies outliers using the **Interquartile Range (IQR)**.

The IQR is calculated as:

```text
IQR = Q3 - Q1
```

where:

- **Q1** = First Quartile (25th percentile)
- **Q3** = Third Quartile (75th percentile)

The lower and upper limits are computed as:

```text
Lower Bound = Q1 - 1.5 × IQR
Upper Bound = Q3 + 1.5 × IQR
```

Any observation outside these boundaries is considered an outlier.

### Advantages

- Simple and intuitive.
- No assumption about the data distribution.
- Effective for skewed data.

### Limitations

- Mainly suitable for univariate analysis.
- Performance decreases with highly contaminated datasets.

---

## 2. Median Absolute Deviation (MAD)

Median Absolute Deviation (MAD) is a robust measure of variability that is less affected by extreme values than the standard deviation.

It is calculated as:

```text
MAD = median(|Xi − median(X)|)
```

A modified Z-score is usually computed from MAD, and observations with a score greater than **3.5** are commonly treated as outliers.

### Advantages

- Highly robust against extreme values.
- Works well on non-normal distributions.
- Less sensitive to skewed data.

### Limitations

- Primarily designed for numerical variables.
- Not intended for high-dimensional datasets.

---

## 3. Z-Score

The Z-Score measures how many standard deviations a data point is from the mean.

The formula is:

```text
Z = (X − μ) / σ
```

where:

- **μ** = Mean
- **σ** = Standard Deviation

A common threshold is:

```text
|Z| > 3
```

which indicates a potential outlier.

### Advantages

- Easy to compute and interpret.
- Widely used in statistics.
- Effective for normally distributed data.

### Limitations

- Sensitive to extreme values.
- Assumes approximately Gaussian data.

---

# Machine Learning Methods

Machine learning methods can capture complex relationships between variables and are particularly effective for multivariate datasets.

---

## 1. DBSCAN

DBSCAN (**Density-Based Spatial Clustering of Applications with Noise**) is a density-based clustering algorithm that identifies observations located in low-density regions as **noise (outliers)**.

### Main Parameters

- **eps**: Maximum distance between neighboring points.
- **min_samples**: Minimum number of neighbors required to form a dense region.

### Advantages

- No need to specify the number of clusters.
- Automatically detects noise.
- Can identify clusters with arbitrary shapes.

### Limitations

- Sensitive to parameter selection.
- Less effective on datasets with varying densities.

---

## 2. Local Outlier Factor (LOF)

Local Outlier Factor (LOF) is a density-based anomaly detection algorithm that measures the local density of each observation relative to its neighbors.

Points with significantly lower density than their surrounding neighbors receive higher LOF scores and are identified as outliers.

### Advantages

- Effective at detecting local anomalies.
- Works well on datasets with varying densities.
- No assumption about data distribution.

### Limitations

- Computationally expensive for large datasets.
- Sensitive to the neighborhood parameter.

---

## 3. One-Class SVM

One-Class Support Vector Machine (One-Class SVM) is an unsupervised anomaly detection algorithm that learns the boundary surrounding normal observations.

Any sample lying outside the learned boundary is classified as an anomaly.

Unlike traditional SVM, One-Class SVM is trained only on normal observations.

### Advantages

- Effective in high-dimensional feature spaces.
- Can model complex nonlinear boundaries using kernel functions.
- Suitable when only normal data is available.

### Limitations

- Sensitive to parameter tuning.
- Computationally expensive on large datasets.

---

# Comparison of Methods

| Method | Category | Multivariate | Distribution Assumption | Robustness |
|----------|----------|--------------|--------------------------|------------|
| Box Plot (IQR) | Statistical | ❌ | No | Medium |
| MAD | Statistical | ❌ | No | High |
| Z-Score | Statistical | ❌ | Yes | Low |
| DBSCAN | Machine Learning | ✅ | No | High |
| LOF | Machine Learning | ✅ | No | High |
| One-Class SVM | Machine Learning | ✅ | No | High |

---

# Technologies Used

- Python
- NumPy
- Pandas
- Matplotlib
- Seaborn
- Scikit-learn

---

# Conclusion

Outlier detection is an essential preprocessing step that improves data quality and enhances the performance of machine learning models.

Statistical methods such as **Box Plot (IQR)**, **Median Absolute Deviation (MAD)**, and **Z-Score** are simple, interpretable, and effective for low-dimensional datasets.

Machine learning techniques including **DBSCAN**, **Local Outlier Factor (LOF)**, and **One-Class SVM** are better suited for multivariate and high-dimensional data, where complex relationships between features make statistical methods less effective.

The choice of method depends on the characteristics of the dataset, the dimensionality of the data, and the expected behavior of outliers.
