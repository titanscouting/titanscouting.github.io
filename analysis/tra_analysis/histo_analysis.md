---
permalink: /analysis/tra-analysis/histo_analysis
title: histo_analysis
sort: 4
---

# analysis.histo_analysis(hist_data)

Does analysis on historical (order dependant) data by taking point to point derivatives and calculating mean and standard deviation of derivatives. It is most useful in calculating the volatility of a trend. Takes a 2D array as input and returns the mean and standard deviation of the derivatives. The input must be a =n array of x values on one axis and y values on another. 

## Example Usage
```
from tra_analysis import analysis

test_data = [[1.2, 3.4, 0.6, 7.8, 4.3, 8.9], [0.3, 5.2, 9.8, 1.6, 5.0, 7.6]]

analysis.histo_analysis(test_data)
```
returns:
```
{'mean': -0.19213689691950578, 'deviation': 1.4167111581233176}
```