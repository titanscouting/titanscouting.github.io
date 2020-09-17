---
permalink: /analysis/general/overview
title: Analysis Overview
sort: 1
---

# Overview 

`tra-analysis` is a higher level package for data processing and analysis. It is a python library that combines popular data science tools like numpy, scipy, and sklearn along with other tools to create an easy-to-use data analysis engine. tra-analysis includes analysis in all ranges of complexity from basic statistics like mean, median, mode to complex kernel based classifiers and allows user to more quickly deploy these algorithms. The package also includes performance metrics for score based applications including elo, glicko2, and trueskill ranking systems.

At the core of the tra-analysis package is the modularity of each analytical tool. The package encapsulates the setup code for the included data science tools. For example, there are many packages that allow users to generate many different types of regressions. With the tra-analysis package, one function can be called to generate many regressions and sort them by accuracy.

To facilitate data analysis of collected scouting data, tra-analysis also interfaces with the `data-analysis` submodule to pull data from a MongoDB database, perform calculations, and then return those calculations back to MongoDB. In the future, the data-analysis submodule will interace with the TRA API to centralize data retrieval and submission.

//to finish later