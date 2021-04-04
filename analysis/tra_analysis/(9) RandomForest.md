---
permalink: /analysis/tra_analysis/RandomForest
title: RandomForest
sort: 9
---

# tra_analysis.RandomForest

RandomForest is a class that holds 2 submodules. The submodules are random forest classification and regression models.

Note: After update 3.x, the classness of this module has been removed.

## tra_analysis.RandomForest.random_forest_classifier(self, data, labels, test_size, n_estimators="warn", criterion="gini", max_depth=None, min_samples_split=2, min_samples_leaf=1, min_weight_fraction_leaf=0.0, max_features="auto", max_leaf_nodes=None, min_impurity_decrease=0.0, min_impurity_split=None, bootstrap=True, oob_score=False, n_jobs=None, random_state=None, verbose=0, warm_start=False, class_weight=None)

Uses a random forest model for classification of data. Expects inputs as data and lables. Refer to [sklearn's documentation](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestClassifier.html) for more information on use. 

Given data and labels, it returns a model, confusion matrix (cm), and classification report (cr).

## Example Usage
```
from tra_analysis import RandomForest

data = [[0], [1], [2], [3]]

labels = [0, 0, 1, 1]

RandomForest.random_forest_classifier(data, labels, test_size = 0.25, n_estimators = 2)[0]
RandomForest.random_forest_classifier(data, labels, test_size = 0.25, n_estimators = 2)[1][0]
RandomForest.random_forest_classifier(data, labels, test_size = 0.25, n_estimators = 2)[1][1]
```
outputs: 

[0] (model)
```
RandomForestClassifier(n_estimators=2)
```

[1][0] (cm)
```
[[1]]
```

[1][1] (cr)
```
              precision    recall  f1-score   support

           1       1.00      1.00      1.00         1

    accuracy                           1.00         1
   macro avg       1.00      1.00      1.00         1
weighted avg       1.00      1.00      1.00         1
```

# tra_analysis.RandomForest.random_forest_regressor(self, data, outputs, test_size, n_estimators="warn", criterion="mse", max_depth=None, min_samples_split=2, min_samples_leaf=1, min_weight_fraction_leaf=0.0, max_features="auto", max_leaf_nodes=None, min_impurity_decrease=0.0, min_impurity_split=None, bootstrap=True, oob_score=False, n_jobs=None, random_state=None, verbose=0, warm_start=False)

Uses a random forest model for regression of data. Expects inputs as data and outputs. Refer to [sklearn's documentation](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestRegressor.html) for more information on use. 

Given data and outputs, it returns a model, r<sup>2</sup>, mean squared error (mse), and root mean squared (rms).

## Example Usage
```
from tra_analysis import RandomForest

x = [[1.2], [3.4], [0.6], [7.8], [4.3], [8.9]]
y = [0.3, 5.2, 9.8, 1.6, 5.0, 7.6]

RandomForest().random_forest_regressor(x, y, test_size = 0.25, n_estimators = 2)[0]
RandomForest().random_forest_regressor(x, y, test_size = 0.25, n_estimators = 2)[1][0]
RandomForest().random_forest_regressor(x, y, test_size = 0.25, n_estimators = 2)[1][1]
RandomForest().random_forest_regressor(x, y, test_size = 0.25, n_estimators = 2)[1][2]
```
outputs: 

[0] (model)
```
RandomForestRegressor(n_estimators=2)
```

[1][0] (r<sup>2</sup>)
```
-7.534026465028354
```

[1][1] (mse)
```
22.930000000000007
```

[1][2] (rms)
```
5.367727638395972
```
