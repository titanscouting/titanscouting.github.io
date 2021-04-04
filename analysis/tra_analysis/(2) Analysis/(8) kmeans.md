---
permalink: /analysis/tra_analysis/Analysis/kmeans
title: kmeans
sort: 8
---

# Analysis.kmeans(data, n_clusters=8, init="k-means++", n_init=10, max_iter=300, tol=0.0001, precompute_distances="auto", verbose=0, random_state=None, copy_x=True, n_jobs=None, algorithm="auto")

Performs a kmeans clusteriung analysis on some provided data. Refer to [sklearn's documentation](https://scikit-learn.org/stable/modules/generated/sklearn.cluster.KMeans.html) for more information on use.

Given nd array of points, returns centers of clusters and array of classifications based on clusters.

## Example Usage
```
from tra_analysis import analysis

x = [[1, 2], [1, 4], [1, 0], [10, 2], [10, 4], [10, 0]]

analysis.kmeans(x, n_clusters = 2)
```
returns:
```
(array([[ 1.,  2.], [10.,  2.]]), array([0, 0, 0, 1, 1, 1], dtype=int32))
```