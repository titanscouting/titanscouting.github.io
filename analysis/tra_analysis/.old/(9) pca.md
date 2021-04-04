---
permalink: /analysis/tra_analysis/Analysis/pca
title: pca
sort: 9
---

# tra_analysis.Analysis.pca(data, n_components = None, copy = True, whiten = False, svd_solver = "auto", tol = 0.0, iterated_power = "auto", random_state = None)

Performs a principal component analysis (pca) on the data. Refer to [sklearn's documentation](https://scikit-learn.org/stable/modules/generated/sklearn.decomposition.PCA.html) for more information on use.

Given some ndarray and number of components to reduce, returns a reduced array.

## Example Usage
```
from tra_analysis import analysis

x = [[-1, -1], [-2, -1], [-3, -2], [1, 1], [2, 1], [3, 2]]

analysis.pca(x, n_components = 2)
```
returns:
```
array([[ 1.38340578,  0.2935787 ],
       [ 2.22189802, -0.25133484],
       [ 3.6053038 ,  0.04224385],
       [-1.38340578, -0.2935787 ],
       [-2.22189802,  0.25133484],
       [-3.6053038 , -0.04224385]])
```