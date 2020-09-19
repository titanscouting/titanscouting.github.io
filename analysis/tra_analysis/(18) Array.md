---
permalink: /analysis/tra_analysis/Array
title: Array
sort: 18
---

# analysis.Array()

Array is a container class for np.array, and integrates `np.array.dot()` as a python magic method `__mul__` and `__rmul__`. Other methods should be the same.

## Example Usage
```
from tra_analysis import analysis

a = analysis.Array([1,2,3,4])
b = analysis.Array([-1,-2,-3,4])
```
returns:
```
-30
```