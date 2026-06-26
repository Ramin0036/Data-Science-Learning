



# Clustering Project

## Overview

This project applies and compares two popular clustering algorithms:

- K-Means
- DBSCAN (Density-Based Spatial Clustering of Applications with Noise)

The quality of clustering results is evaluated using the following metrics:

- Silhouette Score
- Davies-Bouldin Index

Clustering is an unsupervised machine learning technique that aims to group similar data points into clusters while separating dissimilar points into different groups.

---

## Algorithms

### 1. K-Means Clustering

K-Means is a centroid-based clustering algorithm that partitions data into **K clusters**. Each cluster is represented by its centroid, which is the mean position of all points within the cluster.

#### How It Works

1. Choose the number of clusters (**K**).
2. Initialize K centroids.
3. Assign each data point to the nearest centroid.
4. Recalculate centroids based on assigned points.
5. Repeat steps 3 and 4 until convergence.

#### Advantages

- Simple and easy to implement.
- Computationally efficient.
- Works well on large datasets.

#### Limitations

- Requires the number of clusters to be specified beforehand.
- Sensitive to outliers and noise.
- Assumes clusters are roughly spherical.

---

### 2. DBSCAN

DBSCAN (Density-Based Spatial Clustering of Applications with Noise) is a density-based clustering algorithm that groups points based on their local density.

Unlike K-Means, DBSCAN does not require specifying the number of clusters in advance and can identify noise points.

#### Main Parameters

##### `eps`

The maximum distance between two points for them to be considered neighbors.

##### `min_samples`

The minimum number of neighboring points required to form a dense region.

#### Types of Points

##### Core Point

A point with at least `min_samples` neighbors within the radius `eps`.

##### Border Point

A point that belongs to a cluster but does not satisfy the core point condition.

##### Noise Point

A point that does not belong to any cluster.

#### Advantages

- No need to specify the number of clusters.
- Can detect outliers and noise.
- Handles arbitrarily shaped clusters effectively.

#### Limitations

- Sensitive to parameter selection (`eps` and `min_samples`).
- Performance may decrease when clusters have varying densities.

---

## Evaluation Metrics

### Silhouette Score

The Silhouette Score measures how similar a data point is to its own cluster compared to other clusters.

For each sample:

- **a** = Mean distance to points within the same cluster.
- **b** = Mean distance to points in the nearest neighboring cluster.

The score is calculated as:

\[
S = \frac{b-a}{\max(a,b)}
\]

#### Range

```
-1 ≤ Silhouette Score ≤ 1
```

#### Interpretation

| Score | Interpretation |
|---------|---------------|
| Close to 1 | Well-clustered samples |
| Around 0 | Overlapping clusters |
| Less than 0 | Possible misclassification |

#### Conclusion

Higher Silhouette Scores indicate better clustering performance.

---

### Davies-Bouldin Index

The Davies-Bouldin Index (DBI) evaluates clustering quality by measuring cluster compactness and separation.

It considers:

- Intra-cluster similarity (compactness)
- Inter-cluster separation (distance between clusters)

The general formula is:

\[
DBI = \frac{1}{N}
\sum_{i=1}^{N}
\max_{j \neq i}
\left(
\frac{S_i + S_j}{M_{ij}}
\right)
\]

Where:

- \(S_i\) = Average distance of points in cluster i from its centroid.
- \(S_j\) = Average distance of points in cluster j from its centroid.
- \(M_{ij}\) = Distance between the centroids of clusters i and j.

#### Range

```
DBI ≥ 0
```

#### Interpretation

| DBI Value | Interpretation |
|------------|---------------|
| Close to 0 | Excellent clustering |
| Low value | Compact and well-separated clusters |
| High value | Significant cluster overlap |

#### Conclusion

Lower Davies-Bouldin Index values indicate better clustering performance.

---

## Metrics Comparison

| Metric | Optimal Value |
|----------|---------------|
| Silhouette Score | Higher is better |
| Davies-Bouldin Index | Lower is better |

---

## Results

The clustering performance of K-Means and DBSCAN can be compared using:

- Silhouette Score
- Davies-Bouldin Index

A better clustering model typically achieves:

- Higher Silhouette Score
- Lower Davies-Bouldin Index

---

## Technologies Used

- Python
- NumPy
- Pandas
- Matplotlib
- Scikit-learn

---

## References

- Scikit-learn Documentation
- K-Means Clustering
- DBSCAN Clustering
- Silhouette Analysis
- Davies-Bouldin Index

---

## Author

Developed for clustering analysis and evaluation using K-Means and DBSCAN algorithms.
این نسخه مستقیماً قابل قرار دادن در فایل README.md گیت‌هاب است و فرمت Markdown آن کاملاً با GitHub سازگار است.


TypeError                                 Traceback (most recent call last)
Cell In[3], line 1
----> 1 plt.imshow(org_image)

File c:\Users\Ramin\AppData\Local\Programs\Python\Python310\lib\site-packages\matplotlib\pyplot.py:3601, in imshow(X, cmap, norm, aspect, interpolation, alpha, vmin, vmax, colorizer, origin, extent, interpolation_stage, filternorm, filterrad, resample, url, data, **kwargs)
   3579 @_copy_docstring_and_deprecators(Axes.imshow)
   3580 def imshow(
   3581     X: ArrayLike | PIL.Image.Image,
   (...)
   3599     **kwargs,
   3600 ) -> AxesImage:
-> 3601     __ret = gca().imshow(
   3602         X,
   3603         cmap=cmap,
   3604         norm=norm,
   3605         aspect=aspect,
   3606         interpolation=interpolation,
   3607         alpha=alpha,
   3608         vmin=vmin,
   3609         vmax=vmax,
   3610         colorizer=colorizer,
   3611         origin=origin,
   3612         extent=extent,
   3613         interpolation_stage=interpolation_stage,
...
    649                     f"converted to float")
    650 if A.ndim == 3 and A.shape[-1] == 1:
    651     A = A.squeeze(-1)  # If just (M, N, 1), assume scalar and apply colormap.

TypeError: Image data of dtype object cannot be converted to float
Output is truncated. View as a scrollable element or open in a text editor. Adjust cell output settings...مشکل چیه؟

این خطا:

TypeError: Image data of dtype object cannot be converted to float
یعنی متغیر org_image یک آرایه تصویری معتبر نیست و نوع داده‌ی آن object است، در حالی که plt.imshow() انتظار دارد داده‌ها از نوع عددی باشند (uint8, float32, float64 و ...).

اول نوع متغیر را بررسی کن
print(type(org_image))
و اگر numpy array است:

print(org_image.dtype)
print(org_image.shape)
حالت 1: تصویر را با OpenCV اشتباه نخوانده‌ای
اگر از OpenCV استفاده کرده‌ای:

import cv2

org_image = cv2.imread("image.jpg")
اگر مسیر اشتباه باشد:

print(org_image)
خروجی:

None
خواهد بود.

در این حالت:

plt.imshow(org_image)
خطا می‌دهد.

راه حل
org_image = cv2.imread("image.jpg")

if org_image is None:
    print("Image not found!")
حالت 2: آرایه object ساخته شده
مثلا:

org_image = np.array([img1, img2])
در حالی که اندازه تصاویر متفاوت است.

نتیجه:

dtype=object
می‌شود.

بررسی:

print(org_image.dtype)
اگر دیدی:

object
باید تصویر مورد نظر را جداگانه نمایش بدهی:

plt.imshow(img1)
یا ابعاد همه تصاویر را یکسان کنی.

حالت 3: مسیر تصویر را مستقیم به imshow داده‌ای
اشتباه:

org_image = "cat.jpg"
plt.imshow(org_image)
در اینجا رشته (string) به عنوان تصویر ارسال شده و خطا می‌دهد.

درست:

from PIL import Image

org_image = Image.open("cat.jpg")
plt.imshow(org_image)
یا:

import matplotlib.image as mpimg

org_image = mpimg.imread("cat.jpg")
plt.imshow(org_image)
حالت 4: DataFrame یا Series را به imshow داده‌ای
مثلا:

org_image = df["image"]
plt.imshow(org_image)
اگر ستون شامل مسیر تصاویر یا اشیاء باشد، dtype برابر object می‌شود.

بررسی:

print(type(org_image))
برای تشخیص دقیق
این سه خط را اجرا کن و خروجی را بفرست:

print(type(org_image))

if hasattr(org_image, "dtype"):
    print(org_image.dtype)

if hasattr(org_image, "shape"):
    print(org_image.shape)
و همچنین کدی که org_image را ساخته یا خوانده است را بفرست تا دقیقاً مشخص شود مشکل از کجاست.


seabornدستور نصب برای پایتون

برای نصب Seaborn در پایتون، در ترمینال یا CMD این دستور را اجرا کنید:

pip install seaborn
اگر چند نسخه پایتون دارید:

python -m pip install seaborn
یا:

python3 -m pip install seaborn
برای محیط Jupyter Notebook:

!pip install seaborn
برای اطمینان از نصب صحیح:

import seaborn as sns

print(sns.__version__)
اگر خطای نصب دریافت کردید، ابتدا pip را به‌روزرسانی کنید:

python -m pip install --upgrade pip
سپس دوباره:

pip install seaborn
اگر از Anaconda استفاده می‌کنید:

conda install seaborn

حالا یک ردیمی برای گیت هابم میخام که شامل outlier و توضیحش باشه و روش های آماری برای پیدا کردن outlier ها که شامل boxplot,mad,z_score رو با توضیحات بیاری و روش های دسته دیگر که روش های کلاسیک ماشین لرنینگی هستند شامل DBScan,LOF,Oneclass svm , یکی از روش های ماشین لرنینگ مثل SVM رو بیاری با توضیحات.

مطمئناً. متن زیر یک README.md حرفه‌ای و مناسب GitHub است که علاوه بر معرفی پروژه، روش‌های آماری و یادگیری ماشین برای تشخیص داده‌های پرت (Outlier Detection) را توضیح می‌دهد.

Outlier Detection using Statistical and Machine Learning Methods
Overview
Outlier detection is an essential step in data preprocessing and exploratory data analysis. Outliers are observations that significantly differ from the majority of the dataset and may result from measurement errors, data corruption, or genuinely rare events.

Detecting and handling outliers can improve model performance, increase prediction accuracy, and produce more reliable analytical results.

This project explores both statistical and machine learning approaches for outlier detection and compares their behavior on different datasets.

Statistical Methods
Statistical methods identify outliers based on the distribution of the data. These approaches are generally simple, interpretable, and computationally efficient.

1. Box Plot (Interquartile Range - IQR)
The Box Plot method identifies outliers using the Interquartile Range (IQR).

The IQR is calculated as:

IQR = Q3 - Q1
where:

Q1 = First Quartile (25th percentile)

Q3 = Third Quartile (75th percentile)

A data point is considered an outlier if:

Lower Bound = Q1 - 1.5 × IQR
Upper Bound = Q3 + 1.5 × IQR
Advantages
Very simple and intuitive.

Does not require assumptions about data distribution.

Effective for skewed distributions.

Limitations
Works primarily on univariate data.

Sensitive when the dataset contains many extreme values.

2. Median Absolute Deviation (MAD)
Median Absolute Deviation (MAD) is a robust statistical measure of variability.

It is calculated as:

MAD = median(|Xi - median(X)|)
Unlike standard deviation, MAD is much less affected by extreme values.

An observation is typically considered an outlier when its modified Z-score exceeds a predefined threshold (commonly 3.5).

Advantages
Highly robust to outliers.

Performs well on non-normal data.

Less influenced by skewed distributions.

Limitations
Mainly suitable for numerical variables.

Not designed for high-dimensional datasets.

3. Z-Score
The Z-Score measures how many standard deviations a data point is away from the mean.

The formula is:

Z = (X - μ) / σ
where:

μ = Mean

σ = Standard Deviation

A common threshold is:

|Z| > 3
which indicates a potential outlier.

Advantages
Easy to compute.

Widely used in statistical analysis.

Effective when data follows a normal distribution.

Limitations
Sensitive to extreme values.

Assumes approximately Gaussian data.

Machine Learning Methods
Unlike statistical methods, machine learning approaches can capture complex relationships between variables and are particularly useful for multivariate datasets.

1. DBSCAN
DBSCAN (Density-Based Spatial Clustering of Applications with Noise) is a density-based clustering algorithm.

Instead of assigning every point to a cluster, DBSCAN labels points that belong to low-density regions as noise (outliers).

Main Parameters
eps: Maximum neighborhood distance.

min_samples: Minimum number of neighboring points required to form a dense region.

Advantages
No need to specify the number of clusters.

Automatically detects noise.

Works well for arbitrarily shaped clusters.

Limitations
Sensitive to parameter selection.

Less effective when clusters have varying densities.

2. Local Outlier Factor (LOF)
Local Outlier Factor (LOF) is a density-based anomaly detection algorithm.

Instead of considering only the global density, LOF compares the local density of each point with that of its neighbors.

Points with significantly lower local density receive higher LOF scores and are considered anomalies.

Advantages
Detects local anomalies effectively.

Works well on datasets with varying densities.

No assumption about data distribution.

Limitations
Computationally expensive for large datasets.

Sensitive to the choice of neighborhood size.

3. One-Class SVM
One-Class Support Vector Machine (One-Class SVM) is an unsupervised anomaly detection algorithm.

It learns the boundary surrounding normal observations and classifies points lying outside this boundary as anomalies.

Unlike traditional SVM, it requires training only on normal data.

Advantages
Effective in high-dimensional spaces.

Can model complex decision boundaries using kernels.

Suitable when only normal samples are available.

Limitations
Sensitive to parameter tuning.

Computationally expensive for large datasets.

4. Isolation Forest
Isolation Forest is one of the most popular machine learning algorithms for anomaly detection.

Instead of profiling normal observations, it isolates anomalies by recursively partitioning the data using random decision trees.

Since anomalies are few and different, they are isolated with fewer splits.

Advantages
Fast and scalable.

Performs well on high-dimensional datasets.

Requires little parameter tuning.

Efficient for large datasets.

Limitations
Performance may decrease with highly overlapping distributions.

Less interpretable than statistical methods.

Comparison of Methods
Method	Category	Suitable for Multivariate Data	Robust to Outliers	Distribution Assumption
Box Plot (IQR)	Statistical	❌	Moderate	No
MAD	Statistical	❌	Excellent	No
Z-Score	Statistical	❌	Low	Yes
DBSCAN	Machine Learning	✅	High	No
LOF	Machine Learning	✅	High	No
One-Class SVM	Machine Learning	✅	High	No
Isolation Forest	Machine Learning	✅	Excellent	No
Technologies Used
Python

NumPy

Pandas

Matplotlib

Seaborn

Scikit-learn

Conclusion
Outlier detection is a critical preprocessing step that improves data quality and machine learning performance.

Statistical methods such as Box Plot, MAD, and Z-Score are simple, interpretable, and effective for low-dimensional datasets.

Machine learning methods including DBSCAN, Local Outlier Factor (LOF), One-Class SVM, and Isolation Forest are more suitable for complex and high-dimensional data, where traditional statistical techniques may fail.

Selecting the appropriate method depends on the data distribution, dimensionality, and the characteristics of the anomalies being detected.


isolation forest  رو پاک کن و بقیه رو با فرمت ریدمی گیت هاب بده بهم.

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

