---
permalink: /analysis/tra_analysis/RegressionMetric
title: RegressionMetric
sort: 7
---

# analysis.RegressionMetric()

RegressionMetric is a class containing 3 submodules. The submodules are metrics to measure closeness of a regression model to the intended data. It includes, r<sup>2</sup>, mean squared error (mse), and root mean squared (rms).

# analysis.RegressionMetric(predictions, targets)

The default behavior of calling the class is to return all three metrics. Given a 1D array of the predictions from the model and 1D array of the target values, returns the r<sup>2</sup>, mse, and rms values as a tuple.

## Example Usage
```
from tra_analysis import analysis

predictions = [1.2, 3.4, 0.6, 7.8, 4.3, 8.9]
targets = [0.3, 5.2, 9.8, 1.6, 5.0, 7.6]

analysis.RegressionMetric(predictions, targets)
```
returns:
```
(-1.0380361974309804, 21.551666666666666, 4.642377264577564)
```
(clearly this is a terrible regression)

The other three submodules are local and are only called from within the class.