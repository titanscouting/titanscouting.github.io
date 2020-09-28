---
permalink: /analysis/general/overview
title: Analysis Overview
sort: 1
---

# Overview

## tra-analysis

`tra-analysis` is a higher level package for data processing and analysis. It is a python library that combines popular data science tools like numpy, scipy, and sklearn along with other tools to create an easy-to-use data analysis engine. tra-analysis includes analysis in all ranges of complexity from basic statistics like mean, median, mode to complex kernel based classifiers and allows user to more quickly deploy these algorithms. The package also includes performance metrics for score based applications including elo, glicko2, and trueskill ranking systems.

At the core of the tra-analysis package is the modularity of each analytical tool. The package encapsulates the setup code for the included data science tools. For example, there are many packages that allow users to generate many different types of regressions. With the tra-analysis package, one function can be called to generate many regressions and sort them by accuracy.

## data-analysis

To facilitate data analysis of collected scouting data in a user firendly tool, we created the data-analysis application. At its core it uses the tra-analysis package to conduct any number of user selected tests on data collected from the TRA scouting app. It uploads these tests back to MongoDB where it can be viewed from the app at any time.  

The data-analysis application also uses the TRA API to interface with MongoDB and uses the TBA API to collect additional data (match win/loss).

The application can be configured with a configuration tool or by editing the config.json directly.

//to finish later