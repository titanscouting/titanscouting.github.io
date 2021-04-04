---
permalink: /analysis/tra_analysis/SVM
title: SVM
sort: 13
---

# tra_analysis.SVM

SVM is a class that holds 3 submodules and several subclasses. There are 3 sublasses that contains different types of Support Vector Machine (SVM) kernels. The kernels can be used for regression or classification. The submodules include 1 to fit the model to provided data and 2 to evaluate classification or regression performance of the model. Refer to [sklearn's documentation](https://scikit-learn.org/stable/modules/svm.html) for more information on use.

The fit function will return a fitted model given data and labels.

Note: After update 3.x, the classness of this module has been removed.

## Example Usage

```
from tra_analysis import SVM

data = [[0], [1], [2], [3]]

labels = [0, 1, 2, 3]

svm = SVM.PrebuiltKernel.Linear()

svm.fit(data, labels)
```
returns:
```
SVC(kernel='linear')
```