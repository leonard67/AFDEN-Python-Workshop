# Module 2: Handling Data and Descriptive Analysis

[Back to main syllabus](../README.md)

`pandas` is the most useful Python library for data analysis in AccFin research. In this module, you will learn how to use `pandas` to handle data in tabular form. We will cover the fundamental operations needed to load data, explore it, clean it, and prepare it for further analysis, then move on to visualizing it with `matplotlib` and `seaborn`. By the end, you'll have the skills to manage real-world datasets and replicate two seminal papers.

## 2.1. Handling Data with `pandas`

`pandas` is the most useful Python library for data analysis in our research. In the second module, you will learn how to use `pandas` to handle data in tabular form. We will cover the fundamental operations needed to load data, explore it, clean it, and prepare it for further analysis. By the end, you’ll have the skills to manage real-world datasets and apply `pandas` to replicate a saminal paper.

**Prerequisite reading**

- Sloan, R. G. 1996. Do stock prices fully reflect information in accruals and cash flows about future earnings?. *The Accounting Review* 71(3): 289-315. ([link](https://www.jstor.org/stable/248290))

**Learning Outcomes**

By completing this session, you will be able to:

- Create and explore *Series* and *DataFrames*, the two core data structures in `pandas`.
- Import and export datasets from common formats such as CSV and Stata.
- Inspect and summarize data using built-in functions.
- Select, filter, and slice data to focus on what matters, including boolean indexing and `.query()`.
- Clean and transform datasets by handling missing values, renaming columns, changing data types, and winsorizing/truncating outliers.
- Perform basic data analysis with sorting, grouping, and simple aggregations, including `groupby` transformations and `.shift()`.
- Append and merge datasets (one-to-one, one-to-many, and many-to-many merges), including linking Compustat to CRSP via the CCM link table.
- Integrate `pandas` workflows into Python projects replicating seminal academic papers.

Our class is based on [2-1-Pandas.ipynb](2-1_Pandas.ipynb).

### 2.1e-1. Exercise: Replicating Stata's `winsor2`

A homework exercise embedded in the `pandas` session: write a `winsorize_by_group()` function that replicates Stata's `winsor2` command, winsorizing or truncating variables at a chosen percentile, optionally within groups.

Our class is based on [2-1e-1-winsor2.ipynb](2-1e-1_winsor2.ipynb).

### 2.1e-2. Exercise: Replicating Sloan (1996)

This exercise replicates a simplified version of the seminal study by [Sloan (1996)](https://www.jstor.org/stable/248290), one of the most cited papers in accounting and finance research on the *accrual anomaly*. Using the `pandas` skills from 2.1, you construct accrual, cash-flow, and earnings variables from a Compustat/CRSP-style panel, form annual accrual-decile portfolios, and plot the hedge-portfolio returns, similar to Table 6 and Figure 2 of the paper.

Our class is based on [2-1e-2-Replicating_Sloan_1996-Final.ipynb](2-1e-2-Replicating_Sloan_1996-Final.ipynb).

## 2.2. Data Visualization

Data visualization is a critical skill in data analytics, enabling researchers to transform raw data into clear, compelling insights. This session introduces students to two of the most widely used Python libraries for visualization — `matplotlib` and `seaborn`. Students will learn how to create, customize, and interpret a range of plots, from simple line and bar charts to more advanced statistical graphics that are commonly used in AccFin research. By emphasizing both the technical aspects of coding and the principles of effective visual communication, this class equips students to present data in ways that are accurate, insightful, and persuasive for business and research contexts.

**Prerequisite reading**

- Kothari, S. P., B. Schonberger, C. Wasley, and J. Xiao (2025). The first half-century of empirical capital markets research in accounting in pictures. *Review of Accounting Studies* 30: 3111-3176. ([link](https://doi.org/10.1007/s11142-025-09887-3))

**Learning Outcomes**

By completing this session, you will be able to:

- Apply `matplotlib` and `seaborn` to construct foundational plots (line, bar, histogram, scatter, KDE, boxplot, violin, ECDF, Q-Q) and customize elements such as axes, labels, legends, colors, and styles.
- Enhance clarity and impact of visualizations through effective use of color, scaling, and annotation.

Our class is based on [2-2-Data Visualization-Final.ipynb](<2-2-Data Visualization-Final.ipynb>).

### 2.2e. Exercise: Plotting Kothari et al. (2025)

In this exercise, we reproduce one of the plots from [Kothari, et al. (2025, RAST)](https://doi.org/10.1007/s11142-025-09887-3) using Python. The goal here isn't to build an empirical analysis from scratch — the authors have generously shared their underlying data, so this exercise is purely about *visualization*: taking someone else's carefully-constructed dataset and turning it into a clean, publication-style chart. The goal of this exercise is to reproduce the paper's annual CMRA plot: a chosen CMRA statistic (e.g., the median market-adjusted return around "bad news" earnings announcements) plotted by year alongside two macroeconomic series — annual CPI growth and industrial production growth.

**Learning Outcomes**

- Reading a multi-sheet Excel workbook with a non-standard header row.
- Cleaning a text-coded missing-value convention (`"."` for missing) and coercing columns to numeric.
- Filtering long-format data by category columns (`VarName`, `Sample`) and merging it with a second table on a shared key (`YEAR`).
- Building a multi-series `matplotlib` line chart with markers, a reference line, and a legend styled to resemble a published figure.

Our class is based on [2-2e-Plotting_Kothari_et_al_2025-Final.ipynb](2-2e_Plotting_Kothari_et_al_2025-Final.ipynb).

[Back to main syllabus](../README.md)
