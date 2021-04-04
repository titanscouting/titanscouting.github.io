---
permalink: /analysis/tra_analysis/Analysis
title: Overview
sort: 2
---

# tra_analysis.Analysis

The primary imported module. Contains the most basic data analysis tools along with import links for other `tra_analysis` submodules. The documentation for the submodule specific tools are contained here, the linked imports are documented in their own articles.

Note: After update 3.x, the module was renamed to `Analysis` from `analysis`, however the old import name can still be used but support will be removed in future updates. 

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

# tra_analysis.Analysis.z_normalize(array, *args)

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

# tra_analysis.Analysis.histo_analysis(hist_data)

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

# tra_analysis.Analysis.Metric

Metric is a module containing 3 submodules. The submodules are match performance rating systems including elo, glicko2, and trueskill.

Note: not to be confused with metrics.
After update 3.x, the classness of this module has been removed.

# tra_analysis.Analysis.Metric.elo(starting_score, opposing_score, observed, N, K)

The [elo]((https://en.wikipedia.org/wiki/Elo_rating_system)) ranking system was developed primarily to rank chess players objectively using a score system. Its use can be extended to any zero sum game.

Given a previous elo score, an opposing elo score, and the results of a match (an array of 2 values, the first reflecting the points earned by the first player and the second reflecting the score of the second player), returns the new elo score. 

N and K are constants. By default N = 400 and K = 24.

## Example Usage
```
from tra_analysis import analysis

previous_elo = 1524
oppoonent_elo = 1586

N = 400
K = 24

observed = [1, 0] # in this case, the 1st player (the one being evaluated) won, and the opponent lost

analysis.Metric().elo(previous_elo, oppoonent_elo, observed, N, K)
```
returns:
```
1538.118959324716
```

# tra_analysis.Analysis.Metric.glicko2(starting_score, starting_rd, starting_vol, opposing_score, opposing_rd, observations)

The [glicko2](http://www.glicko.net/glicko/glicko2.pdf) rating system was designed to improve on the elo system by introducing a rating deviation (rd) and rating volitility (vol) in addition to the rating. It can also calculate scores for several consecutive games and expects opposing_score and opposing_rd to be lists

Given a previous glicko2 rating (score, rd and vol), an opposing glicko2 rating (rating and rd), and the results of a match (an array of 2 values, the first reflecting the points earned by the first player and the second reflecting the score of the second player), returns a tuple of (new score, new rd, new vol)


## Example Usage
```
from tra_analysis import analysis

previous_rating = 1650
previous_rd = 151.52
previous_vol = 0.05999

opponent_ratings = [1690, 1450]
opponent_rds = [162.32, 125.3]

observed = [0, 1] # in this case, the player being evaluated lost against their first opponent, and won against their second

analysis.Metric().glicko2(previous_rating, previous_rd, previous_vol, opponent_ratings, opponent_rds, observed)
```
returns:
```
(1633.1498393809143, 134.50703588188637, 0.059986396179992955)
```

# tra_analysis.Analysis.Metric.trueskill(teams_data, observations)

The [glicko2](http://www.glicko.net/glicko/glicko2.pdf) rating system was developed by microsoft to rank players in games that involved more than 2 players per game. 

Given some teams_data (array of tuples of ratings) and the observed outcome of the game, returns new ratings.

Example teams_data:

```
[
    [rating1, rating2, rating3] # team 1
    [rating4, rating5, rating6] # team 2
]
```

where the ratings are tuples of mu and sigma values (mu, sigma). Default values are mu = 25, sigma = 25/3

With trueskill, the observations can be raw points, as it does not require the game played to be zero summed.

## Example Usage
```
from tra_analysis import analysis

rating1 = (24.3, 8.2)
rating2 = (26.4, 7.5)
rating3 = (25, 8.3)
rating4 = (22.5, 7.75)

teams_data = [
    [rating1, rating2],
    [rating3, rating4],
]

observed = [0, 1] # in this case, the first team lost and the second team won

analysis.Metric().trueskill(teams_data, observed)
```
returns:
```
[
    (tra_analysis.metrics.trueskill.Rating(mu=27.010, sigma=7.660), tra_analysis.metrics.trueskill.Rating(mu=28.667, sigma=7.090)), 
    (tra_analysis.metrics.trueskill.Rating(mu=22.223, sigma=7.740), tra_analysis.metrics.trueskill.Rating(mu=20.079, sigma=7.296))
]
```

# tra_analysis.Analysis.kmeans(data, n_clusters=8, init="k-means++", n_init=10, max_iter=300, tol=0.0001, precompute_distances="auto", verbose=0, random_state=None, copy_x=True, n_jobs=None, algorithm="auto")

Performs a kmeans clusteriung analysis on some provided data. Refer to [sklearn's documentation](https://scikit-learn.org/stable/modules/generated/sklearn.cluster.KMeans.html) for more information on use.

Given nd array of points, returns centers of clusters and array of classifications based on clusters.

## Example Usage
```
from tra_analysis import analysis

x = [[1, 2], [1, 4], [1, 0], [10, 2], [10, 4], [10, 0]]

analysis.kmeans(x, n_clusters = 2)
```
returns:
```
(array([[ 1.,  2.], [10.,  2.]]), array([0, 0, 0, 1, 1, 1], dtype=int32))
```

# tra_analysis.Analysis.pca(data, n_components = None, copy = True, whiten = False, svd_solver = "auto", tol = 0.0, iterated_power = "auto", random_state = None)

Performs a principal component analysis (pca) on the data. Refer to [sklearn's documentation](https://scikit-learn.org/stable/modules/generated/sklearn.decomposition.PCA.html) for more information on use.

Given some ndarray and number of components to reduce, returns a reduced array.

## Example Usage
```
from tra_analysis import analysis

x = [[-1, -1], [-2, -1], [-3, -2], [1, 1], [2, 1], [3, 2]]

analysis.pca(x, n_components = 2)
```
returns:
```
array([[ 1.38340578,  0.2935787 ],
       [ 2.22189802, -0.25133484],
       [ 3.6053038 ,  0.04224385],
       [-1.38340578, -0.2935787 ],
       [-2.22189802,  0.25133484],
       [-3.6053038 , -0.04224385]])
```

# tra_analysis.Analysis.decisiontree(data, labels, test_size = 0.3, criterion = "gini", splitter = "default", max_depth = None)

Creates a decision tree classifier given data input and associated labels. Refer to [sklearn's documentation](https://scikit-learn.org/stable/modules/tree.html) for more information on use.