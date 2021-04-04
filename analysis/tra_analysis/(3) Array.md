---
permalink: /analysis/tra_analysis/Array
title: Array
sort: 3
---

# tra_analysis.Array()

Array is a container class for np.array, and integrates `np.array.dot()` as a python magic method `__mul__` and `__rmul__`. Other methods should be the same.

## Example Usage
```
from tra_analysis import Array

a = Array([1,2,3,4])
b = Array([-1,-2,-3,4])

a * b
```
returns:
```
2
```