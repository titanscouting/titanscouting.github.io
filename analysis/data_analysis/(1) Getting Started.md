---
permalink: /analysis/data_analysis/getting-started
title: "Getting Started: Data Analysis"
sort: 2
---

# Prerequisites
Before installing and using data-analysis, make sure that you have installed the folowing prerequisites:
- A common operating system like **Windows** or (*most*) distributions of **Linux**. BSD may work but has not been tested nor is it reccomended.
- [Python](https://www.python.org/) version **3.6** or higher
- [Pip](https://pip.pypa.io/en/stable/) (installation instructions [here](https://pip.pypa.io/en/stable/installing/))

# Installing Requirements

Once navigated to the data-analysis folder run `pip install -r requirements.txt` to install all of the required python libraries.

# Scripts

The data-analysis application is a collection of various scripts and one config file. For users, only the main application `superscript.py` and the config file `config.json` are important. 

To run the data-analysis application, navigate to the data-analysis folder once all requirements have been installed and run `python superscript.py`. If you encounter the error:

`pymongo.errors.ConfigurationError: Empty host (or extra comma in host list).`

don't worry, you may have just not configured the application correctly, but would otherwise work. Refer to [link]() to learn how to configure data-analysis.