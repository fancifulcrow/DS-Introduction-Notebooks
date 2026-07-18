# K-Means Clustering

## Introduction

K-Means is an unsupervised machine learning algorithm used for clustering data into *K* groups. It is widely used for pattern recognition, image segmentation, and anomaly detection.

**NOTE:** K-Means Clustering assumes that clusters are spherical and of similar sizes, which means it may struggle with non-spherical cluster shapes or clusters of varying densities.

## Objective Function

The K-Means algorithm aims to minimize the following objective function:

$$ J = \sum_{i=1}^{K} \sum_{x \in C_i} ||x - \mu_i||^2 $$

Where:
- $J$ is the total within-cluster sum of squares
- $K$ is the number of clusters
- $C_i$ represents the $i$-th cluster
- $x$ is a data point in the cluster
- $\mu_i$ is the centroid (mean) of the $i$-th cluster
- $||x - \mu_i||^2$ is the squared Euclidean distance

## Algorithm

**Step 1:** Calculate the number of K (Clusters).

**Step 2:** Randomly select K data points as cluster center (centroid).

**Step 3:** Using the Euclidean distance formula measure the distance between each data point and each cluster center.
$$
\text{Distance} = \sqrt{(x_2 - x_1)^2 + (y_2 - y_1)^2}
$$

**Step 4:** Assign each data point to that cluster whose center is nearest to that data point.

**Step 5:** Re-compute the center of newly formed clusters. The center of a cluster is computed by taking the mean of all the data points contained in that cluster.

**Step 6:** Keep repeating the procedure from Step 3 to Step 5 until any of the following stopping criteria is met:

- If data points fall in the same cluster
- Reached maximum of iteration
- The newly formed cluster does not change in center points
