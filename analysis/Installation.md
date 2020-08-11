---
permalink: /analysis/installation
title: Installation
sort: 4
---

# Installing tra-analysis

## Standard Platforms

For the latest version of tra-analysis, run:

`pip install tra-analysis` 

or

`pip install tra_analysis`

The requirements for tra-analysis should be automatically installed.

## Exotic Platforms (Android)
[Termux](https://termux.com/) is recommended for a linux environemnt on Android. In Termux, the `pkg` command substitutes for the `apt`/`apt-get` commands in most instances. For example installing python can be done by running:

`pkg install python`

and pip can be installed (if it already was not installed) by:

`pkg install pip`

however several of the dependencies can't be installed by simply pip installing them. The methods for installation for each dependencies are below:

- numba: `pip install numba`
- numpy and scipy:\
    - `curl -L https://its-pointless.github.io/setup-pointless-repo.sh | sh`
    - `pkg install numpy`
    - `pkg install scipy`
- scikit-learn: `pip install scikit-learn`
    - if that does not work, please consult [this github thread](https://github.com/termux/termux-packages/issues/1618)
- matplotlib/ `pip install matplotlib`

After the prerequisites are installed, the package can be installed like normal using pip.