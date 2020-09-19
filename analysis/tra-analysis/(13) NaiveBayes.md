---
permalink: /analysis/tra_analysis/NaiveBayes
title: NaiveBayes
sort: 13
---

# analysis.NaiveBayes()

NaiveBayes is a class that holds 4 submodules. The submodules are Naieve Bayes algorithms for classification. There are 4 different "kernels" or methods that can be used in naive bayes classification, they differ in the assumptions they make regarding the distribution of P(x<sub>i</sub>｜y). Refer to [sklearn's documentation](https://scikit-learn.org/stable/modules/naive_bayes.html) for more information on use.

Given data and labels, each subclass will return a fitted model given the specified kernel type.

## Example Usage

All kernels expect the same required arguments and only differ in their optional parameters. Usage is identical to [sklearn.naive_bayes.*](https://scikit-learn.org/stable/modules/naive_bayes.html).

```
from tra_analysis import analysis

data = [[0], [1], [2], [3]]

labels = [0, 0, 1, 1]

analysis.NaiveBayes().guassian(data, labels, test_size = 0.25)[0]
analysis.NaiveBayes().guassian(data, labels, test_size = 0.25)[1][0]
analysis.NaiveBayes().guassian(data, labels, test_size = 0.25)[1][1]
```
outputs: 

[0] (model)
```
GaussianNB()
```

[1][0] (cm)
```
[[0, 0],
 [1, 0]]
```

[1][1] (cr)
```
              precision    recall  f1-score   support

           0       0.00      0.00      0.00       0.0
           1       0.00      0.00      0.00       1.0

    accuracy                           0.00       1.0
   macro avg       0.00      0.00      0.00       1.0
weighted avg       0.00      0.00      0.00       1.0
```
