---
permalink: /analysis/tra_analysis/Analysis/basic_stats
title: basic_analysis
sort: 2
---

# tra_analysis.Analysis.basic_stats(data)

Performs basic statistics tests including:
- mean
- median
- mode
- standard deviation
- variance
- maximum
- minumum

on any flattenable array.

Returns the results as a dictionary with keys of test names and values of test results.

## Example Usage

```
from tra_analysis import analysis

test_data = [1.2, 3.4, 0.6, 7.8, 4.3, 8.9]

analysis.basic_stats(test_data)
```
returns:
```
{'mean': 4.366666666666667, 'median': 3.8499999999999996, 'standard-deviation': 3.095516470998373, 'variance': 9.582222222222223, 'minimum': 0.6, 'maximum': 8.9}
```