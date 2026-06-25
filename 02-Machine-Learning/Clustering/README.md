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
