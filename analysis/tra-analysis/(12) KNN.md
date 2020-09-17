---
permalink: /analysis/tra_analysis/KNN
title: KNN
sort: 12
---

# analysis.KNN()

KNN is a class that holds 2 submodules. The submodules are K Nerarest Neighbor classification and regression models.

# analysis.KNN().knn_classifier(data, labels, test_size = 0.3, algorithm='auto', leaf_size=30, metric='minkowski', metric_params=None, n_jobs=None, n_neighbors=5, p=2, weights='uniform')

Using a K Neighbors model for classification of data. Expects inputs as data and lables. Refer to [sklearn's documentation](https://scikit-learn.org/stable/modules/generated/sklearn.neighbors.KNeighborsClassifier.html) for more information on use. Given data and labels, it returns a model, confusion matrix (cm), and classification report (cr).

## Example Usage
```
from tra_analysis import analysis

data = [[0], [1], [2], [3]]

labels = [0, 0, 1, 1]

analysis.KNN().knn_classifier(data, labels, n_neighbors = 2)[0]
analysis.KNN().knn_classifier(data, labels, n_neighbors = 2)[1][0]
analysis.KNN().knn_classifier(data, labels, n_neighbors = 2)[1][1]
```
outputs: 

[0] (model)
```
KNeighborsClassifier(n_neighbors=2)
```

[1][0] (cm)
```
[[0 0]
 [2 0]]
```

[1][1] (cr)
```
              precision    recall  f1-score   support

           0       0.00      0.00      0.00       0.0
           1       0.00      0.00      0.00       2.0

    accuracy                           0.00       2.0
   macro avg       0.00      0.00      0.00       2.0
weighted avg       0.00      0.00      0.00       2.0
```

# analysis.KNN().knn_regressor(self, data, outputs, test_size, n_neighbors = 5, weights = "uniform", algorithm = "auto", leaf_size = 30, p = 2, metric = "minkowski", metric_params = None, n_jobs = None)

Using a K Neighbors model for regression of data. Expects inputs as data and outputs. Refer to [sklearn's documentation](https://scikit-learn.org/stable/modules/generated/sklearn.neighbors.KNeighborsClassifier.html) for more information on use. Given data and outputs, it returns a model, r<sup>2</sup>, mean squared error (mse), and root mean squared (rms).

## Example Usage
```
from tra_analysis import analysis

data = [[0], [1], [2], [3]]

outputs = [0, 0, 1, 1]

analysis.KNN().knn_regressor(data, outputs, n_neighbors = 2)[0]
analysis.KNN().knn_regressor(data, outputs, n_neighbors = 2)[1][0]
analysis.KNN().knn_regressor(data, outputs, n_neighbors = 2)[1][1]
analysis.KNN().knn_regressor(data, outputs, n_neighbors = 2)[1][2]
```
outputs: 

[0] (model)
```
KNeighborsRegressor(n_neighbors=2)
```

[1][0] (r<sup>2</sup>)
```
0.0
```

[1][1] (mse)
```
1.0
```

[1][2] (rms)
```
1.0
```