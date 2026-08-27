**AFDEN Python Workshop for Accounting and Finance Research**

Creator: [Leonard Leye Li](https://www.unsw.edu.au/staff/leonard-leye-li)

Edition: 2026 August

---

Welcome to [AFDEN](https://www.afaanz.org/doctoral-education)'s Python workshop for Accounting and Finance (AccFin) researchers. This file provides the course outline, learning outcomes, and prerequisite readings for each module of this workshop.

## Overview

This course is designed to equip doctoral students and early career researchers in accounting and finance with foundational and practical skills in Python programming, tailored specifically for empirical research. I will cover core programming concepts, data manipulation techniques, data collection from databases and the web, natural language processing techniques, and modern statistical and machine-learning methods using Python. Through hands-on assignments and coding exercises, students will learn how to efficiently collect and clean data, perform statistical testing, build predictive models, and visualize results. The goal is not only to become competent in coding but also to use Python as a tool to enhance the quality and efficiency of academic research.

A distinctive feature of this workshop is that almost every module and session is built around understanding or replicating a published study from a top journal, such as Sloan's (1996, *The Accounting Review*) accrual anomaly,  Kim et al.'s (2016 *Journal of Accounting and Economics*) option volatility smirk, Obaid and Pukthuanthong's (2022 *Journal of Financial Economics*) image sentiment, Chen et al.'s (2022, *Journal of Accounting Research*) earnings forecasting, de Kok's (2025 *Management Science*) detection of "non-answers" in earnings call, among many others. Emphasis will be placed on applications to real-world accounting and finance data, such as databases in WRDS, SEC filings, and textual data (e.g., 10-Ks and earnings-call transcripts). Thus, the Python skills you learn are grounded in the same empirical research you'll be expected to produce.

The outline below provides a detailed description of the material that is covered in the course. The course consists of two 2-hour online modules, which introduce the Python fundamentals for research (Module 1) and the *pandas* package for handling and analysing data (Module 2), followed by a two-day in-person workshop: Day 1 covers data collection from WRDS and web scraping (Module 3), together with natural language processing and textual analysis (Module 4), and Day 2 covers generative LLMs as a research tool (Module 5) and modern statistical and machine-learning methods for accounting and finance research, including regression, classification, prediction and explainable AI (Module 6).

## Table of Contents <a name="toc"></a>

0. [Python Environment Setup](#section0)
1. [Introduction to Python Fundamentals](#section1)
2. [Handling Data and Descriptive Analysis](#section2)
3. [Data Collection](#section3)
4. [Natural Language Processing](#section4)
5. [Generative LLM for Research](#section5)
6. [Machine Learning](#section6)

## 0. Python Environment Setup<a name="section0"></a>

Before our first session, please follow the steps to set up the required Python environment on your computer.

The python version we use is 3.12, and the IDE I will use for demostration is [VS Code](https://code.visualstudio.com/download). If you prefer other IDEs such as PyCharm or jupyter notebook, you are welcome to use the one you are familar with.

I set up the python environment using `uv`, which is fast and easy for begginers. If you have already known how to use `pip` or `conda` to set up your Python virtual environment, you can use your preferred method and ignore the following steps. Just make sure you have installed all the packages in [requirements file](./requirements.txt).

1. **Install `uv`**: See [docs.astral.sh/uv/getting-started/installation](https://docs.astral.sh/uv/getting-started/installation/)
   - If you are using Windows: open Command Prompt, type `winget install --id=astral-sh.uv  -e`
   - If you are using Mac OS: open Terminal, type `wget -qO- https://astral.sh/uv/install.sh | sh`
   - To check if `uv` is successfully installed, type `uv --version`
2. **Install VS Code** from [code.visualstudio.com/download](https://code.visualstudio.com/download). In VS Code, Install the following Extensions (on the left column):
   - Data Wrangler
   - Jupyter
   - Python
3. Download this Github repository to your local disk.
   - Click the  green "<> Code" button and click "Download ZIP"
   - Create a new folder on your computer and extract the ZIP file in that directory
   - Open the directory using VS Code (or your IDE). In Terminal, run `uv sync`.

If you also want to learn how to use `conda` and some basic concepts of Python modules and packages, I encourage you to take [the course by ANACONDA (1 hour)](https://learning.anaconda.com/courses/get-started-with-anaconda).

[Back to ToC](#toc)

## 1. Introduction to Python Fundamentals<a name="section1"></a>

In this first module, we will quickly go through the Python Basics, from data types to control flows. This module is designed with beginners in mind. You will be introduced to the essential building blocks of Python, moving step by step from basic concepts to more practical applications. Along the way, you will practice coding through short examples and exercises. I will also share the functions that I frequently uesed in my own research such as list conprehension and lambda functions. By the end, you’ll put everything together in a fun project: building a simple chat bot.

**Prerequisite reading**

You can go through the [1-1-Intro_to_Python.ipynb](<Module%201-Introduction%20to%20Python%20Fundamentals/1-1-Intro_to_Python.ipynb>) file before class.

**Learning Outcomes**

By completing this module, you will be able to:

- Understand Python’s core data types (integers, floats, strings, booleans) and how they are used.
- Work with collections such as lists and dictionaries to store and manage groups of data.
- Define and use functions to organize and reuse code effectively.
- Apply control flows (if statements, loops) to make decisions and repeat tasks in your programs.
- Handle errors gracefully using Python’s exception handling features.
- Import and use packages to extend Python’s functionality.
- Integrate your knowledge by developing a simple chat bot that responds to user input.

Our class is based on [1-1-Intro_to_Python.ipynb](<Module%201-Introduction%20to%20Python%20Fundamentals/1-1-Intro_to_Python.ipynb>) (completed version: [1-1-Intro_to_Python-Final.ipynb](<Module%201-Introduction%20to%20Python%20Fundamentals/1-1-Intro_to_Python-Final.ipynb>)).

### 1.2. Opening Files: the `with` Context Manager

Research work involves more than data living inside Python's memory — it means reading data from files (a `.txt` file of a 10-K filing, a `.csv` of Compustat data) and writing results back to disk. This session introduces Python's `with` statement (the **context manager**) as the safe, Pythonic way to open and close files, contrasting it with the error-prone manual `open()`/`close()` pattern. You will practice reading and writing text files, choosing the correct file mode, and applying these skills to a research example — loading an R&D keyword list used to measure innovation disclosure in 10-Ks.

**Learning Outcomes**

By completing this session, you will be able to:

- Explain why files must be explicitly closed, and the risks of forgetting (lost writes, locked files) — especially when an error interrupts execution before `close()` is reached.
- Use the `with` statement to open a file safely, so it is closed automatically even if the code inside the block raises an error.
- Choose the correct file mode (`"r"`, `"w"`, `"a"`, `"x"`, and their binary variants) for a given task, and recognize the destructive effect of `"w"` mode on an existing file.
- Read a file back with `.read()`, `.readlines()`, or by iterating line by line, and choose the right method based on file size.
- Open two files in a single `with` statement to read from one and write to another.
- Recognize the `with` pattern beyond files — e.g., WRDS database connections, Excel writers, network sessions — and apply the rule of thumb: if a library gives you something you are supposed to `close()`, open it with `with`.

Our class is based on [1-2-Context_Manager.ipynb](<Module%201-Introduction%20to%20Python%20Fundamentals/1-2-Context_Manager.ipynb>) (completed version: [1-2-Context_Manager-Final.ipynb](<Module%201-Introduction%20to%20Python%20Fundamentals/1-2-Context_Manager-Final.ipynb>)).

### 1.3o. Object-Oriented Programming Basics (Optional)

A brief, optional follow-on session introducing Object-Oriented Programming (OOP) in Python, using a running `FirmYear`/Compustat-style example.

**Learning Outcomes**

By completing this session, you will be able to:

- Explain what Object-Oriented Programming is and why it is useful in AccFin research.
- Create and use **classes** and **objects**, including composing one class from another.
- Apply core OOP concepts: **attributes**, **methods**, and **encapsulation** (public/protected/private access, getters/setters, and the `@property` decorator).
- Distinguish instance-level from static (class-level) attributes and methods.
- Recognize **inheritance** and **polymorphism** through a simple example.

Our class is based on [1-3o_OOP Basics.ipynb](<Module%201-Introduction%20to%20Python%20Fundamentals/1-3o_OOP%20Basics.ipynb>).

[Back to ToC](#toc)

## 2. Handling Data and Descriptive Analysis<a name="section2"></a>

`pandas` is the most useful Python library for data analysis in AccFin research. In this module, you will learn how to use `pandas` to handle data in tabular form. We will cover the fundamental operations needed to load data, explore it, clean it, and prepare it for further analysis, then move on to visualizing it with `matplotlib` and `seaborn`. By the end, you'll have the skills to manage real-world datasets and replicate two seminal papers.

### 2.1. Handling Data with `pandas`

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

Our class is based on [2-1-Pandas.ipynb](<Module%202-Handling%20Data%20and%20Descriptive%20Analysis/2-1_Pandas.ipynb>).

### 2.1e-1. Exercise: Replicating Stata's `winsor2`

A homework exercise embedded in the `pandas` session: write a `winsorize_by_group()` function that replicates Stata's `winsor2` command, winsorizing or truncating variables at a chosen percentile, optionally within groups.

Our class is based on [2-1e-1-winsor2.ipynb](<Module%202-Handling%20Data%20and%20Descriptive%20Analysis/2-1e-1_winsor2.ipynb>).

### 2.1e-2. Exercise: Replicating Sloan (1996)

This exercise replicates a simplified version of the seminal study by [Sloan (1996)](https://www.jstor.org/stable/248290), one of the most cited papers in accounting and finance research on the *accrual anomaly*. Using the `pandas` skills from 2.1, you construct accrual, cash-flow, and earnings variables from a Compustat/CRSP-style panel, form annual accrual-decile portfolios, and plot the hedge-portfolio returns, similar to Table 6 and Figure 2 of the paper.

Our class is based on [2-1e-2-Replicating_Sloan_1996-Final.ipynb](<Module%202-Handling%20Data%20and%20Descriptive%20Analysis/2-1e-2-Replicating_Sloan_1996-Final.ipynb>).

### 2.2. Data Visualization

Data visualization is a critical skill in data analytics, enabling researchers to transform raw data into clear, compelling insights. This session introduces students to two of the most widely used Python libraries for visualization — `matplotlib` and `seaborn`. Students will learn how to create, customize, and interpret a range of plots, from simple line and bar charts to more advanced statistical graphics that are commonly used in AccFin research. By emphasizing both the technical aspects of coding and the principles of effective visual communication, this class equips students to present data in ways that are accurate, insightful, and persuasive for business and research contexts.

**Prerequisite reading**

- Kothari, S. P., B. Schonberger, C. Wasley, and J. Xiao (2025). The first half-century of empirical capital markets research in accounting in pictures. *Review of Accounting Studies* 30: 3111-3176. ([link](https://doi.org/10.1007/s11142-025-09887-3))

**Learning Outcomes**

By completing this session, you will be able to:

- Apply `matplotlib` and `seaborn` to construct foundational plots (line, bar, histogram, scatter, KDE, boxplot, violin, ECDF, Q-Q) and customize elements such as axes, labels, legends, colors, and styles.
- Enhance clarity and impact of visualizations through effective use of color, scaling, and annotation.

Our class is based on [2-2-Data Visualization-Final.ipynb](<Module%202-Handling%20Data%20and%20Descriptive%20Analysis/2-2-Data%20Visualization-Final.ipynb>).

### 2.2e. Exercise: Plotting Kothari et al. (2025)

This exercise reproduces one of the annual CMRA plots from [Kothari et al. (2025)](https://doi.org/10.1007/s11142-025-09887-3). Unlike the Sloan (1996) exercise, the goal here isn't to build an empirical analysis from scratch — the authors have generously shared their underlying data, so this exercise is purely about visualization: combining their shared data with macroeconomic series into a publication-style `matplotlib` chart.

Our class is based on [2-2e-Plotting_Kothari_et_al_2025-Final.ipynb](<Module%202-Handling%20Data%20and%20Descriptive%20Analysis/2-2e_Plotting_Kothari_et_al_2025-Final.ipynb>).

[Back to ToC](#toc)

## 3. Data Collection<a name="section3"></a>

Empirical AccFin research relies its data. This module covers the three ways researchers get it into Python:

* querying the structured databases on **WRDS** (Compustat, CRSP, IBES, OptionMetrics),
* **scraping** disclosures that are only available as web pages, and
* calling **third-party APIs** (SEC EDGAR, Google Maps) for filings and geographic data.

Each session is built around a real research task: constructing an option-implied crash-risk measure, building a dataset of SEC enforcement actions, geocoding firm addresses.

### 3.1. Accessing WRDS with Python

Access to high-quality financial and economic data is fundamental for empirical research in AccFin. The Wharton Research Data Services (WRDS) platform, which provides a gateway to a wide range of leading databases such as Compustat, CRSP and IBES, is the most commonly used data platform for AccFin empirical research. In this session, we will learn how to use the `wrds` Python package to connect programmatically to WRDS, query structured datasets, and efficiently download and manage data for analysis. The session emphasizes both the technical skills required for accessing large-scale databases and the research practices necessary to ensure data integrity, reproducibility, and efficiency in academic and applied settings.

**Prerequisite reading**

- You can preview the [tutorial provided by WRDS](https://wrds-www.wharton.upenn.edu/pages/support/programming-wrds/programming-python/querying-wrds-data-python/).
- Appendix B of Kim, J. B., Li, L., Lu, L. Y., & Yu, Y. (2016). Financial statement comparability and expected crash risk. *Journal of Accounting and Economics* 61(2-3): 294-312. ([link](https://doi.org/10.1016/j.jacceco.2015.12.003))

**Learning Outcomes**

By the end of this class, you will be able to:

- Understand the role of WRDS as a central platform for accessing accounting and financial datasets.
- Establish a secure connection to WRDS using the `wrds` Python package, including creating a `.pgpass` file for password authentication.
- Query the dataset structure: list available libraries and tables, and inspect a table's column headers.
- Formulate and execute SQL queries within Python using `raw_sql()` to retrieve specific datasets, including joins across Compustat and the CRSP-Compustat Merged (CCM) link table.
- Download and manage large datasets, including filtering, merging, and exporting to Stata or CSV.
- Integrate WRDS data with Python workflows, preparing it for use in packages such as `pandas` and `statsmodels`.
- Apply best practices for reproducible research, including documenting queries and saving data pipelines.

Our class is based on [3-1-WRDS_with_Python-Final.ipynb](<Module%203-Data%20Collection/3-1-WRDS_with_Python-Final.ipynb>).

### 3.1e. Exercise: Building the Option Volatility Smirk from OptionMetrics

This exercise builds a firm-year panel of the option-implied volatility smirk from scratch, using the WRDS querying skills from 3.1. Following [Kim, Li, Lu and Yu (2016)](https://doi.org/10.1016/j.jacceco.2015.12.003), it aggregates OptionMetrics' daily option-price files server-side in SQL to get the open-interest-weighted implied volatility of at-the-money calls and out-of-the-money puts, caching each year to Parquet, linking identifiers across OptionMetrics, CRSP and Compustat with range joins on validity dates, building the accounting controls, and collapsing the daily smirk into a firm-year measure of expected crash risk.

**Learning Outcomes**

- Aggregating a very large table server-side in SQL, so that only the summarised rows travel over the network.
- Looping over year-partitioned WRDS tables and caching each year's result to disk.
- Linking identifiers across three databases (OptionMetrics, CRSP, Compustat) with range joins on validity dates.
- Collapsing daily data to a firm-year panel over a custom event window, without blowing up memory.

Our class is based on [3-1e-Option_Volatility_Smirk-Final.ipynb](<Module%203-Data%20Collection/3-1e-Option_Volatility_Smirk-Final.ipynb>).

### 3.2. Web Scraping

In modern AccFin research, valuable data is often "locked" inside company websites, regulatory documents, and other websites. While numerical datasets (CRSP, Compustat, WRDS) are well-structured and easy to query, textual and legal disclosures frequently require researchers to gather data directly from the web. This session introduces web scraping in Python as a tool to collect, clean, and analyze information from online sources. Using the SEC Accounting and Auditing Enforcement Releases (AAER) archive as our central case study, you will learn how to extract structured datasets from unstructured web pages, handling the unique challenges of financial text — and the responsibilities (site terms, rate limits, ethical research practices) that come with web scraping.

**Prerequisite reading**

- Karpoff, J. M., Koester, A., Lee, D. S., & Martin, G. S. (2017). Proxies and databases in financial misconduct research. *The Accounting Review* 92(6): 129-163. ([link](https://doi.org/10.2308/accr-51766))

**Learning Outcomes**

By the end of this session, you will be able to:

- Understand the role of web scraping in AccFin research, and identify cases where scraping is necessary to build novel datasets.
- Apply Python libraries such as `requests`, `BeautifulSoup`, and `pandas` to access web pages programmatically, parse HTML structures with `find()`/`find_all()`/CSS selectors to locate relevant information, and store results in clean, structured formats (e.g., CSV).
- Implement scraping logic to handle pagination, nested links, and multiple fields (e.g., dates, respondents, release numbers).
- Practice responsible scraping by setting custom User-Agents, respecting rate limits and `robots.txt`, and following ethical/legal guidelines for automated data collection.
- Clean and normalize extracted data with regular expressions, converting messy text into structured variables (e.g., extracting AAER numbers and release references).
- Integrate scraped data into empirical workflows, linking enforcement case information to firm fundamentals, stock market data, or textual analysis pipelines.

Our class is based on [3-2-Web_Scraping-Final.ipynb](<Module%203-Data%20Collection/3-2-Web_Scraping-Final.ipynb>).

### 3.3o. Using the Google Maps API (Optional)

Many datasets in AccFin research include a street address somewhere — a corporate headquarters, an audit office, a plant. Once that address is geocoded into latitude/longitude, geography becomes a source of research variables in its own right. This optional session covers Google's Python clients for the Google Maps Platform — `googlemaps` for geocoding, and the `google-maps-routing` / `google-maps-places` clients for directions, distances, and place search.

**Optional reading**

- Chen, C., Chen, Y., Pittman, J. A., Podolski, E. J., & Veeraraghavan, M. (2022). Emotions and managerial judgment: Evidence from sunshine exposure. *The Accounting Review* 97(3): 179-203. ([link](https://doi.org/10.2308/TAR-2020-0215))
- Ma, T., Wan, C., Wang, Y., & Zhao, Y. (2024). Individual auditor turnover and audit quality—Large sample evidence from US audit offices. *The Accounting Review* 99(6): 297-324. ([link](https://doi.org/10.2308/TAR-2021-0862))

**Learning Outcomes**

By the end of this session, you will be able to:

- Geocode an address to latitude/longitude, and reverse-geocode coordinates back to an address.
- Compute travel routes, distances, and durations between locations using the Routes API.
- Search for nearby places and retrieve place details using the Places API (New).

Our class is based on [3-3o-Google_Map_API.ipynb](<Module%203-Data%20Collection/3-3o-Google_Map_API.ipynb>).

### 3.4o. Using the SEC EDGAR API (Optional)

The U.S. Securities and Exchange Commission's (SEC) EDGAR database is a critical resource for financial and accounting research, providing open access to corporate filings such as 10-K/Qs, 8-Ks, and proxy statements. However, navigating and retrieving this information manually can be time-consuming and inefficient. This session introduces you to `secedgar` Python package, which provides a convenient interface to the SEC EDGAR API services. In this optional module, you will learn how to automate the process of searching and downloading regulatory filings to build structured datasets for empirical analysis. The class emphasizes both technical implementation and research applications, highlighting how SEC filings can be leveraged for corporate disclosure studies, textual analysis, and financial statement research.

**Learning Outcomes**

By the end of this class, you will be able to:

- Explain the role of SEC EDGAR in financial markets and academic research.
- Install and configure `secedgar` to access SEC filings through the EDGAR API.
- Look up company CIKs, and retrieve corporate filings programmatically, including annual reports (10-K), quarterly reports (10-Q), and event-driven filings (8-K).
- Automate large-scale data collection, including batch downloads across firms and time periods.
- Organize and manage raw filings for downstream textual analysis.

Our class is based on [3-4o-SEC_API.ipynb](<Module%203-Data%20Collection/3-4o-SEC_API.ipynb>).

[Back to ToC](#toc)

## 4. Natural Language Processing<a name="section4"></a>

AccFin research is no longer limited to numerical disclosures and structured data. Textual data — the MD&A and risk-factor sections of 10-K filings, earnings-call transcripts, analyst reports — carries rich information about firms' strategies, risks, and performance. This module works through Natural Language Processing (NLP) in Python, moving from simple pattern-matching to a large language model built specifically for AccFin research:

- **Regular expressions** (and the `textstat` package): identifying, extracting, and cleaning patterns in text, and computing readability metrics.
- **Dictionary-based textual analysis**: scoring text with the Loughran-McDonald word lists, the standard "bag-of-words" approach in AccFin research.
- **Text vectorization** (bag-of-words, TF-IDF, n-grams) with `scikit-learn`, and visualizing term frequencies as word clouds.
- **FinBERT**: a large language model pretrained on financial text, used to classify sentiment and fine-tuned on your own labeled data.

By the end of the module you will be able to replicate influential textual-analysis studies in AccFin and apply modern NLP tools — from a handful of keywords to a domain-specific LLM — to your own research.

**Prerequisite reading**

- Loughran, T., & McDonald, B. (2011). When is a liability not a liability? Textual analysis, dictionaries, and 10‐Ks. *The Journal of Finance* 66(1): 35-65. ([link](https://doi.org/10.1111/j.1540-6261.2010.01625.x))
- Merkley, K. J. (2014). Narrative disclosure and earnings performance: Evidence from R&D disclosures. *The Accounting Review* 89(2): 725-757. ([link](https://doi.org/10.2308/accr-50649))
- Section 3.3 of Teoh, S. H. (2018). The promise and challenges of new datasets for accounting research. *Accounting, Organizations and Society* 68: 109-117. ([link](https://doi.org/10.1016/j.aos.2018.03.008))
- Huang, A. H., Wang, H., & Yang, Y. (2023). FinBERT: A large language model for extracting information from financial text. *Contemporary Accounting Research* 40(2): 806-841. ([link](https://doi.org/10.1111/1911-3846.12832))

You can also watch [the video by Corey Schafer (53 mins)](https://youtu.be/K8L6KVGG-7o?si=H83lHipbbrHELfXD) for a thorough introduction to regular expressions in Python before class.

### 4.1. NLP Basics and Regular Expressions

This session introduces NLP in Python with a focus on **regular expressions** (the `re` module): patterns used to match, search, extract, and replace text. You will process unstructured disclosure text — identifying financial terms, footnotes, and forward-looking statements, and stripping tables, formatting artifacts, and boilerplate — and turn it into features that can be linked to financial and capital-market outcomes.

**Learning Outcomes**

By the end of this session, you will be able to:

- Understand the role of textual analysis in AccFin research, particularly how narrative disclosures affect investors, regulators, and other stakeholders.
- Use Python's `re` package with `re.findall()` and `re.sub()` to identify patterns (financial terms, footnotes, forward-looking statements) and clean raw disclosures.
- Build reproducible pipelines that ingest a collection of text files (e.g., 10-K sections), extract features, and output structured datasets.
- Critically evaluate the limitations of preprocessing methods and discuss best practices for textual analysis in academic work.

Our class is based on [4-1-NLP_Basics_and_Regex-Final.ipynb](<Module%204-Natural%20Language%20Processing/4-1-NLP_Basics_and_Regex-Final.ipynb>).

### 4.1o. Readability with `textstat` (Optional)

A short introduction to the `textstat` package: character/word/syllable/sentence counts, and the readability indices most cited in the disclosure literature (Gunning Fog, SMOG, Flesch Reading Ease, Flesch-Kincaid, Coleman-Liau, Dale-Chall), computed for single texts and across a corpus.

Our class is based on [4-1o-textstat.ipynb](<Module%204-Natural%20Language%20Processing/4-1o-textstat.ipynb>).

### 4.2. Dictionary-Based Textual Analysis

This session applies the standard "bag-of-words" approach: scoring disclosure text against curated word lists. Using the Loughran-McDonald master dictionary and a stop-word list, and the R&D keyword list from Merkley (2014), you build a reproducible pipeline that ingests a collection of 10-K text files, flags R&D-related sentences, and outputs a structured dataset of readability and tone (positive, negative, uncertainty, complexity) measures.

**Learning Outcomes**

By the end of this session, you will be able to:

- Load and use textual-analysis resources (Loughran-McDonald dictionary, generic stop words, keyword lists).
- Tokenize text into sentences and words with `nltk`, and flag sentences containing target phrases.
- Score text against the Loughran-McDonald dictionary to measure tone, uncertainty, and complexity.
- Compute readability of a specific disclosure passage, and assemble filing-level variables keyed to CIK and accession number.

Our class is based on [4-2-Dictionary_Based_Textual_Analysis-Final.ipynb](<Module%204-Natural%20Language%20Processing/4-2-Dictionary_Based_Textual_Analysis-Final.ipynb>).

### 4.3. Text Vectorization and Word Clouds

Dictionary methods only check whether specific words are present. This session builds the bag-of-words / document-term matrix properly — representing each piece of text as a vector of *all* its words — reusing the R&D-flagged sentences saved in 4.2.

**Learning Outcomes**

By the end of this session, you will be able to:

- Represent text numerically with `scikit-learn`'s `CountVectorizer` and `TfidfVectorizer` (bag-of-words, TF-IDF).
- Explain why TF-IDF reweights frequent-but-undistinctive words downward, and capture multi-word phrases with `ngram_range`.
- Visualize term importance as word clouds, from raw counts, TF-IDF weights, or raw text.
- Recognize the limitations of keyword-based extraction by comparing word clouds across filings.

Our class is based on [4-3-Text_Vectorization_and_WordClouds-Final.ipynb](<Module%204-Natural%20Language%20Processing/4-3-Text_Vectorization_and_WordClouds-Final.ipynb>).

### 4.4. FinBERT Sentiment

Dictionary counts and TF-IDF weights both treat text as a *bag* of words — order and context are discarded. **FinBERT** (Huang, Wang, and Yang 2023) is a large language model pretrained on 4.9 billion words of financial text that reads a sentence in context instead. This session uses an already fine-tuned FinBERT to classify sentiment, compares it against the Loughran-McDonald dictionary sentence by sentence, and aggregates sentence-level output into a document-level tone measure — applied to R&D disclosures and to real Tesla earnings-call transcripts.

**Learning Outcomes**

By the end of this session, you will be able to:

- Explain what distinguishes a domain-pretrained large language model (FinBERT) from dictionary- and classic-ML approaches, and why that matters for financial text.
- Load `yiyanghkust/finbert-tone` and classify the sentiment of financial sentences in batches with `transformers`.
- Compare FinBERT against a Loughran-McDonald rule, and interpret the disagreements.
- Aggregate sentence-level labels into a document-level *Tone* measure (share positive minus share negative), and apply it to an earnings-call transcript.

Our class is based on [4-4-FinBERT_Sentiment-Final.ipynb](<Module%204-Natural%20Language%20Processing/4-4-FinBERT_Sentiment-Final.ipynb>).

### 4.4o. Fine-Tuning FinBERT (Optional)

An optional, more advanced class that fine-tunes the *pretrained* FinBERT on a small labeled dataset (the Financial PhraseBank), following the FinBERT repository's own recipe. It replicates the paper's small-sample finding — a few hundred task-specific sentences is often enough — and quantifies what fine-tuning buys over an already fine-tuned model.

**Learning Outcomes**

- Tokenize a labeled dataset and wrap it as a Hugging Face `datasets.Dataset`.
- Fine-tune `BertForSequenceClassification` with the `transformers` `Trainer` API (learning rate, epochs, early evaluation).
- Evaluate a fine-tuned model on a held-out test set, and compare it against a zero-shot model.
- Weigh the trade-offs (accuracy, cost, interpretability) between dictionary, classic ML, and LLM-based textual analysis.

Our class is based on [4-4o-FinBERT_Finetuning.ipynb](<Module%204-Natural%20Language%20Processing/4-4o-FinBERT_Finetuning.ipynb>).

[Back to ToC](#toc)

## 5. Generative LLM for Research<a name="section5"></a>

Generative LLMs are increasingly used in accounting research for textual-analysis tasks that used to require either dictionary/bag-of-words methods or costly manual human coding — classifying disclosure tone, extracting structured facts from filings, detecting evasive "non-answers" in earnings-call Q&As. This module introduces the Python client libraries for two major providers — OpenAI and Google Gemini — covering the mechanics you need before using an LLM as a research tool (prompts, structured JSON output, multi-turn conversations, multimodal input), then applies them to research settings through a replication exercise and an optional image-analysis exercise.

**Prerequisite reading**

- de Kok, T. (2025). ChatGPT for textual analysis? How to use generative LLMs in accounting research. *Management Science* 71(9): 7888-7906. ([link](https://doi.org/10.1287/mnsc.2023.03253))
- Blankespoor, E., deHaan, E., & Li, Q. (2026). Generative AI in financial reporting. *Journal of Accounting Research* 64(3): 1189-1232. ([link](https://doi.org/10.1111/1475-679x.7005))

### 5.1. Using Generative LLM APIs in AccFin Research

This session covers the API-level building blocks a research design is built on: setting up keys securely, sending prompts, requesting schema-conformant structured output, holding a chat, and passing images — with both the OpenAI (`openai`) and Google Gemini (`google-genai`) Python clients.

**Learning Outcomes**

By the end of this session, you will be able to:

- Set up API keys securely via a `.env` file for both OpenAI and Google Gemini.
- Send text prompts and read model output using both providers' Python clients.
- Request structured (JSON) output from a model using a defined schema (e.g., a Pydantic model).
- Hold a multi-turn conversation (chat) with an LLM.
- Pass images as multimodal input.

Our class is based on [5-1-LLM_API-Final.ipynb](<Module%205-Generative%20LLM%20for%20Research/5-1-LLM_API-Final.ipynb>).

### 5.1e-1. Exercise: Detecting Non-Answers in Earnings Conference Calls

This exercise replicates the core of the case study in de Kok ([2025](https://doi.org/10.1287/mnsc.2023.03253)) on 13 Tesla Q4 earnings-call transcripts. A **non-answer** is a response in which a manager signals an inability or unwillingness to provide the information asked for. The notebook works through de Kok's four-step framework: parsing raw transcripts into question-answer pairs, choosing a zero-shot approach and model, developing a prompt with explicit coding rules and a Pydantic output schema, running the classification with logging and resumability, and — critically — evaluating construct validity against a keyword baseline and a hand-coded sample before scaling to all 13 calls.

**Learning Outcomes**

- Turn a messy Markdown transcript into a structured table of question-answer pairs with regular expressions.
- Design a zero-shot classification prompt: coding rules, "what is *not*" a non-answer, chain-of-thought field ordering, and stating the expected class distribution.
- Log raw prompts and completions as the primary data of the study, and build a resumable, concurrent inference loop.
- Evaluate a minority-class classifier with precision/recall/F1 (not accuracy), and test a prompt's robustness to its own wording.

Our class is based on [5-1e-1-No_Answer_in_CC-Final.ipynb](<Module%205-Generative%20LLM%20for%20Research/5-1e-1-No_Answer_in_CC-Final.ipynb>).

### 5.1e-2. Exercise: Detecting the Use of GenAI in 10-K Reports

This exercise applies ZeroGPT to detect the use of generative AI in firms' 10-K reports, based on Blankespoor, deHaan, and Li ([2026](https://doi.org/10.1111/1475-679x.7005)).

### 5.2o. Identifying Common Visual Themes in an Annual Report (Optional)

An optional exercise applying the Gemini API skills from 5.1 to a real annual report: extracting embedded photographs from a PDF (filtering out signatures and logos by pixel area), captioning each with Gemini (flagging and excluding director/executive headshots), and summarizing the most common visual themes with a schema-constrained call — motivated by Obaid and Pukthuanthong (2022).

**Optional reading**

- Obaid, N., & Pukthuanthong, K. (2022). A picture is worth a thousand words: Measuring investor sentiment by combining machine learning and photos from news. *Journal of Financial Economics* 144(1): 273-297. ([link](https://doi.org/10.1016/j.jfineco.2021.06.002))

**Learning Outcomes**

- Extract and filter embedded images from a PDF with PyMuPDF (`fitz`).
- Send images to Gemini for captioning, and use a lightweight label convention to route the output.
- Summarize a corpus of captions into a structured list of themes with Structured Outputs.

Our class is based on [5-2o-Identifying_Images.ipynb](<Module%205-Generative%20LLM%20for%20Research/5-2o-Identifying_Images.ipynb>).

[Back to ToC](#toc)

## 6. Machine Learning<a name="section6"></a>

Machine learning has become a core empirical tool in AccFin research: tree ensembles and other flexible models now routinely outperform traditional linear benchmarks at prediction tasks such as forecasting earnings, detecting misstatements, and assessing credit risk. This module builds up from classical statistical inference to modern gradient-boosted trees, replicating recent AccFin papers along the way — a linear-regression specification, a classification task, a regression/forecasting task, and an explainability exercise that opens up what the model actually learned.

**Prerequisite reading**

- Chen, X., Cho, Y. H. (T.), Dou, Y., & Lev, B. (2022). Predicting future earnings changes using machine learning and detailed financial data. *Journal of Accounting Research* 60(2): 467-515. ([link](https://doi.org/10.1111/1475-679X.12429))
- Parker, C. (A.) Z., Jiang, L., Cho, S., & Vasarhelyi, M. A. (2025). Predicting material misstatements using machine learning. *The Accounting Review* 100(6): 225-262. ([link](https://doi.org/10.2308/TAR-2024-0035))

### 6.1. Statistical Testing and Regression

A refresher on classical statistical inference — the toolkit that empirical AccFin research rests on, and the benchmark against which the machine-learning methods in the rest of the module are judged. Section 1 works through the three *t*-tests you will use most with `scipy.stats`; Section 2 builds one complete specification of Kim, Li, Lu and Yu (2016), using the option volatility smirk panel constructed in the Module 3 exercise, estimating it with `pyfixest`.

**Prerequisite reading**

- Kim, J. B., Li, L., Lu, L. Y., & Yu, Y. (2016). Financial statement comparability and expected crash risk. *Journal of Accounting and Economics* 61(2-3): 294-312. ([link](https://doi.org/10.1016/j.jacceco.2015.12.003))

**Learning Outcomes**

By the end of this session, you will be able to:

- Run and interpret one-sample, independent-samples, and paired *t*-tests using `scipy.stats`.
- Aggregate a very large daily database into firm-year variables efficiently, by computing sufficient statistics on the WRDS server rather than downloading raw rows.
- Assemble an estimation sample the way a published paper does — sample filters, winsorizing continuous variables.
- Specify and estimate a linear regression with `pyfixest` using R-style formula syntax.
- Explain why standard errors in a firm-year panel must be clustered, and estimate two-way (firm and year) clustered standard errors.
- Absorb high-dimensional fixed effects, and explain via the Frisch-Waugh-Lovell theorem why this is equivalent to (and better than) adding a dummy per firm.
- Assemble a publication-style regression table with `pf.etable()`.

Our class is based on [6-1-Statistical_Testing_and_Regression-Final.ipynb](<Module%206-Machine%20Learning/6-1-Statistical_Testing_and_Regression-Final.ipynb>). Section 2 continues the Module 3 exercise [3-1e-Option_Volatility_Smirk-Final.ipynb](<Module%203-Data%20Collection/3-1e-Option_Volatility_Smirk-Final.ipynb>).

### 6.2. Classification with XGBoost: Predicting the Direction of Earnings Changes

Following Chen et al. (2022), this session frames the direction of next-year earnings changes as a binary classification problem, engineers a wide set of Compustat-based predictors, and benchmarks a logistic regression against `xgboost.XGBClassifier`.

**Learning Outcomes**

By the end of this session, you will be able to:

- Frame a prediction problem (direction of earnings changes) as a binary classification task, using a drift-adjusted label.
- Engineer a wide set of financial-statement predictors (current value, lagged value, percentage change) by auto-detecting columns rather than hand-picking a subset.
- Explain why panel data needs a **chronological** train/validation/test split rather than a random one.
- Fit and evaluate a `LogisticRegression` benchmark (with imputation and scaling) and an `xgboost.XGBClassifier` (NaNs and all), and compare them with ROC-AUC and ROC curves.
- Tune an XGBoost model with a validation set and `early_stopping_rounds`.
- Read a gain-based feature-importance plot, and understand its limitations.

Our class is based on [6-2-Classification-Final.ipynb](<Module%206-Machine%20Learning/6-2-Classification-Final.ipynb>).

### 6.3. Forecasting Continuous Earnings with XGBoost

This session reuses 6.2's data and feature pipeline but predicts next-year *continuous* EPS — a regression task — following Chattopadhyay, Fang, and Mohanram (2025). It benchmarks a naive random-walk forecast and a regularized (Ridge) regression against an `xgboost.XGBRegressor` fit with a Huber loss.

**Prerequisite reading**

- Chattopadhyay, A., Fang, B., & Mohanram, P. (2025). Machine learning for earnings forecasting — US and international evidence. Working paper. ([link](https://dx.doi.org/10.2139/ssrn.5941658))

**Learning Outcomes**

By the end of this session, you will be able to:

- Frame a forecasting problem as a regression task, and implement a one-line random-walk benchmark.
- Explain why regression targets built from raw accounting data need outlier treatment (winsorizing using training-period bounds only) before a linear model can be trusted, and why tree ensembles are more forgiving.
- Fit `xgboost.XGBRegressor` with a Huber loss objective, and tune it with early stopping.
- Evaluate forecasts with price-scaled MAFE, RMSE, and MDAFE.
- Read an XGBoost regression feature-importance plot.

Our class is based on [6-3_Earnings_Forecasting-Final.ipynb](<Module%206-Machine%20Learning/6-3_Earnings_Forecasting-Final.ipynb>).

### 6.4o. Explainable AI: Using SHAP to Understand an XGBoost Model (Optional)

Following Parker et al. (2025), this optional session picks up the classification model from 6.2 and applies SHAP (SHapley Additive exPlanations) to understand which predictors drive it and how — going beyond a single gain-based importance score to directional, per-observation explanations.

**Learning Outcomes**

- Explain what a SHAP value is and how it differs from a gain-based feature-importance score.
- Use `shap.TreeExplainer` to compute exact SHAP values for an XGBoost model.
- Read SHAP bar, beeswarm, dependence (scatter), and waterfall plots to understand which features drive predictions, in which direction, and why for an individual firm-year.
- Critically interpret machine-learning output as an attention-directing tool rather than evidence of causation.

Our class is based on [6-4o-Explainable_AI.ipynb](<Module%206-Machine%20Learning/6-4o-Explainable_AI.ipynb>).

[Back to ToC](#toc)
