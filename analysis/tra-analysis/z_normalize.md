---
permalink: /analysis/tra-analysis/z_normalize
title: z_normalize
sort: 3
---

# analysis.z_normalize(array, *args)

Normalizes an axis of an array by fitting it to a normal curve. The function takes in some array (n >= 1) and an option list of axes to normalize against (if no axes are provided then no normalization occurs). Returns a normalized array of the same size. 

## Example Usage


### In this case, the data is normalized along the 0th axis:
```
from tra_analysis import analysis

test_data = [[1.2, 3.4, 0.6, 7.8, 4.3, 8.9], [0.3, 5.2, 9.8, 1.6, 5.0, 7.6]]

analysis.z_normalize(test_point, 0)
```
returns:
```
array([[0.9701425 , 0.54724936, 0.06111006, 0.9796027 , 0.65203927,0.76046158],
[0.24253563, 0.83696961, 0.99813103, 0.20094414, 0.7581852 ,0.64938292]])
```

### In this case, the data is normalized along the 1st axis:
```
from tra_analysis import analysis

test_data = [[1.2, 3.4, 0.6, 7.8, 4.3, 8.9], [0.3, 5.2, 9.8, 1.6, 5.0, 7.6]]

analysis.z_normalize(test_point, 1)
```
returns:
```
array([[0.09152575, 0.25932297, 0.04576288, 0.59491739, 0.32796728, 0.678816],
[0.0207768 , 0.36013118, 0.67870877, 0.1108096 , 0.34627998, 0.52634558]])
```