---
permalink: /analysis/tra_analysis/CorrelationTest
title: CorrelationTest
sort: 16
---

# analysis.CorrelationTest()

CorrelationTest is a class that holds 7 submodules. The submodules are various types of tests that can be performed on samples of collected data to determine correlation between samples. Usage of each test is identical to the associated scipy source and returns a dictionary of test results.

- [anova_oneway](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.f_oneway.html#scipy.stats.f_oneway) | f value, p value
- [pearson](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.pearsonr.html#scipy.stats.pearsonr) | r value, p value
- [spearman](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.spearmanr.html#scipy.stats.spearmanr) | r value, p value
- [point_biserial](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.pointbiserialr.html#scipy.stats.pointbiserialr) | r value, p value
- [kendall](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.kendalltau.html#scipy.stats.kendalltau) | tau, p value
- [kendall_weighted](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.weightedtau.html#scipy.stats.weightedtau) | tau (weighted), p value
- [mgc](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.multiscale_graphcorr.html#scipy.stats.multiscale_graphcorr) (Multiscale Graph Correlation) | k value, p value, addition results including:
    - 2D representation of the latent geometry of the relationship of results
    - estimated optimal scale as a (x, y) pair
    - null distribution derived from the permuted matrices