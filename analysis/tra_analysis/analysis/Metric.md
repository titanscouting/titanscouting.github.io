---
permalink: /analysis/tra-analysis/analysis/Metric
title: Metric
sort: 6
---

# analysis.Metric()

Metric is a class containing 3 submodules. The submodules are match performance rating systems including elo, glicko2, and trueskill.

Note: not to be confused with metrics.

# analysis.Metric().elo(starting_score, opposing_score, observed, N, K)

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

# analysis.Metric().glicko2(starting_score, starting_rd, starting_vol, opposing_score, opposing_rd, observations)

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

# analysis.Metric().trueskill(teams_data, observations)

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