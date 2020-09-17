---
permalink: /analysis/tra_analysis/ClassificationMetric
title: RegressionMetric
sort: 8
---

# analysis.ClassificationMetric()

RegressionMetric is a class containing 2 submodules. The submodules are metrics to measure the accuracy of a classification model to the data. It includes generating a confusion matrix (cm) and a classification report (cr).

# analysis.ClassificationMetric(predictions, targets)

The default behavior of calling the class is to return all 2 metrics. Given a 1D array of the predictions from the model and 1D array of the target values, cm and the cr.

## Example Usage
```
from tra_analysis import analysis
predictions = [0, 0, 2, 3, 1, 1, 3, 3, 1, 2, 3, 0, 1, 3, 2, 3]
targets = [0, 1, 2, 3, 0, 1, 2, 3, 0, 1, 2, 3, 0, 1, 2, 3]

metric = analysis.ClassificationMetric(predictions, targets)
print(metric[0])
print(metric[1])
```
outputs:
```
[[1 3 0 0]
 [1 1 1 1]
 [0 0 2 2]
 [1 0 0 3]]
```
```
              precision    recall  f1-score   support

           0       0.33      0.25      0.29         4
           1       0.25      0.25      0.25         4
           2       0.67      0.50      0.57         4
           3       0.50      0.75      0.60         4

    accuracy                           0.44        16
   macro avg       0.44      0.44      0.43        16
weighted avg       0.44      0.44      0.43        16
```

The other 2 submodules are local and are only called from within the class.