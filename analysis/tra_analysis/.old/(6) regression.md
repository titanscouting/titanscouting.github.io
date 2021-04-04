---
permalink: /analysis/tra_analysis/Analysis/regression
title: regression
sort: 6
---

# tra_analysis.Analysis.regression(inputs, outputs, args)

Performs a number of specified regressions on a set of 2D data. Given: 
- inputs (x values or independent variable values)
- outputs (y values or dependent variable values)
- args (list of types of regressions)
the function returns a dictionary with keys of regression types and values of regression parameters (coefficients). 

Types of regressions that can be performed are:
- "lin" = linear 
- "log" = logarithmic 
- "exp" = exponential
- "ply" = polynomial
- "sig" = sigmoidal

Note: not all regressions will have resonable results on all datasets.

## Example Usage
```
from tra_analysis import analysis

test_data = [[1.2, 3.4, 0.6, 7.8, 4.3, 8.9], [0.3, 5.2, 9.8, 1.6, 5.0, 7.6]]

analysis.regression(test_data[0], test_data[1], ["lin"])
```
returns:
```
{'lin': '-0.056992116353780986*x+5.165532228810201'}
```