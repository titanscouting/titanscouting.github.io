---
permalink: /analysis/tra_analysis/Analysis/z_score
title: z_score
sort: 3
---

# tra_analysis.Analysis.z_score(point, mean, stdev)

Calculates z score of a data point (the associated score of the point on a normalized curve) relative to the rest of the dataset. Requires the point, the mean of the set, and the standard deviation of the set. Outputs the calculated z score as a python numerical.

[Read here](https://www.statisticshowto.com/probability-and-statistics/z-score/) for more information about normal curves and z scores. 

## Example Usage
```
from tra_analysis import analysis

test_data = [1.2, 3.4, 0.6, 7.8, 4.3, 8.9]

mean = analysis.basic_stats(test_data)["mean"]

stdev = analysis.basic_stats(test_data)["standard-deviation"]

test_point = 6.0

analysis.z_score(test_point, mean, stdev)
```
returns:
```
0.5276448530110862
```