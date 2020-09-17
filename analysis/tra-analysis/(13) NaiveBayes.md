---
permalink: /analysis/tra_analysis/NaiveBayes
title: NaiveBayes
sort: 13
---

# analysis.NaiveBayes()

NaiveBayes is a class that holds 4 submodules. The submodules are Naieve Bayes algorithms for classification. There are 4 different "kernels" or methods that can be used in naive bayes classification, they differ in the assumptions thy make regarding the distribution of P(x<sub>i</sub>｜y). Refer to [sklearn's documentation](https://scikit-learn.org/stable/modules/naive_bayes.html) for more information on use.

## Example Usage

All kernels expect the same required arguments and only differ in their optional parameters.