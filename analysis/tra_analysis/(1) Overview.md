---
permalink: /analysis/tra_analysis/overview
title: Overview
sort: 1
---

# Package Structure

In general the structure of tra-analysis follows the [guidelines](https://docs.python.org/3/tutorial/modules.html#packages) set by python.

Overall package update logs have been moved to the highest level ```__init__.py```.

# Submodule Formatting

## Header

Please adhere to the following header template for each forward facing submodule:

```
# Titan Robotics Team 2022: %SubmoduleName% submodule
# 
# Notes:
#    %SomeNotes%
#
# setup:

__version__ = "%Version%"

__changelog__ = """changelog:
	%Changelog (refer to docs for changelog format)%
"""

__author__ = (
	%Authors%
)

__all__ = [
    %Methods%
]
```