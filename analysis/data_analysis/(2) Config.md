---
permalink: /analysis/data_analysis/config
title: "Configuring Data Analysis"
sort: 3
---

# Location

The configuration file for data-analysis is called `config.json` and is located under the data-analysis folder 

# Structure

The structure of `config.json` is a standard [json file](https://www.json.org/json-en.html). The structure is very similar to the python dictionary object. The config is composed of many key-value pairs, with strings as keys and values of either some value (string, number, boolean) or more string value pairs.

# Important Values

- `"team"` key: this determines which team you are performing data analysis on. Set this for your own team.
- `"competition"` key: this determines which competition you are performing on. Set this to [TBA](https://www.thebluealliance.com/) or FRC's official designation (ie. 2020ilch).
- `"keys"` key: this contains 2 sub key-value pairs.
    - `"database"` key: this is the access key to your team's MongoDB. It should start with `"mongodb+srv://"`.
    - `"tba"` key: this is your key to te TBA API. You can get one with TBA at their website.
- `"statistics"` key: contains 3 sub key-value pairs that are used to configure the tests performed on collected data. Only 2 shoulc be changed between seasons.
    - `"match"` key: this key determines what tests are run on which collected variables from scouted data. It contains some number of key value pairs, where the keys are the names of each variable as shown in the database (ie. `"balls-sorted"`) and the value should be an array (list) of tests to be run (ie `"regression_linear"`)
    - `"pit"` key: this key describes which variables to run pit analysis on. The values are some number of key-value pairs with keys of the name of variables (ie. `"balls-sorted"`) and values of `True` or `False` to indicate whether the pit analysis is run on that variable.
# Less Important Values
- `"max-threads"` key: this key determines the number of threads that the analysis engine can use to run the tests. By default it is 0.5, meaning 1/2 the number of cores avaliable. Acceptable values include (in set notation) with max being the number of maximum threads avaliable:
    - n in [1, max] | number of cores used = n, must be an integer
    - n in (0, 1) | decimal portion (percentage) of maximum cores used (0.5 = 50% * max)
    - n = 0 | use all avaliable threads (threads used = max)
    - n in (-max, 0) | use all but n threads, must be an integer (ie, -1 means use all but one thread)
- `"statistics"."metric"` key: these contain the constant values for the metric tests, seperated by k-v pairs of each metric, and then k-v pairs of each value.