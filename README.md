**AFDEN Python Workshop for Accounting and Finance Research**

Creator: [Leonard Leye Li](https://www.unsw.edu.au/staff/leonard-leye-li)

Edition: 2026 Jul

---

Welcome to [AFDEN](https://www.afaanz.org/doctoral-education)'s Python workshop for Accounting and Finance (AccFin) researchers. This file provides the course introductions, learning outcomes, and prerequisite readings for each module of this workshop.

## Table of Contents <a name="toc"></a>

0. [Python Environment Setup](#section0)
1. [Introduction to Python Fundamentals](#section1)
2. [Handling Data and Descriptive Analysis with `pandas`](#section2)
3. [Data Collection](#section3)
4. [Natural Language Processing](#section4)
5. [Machine Learning](#section5)

## 0. Python Environment Setup <a name="section0"></a>

Before our first session, please follow the steps to set up the required Python environment on your computer.

The python version we use is 3.12, and the IDE I will use for demostration is VS Code. If you prefer other IDEs such as PyCharm or jupyter notebook, you are welcome to use the one you are familar with.

I set up the python environment using `uv`, which is fast and easy for begginers. If you have already known how to use `pip` or `conda` to set up your Python virtual environment, you can use your preferred method and ignore the following steps. Just make sure you have installed all the packages in [requirements file](./requirements.txt).

1. **Install `uv`**: See https://docs.astral.sh/uv/getting-started/installation/
   - If you are using Windows: open Command Prompt, type `winget install --id=astral-sh.uv  -e`
   - If you are using Mac OS: open Terminal, type `wget -qO- https://astral.sh/uv/install.sh | sh`
   - To check if `uv` is successfully installed, type `uv --version`
2. **Install VS Code** from https://code.visualstudio.com. In VS Code, Install the following Extensions (on the left column):
   - Data Wrangler
   - Jupyter
   - Python
3. Download this Github repository to your local disk.
   - Click the  green "<> Code" button and click "Download ZIP".
   - Create a new folder on your computer and extract the ZIP file in that directory
   - Open the directory using VS Code (or your IDE). In Terminal, run `uv sync`.

If you also want to learn how to use `conda` and some basic concepts of Python modules and packages, I encourage you to take [the course by ANACONDA (1 hour)](https://learning.anaconda.com/courses/get-started-with-anaconda).

[Back to ToC](#toc)

## 1. Introduction to Python Fundamentals <a name="section1"></a>

In this first module, we will quickly go through the Python Basics, from data types to control flows. This module is designed with beginners in mind. You will be introduced to the essential building blocks of Python, moving step by step from basic concepts to more practical applications. Along the way, you will practice coding through short examples and exercises. I will also share the functions that I frequently uesed in my own research such as list conprehension and lambda functions. By the end, you’ll put everything together in a fun project: building a simple chat bot.

**Prerequisite reading**

You can go through the [1-1-Intro_to_Python.ipynb](<Module 1-Introduction to Python Fundamentals/1-1-Intro_to_Python.ipynb>) file before class.

**Learning Outcomes**

By completing this module, you will be able to:

- Understand Python’s core data types (integers, floats, strings, booleans) and how they are used.
- Work with collections such as lists and dictionaries to store and manage groups of data.
- Define and use functions to organize and reuse code effectively.
- Apply control flows (if statements, loops) to make decisions and repeat tasks in your programs.
- Handle errors gracefully using Python’s exception handling features.
- Import and use packages to extend Python’s functionality.
- Integrate your knowledge by developing a simple chat bot that responds to user input.

Our class is based on [1-1-Intro_to_Python.ipynb](<Module 1-Introduction to Python Fundamentals/1-1-Intro_to_Python.ipynb>).

### 1.1o. Object-Oriented Programming Basics (Optional)

A brief, optional follow-on session introducing Object-Oriented Programming (OOP) in Python, using a running `FirmYear`/Compustat-style example.

**Learning Outcomes**

By completing this session, you will be able to:

- Explain what Object-Oriented Programming is and why it is useful in AccFin research.
- Create and use **classes** and **objects**, including composing one class from another.
- Apply core OOP concepts: **attributes**, **methods**, and **encapsulation** (public/protected/private access, getters/setters, and the `@property` decorator).
- Distinguish instance-level from static (class-level) attributes and methods.
- Recognize **inheritance** and **polymorphism** through a simple `Security`/`Stock`/`Bond` example.

Our class is based on [1-2o-OOP Basics.ipynb](<Module 1-Introduction to Python Fundamentals/1-2o-OOP Basics.ipynb>).

[Back to ToC](#toc)

## 2. Handling Data and Descriptive Analysis with `pandas` <a name="section2"></a>

`pandas` is the most useful Python library for data analysis in our research. In this module, you will learn how to use `pandas` to handle data in tabular form. We will cover the fundamental operations needed to load data, explore it, clean it, and prepare it for further analysis, then move on to visualizing it with `matplotlib` and `seaborn`. By the end, you’ll have the skills to manage real-world datasets and apply `pandas` to replicate seminal papers in AccFin research.

**Prerequisite reading**

- Sloan, R. G. 1996. Do stock prices fully reflect information in accruals and cash flows about future earnings?. *The Accounting Review* 71(3): 289-315. ([link](https://www.jstor.org/stable/248290))
- Kothari, S. P., B. Schonberger, C. Wasley, and J. Xiao (2025). The first half-century of empirical capital markets research in accounting in pictures. *Review of Accounting Studies* 30: 3111-3176. ([link](https://doi.org/10.1007/s11142-025-09887-3))

**Learning Outcomes**

By completing this module, you will be able to:

- Create and explore *Series* and *DataFrames*, the two core data structures in `pandas`.
- Import and export datasets from common formats such as CSV and Stata.
- Inspect and summarize data using built-in functions.
- Select, filter, and slice data to focus on what matters, including boolean indexing and `.query()`.
- Clean and transform datasets by handling missing values, renaming columns, changing data types, and winsorizing/truncating outliers.
- Perform basic data analysis with sorting, grouping, and simple aggregations, including `groupby` transformations and `.shift()`.
- Append and merge datasets (one-to-one, one-to-many, and many-to-many merges), including linking Compustat to CRSP via the CCM link table.
- Apply `matplotlib` and `seaborn` to construct foundational plots (line, bar, histogram, scatter, KDE, boxplot, violin, ECDF, Q-Q) and customize elements such as axes, labels, legends, colors, and styles.
- Enhance clarity and impact of visualizations through effective use of color, scaling, and annotation.
- Integrate `pandas` workflows into Python projects replicating seminal academic papers.

Our class is based on [2-1-Pandas.ipynb](<Module 2-Handling Data and Descriptive Analysis with Pandas/2-1-Pandas.ipynb>) (completed version: [2-1_Pandas_Final.ipynb](<Module 2-Handling Data and Descriptive Analysis with Pandas/2-1_Pandas_Final.ipynb>)) and [2-2-Data Visualization.ipynb](<Module 2-Handling Data and Descriptive Analysis with Pandas/2-2-Data Visualization.ipynb>).

### 2.1e. Exercises

- [2-1e_winsor2.ipynb](<Module 2-Handling Data and Descriptive Analysis with Pandas/2-1e_winsor2.ipynb>): homework exercise — write a `winsorize_by_group()` function (replicating Stata's `winsor2` command) that winsorizes or truncates variables, optionally by group.
- [2-1e-Replicating_Sloan_1996_Final.ipynb](<Module 2-Handling Data and Descriptive Analysis with Pandas/2-1e-Replicating_Sloan_1996_Final.ipynb>): replicate Figure 2 of Sloan (1996) — construct accruals/cash-flow/earnings variables from a Compustat/CRSP-style panel, form annual accrual-decile portfolios, and plot the hedge-portfolio returns.
- [2-2e_Plotting_Kothari_et_al_2025_Final.ipynb](<Module 2-Handling Data and Descriptive Analysis with Pandas/2-2e_Plotting_Kothari_et_al_2025_Final.ipynb>): reproduce one of the annual CMRA plots from Kothari et al. (2025), combining the authors' shared data with macroeconomic series into a publication-style `matplotlib` chart.

[Back to ToC](#toc)

## 3. Data Collection <a name="section3"></a>

### 3.1. WRDS with Python

Access to high-quality financial and economic data is fundamental for empirical research in AccFin. The Wharton Research Data Services (WRDS) platform, which provides a gateway to a wide range of leading databases such as Compustat, CRSP and IBES, is the most commonly used data platform for AccFin empirical research. In this session, we will learn how to use the `wrds` Python package to connect programmatically to WRDS, query structured datasets, and efficiently download and manage data for analysis. The session emphasizes both the technical skills required for accessing large-scale databases and the research practices necessary to ensure data integrity, reproducibility, and efficiency in academic and applied settings.

**Prerequisite reading**

You can preview the [tutorial provided by WRDS](https://wrds-www.wharton.upenn.edu/pages/support/programming-wrds/programming-python/querying-wrds-data-python/).

**Learning Outcomes**

By the end of this class, you will be able to:

- Understand the role of WRDS as a central platform for accessing accounting and financial datasets.
- Establish a secure connection to WRDS using the `wrds` Python package.
- Query the dataset structure: list available libraries and tables, and inspect a table's column headers.
- Formulate and execute SQL queries within Python using `raw_sql()` to retrieve specific datasets from WRDS, including joins across Compustat and the CRSP-Compustat Merged (CCM) link table.
- Download and manage large datasets, including filtering, merging, and exporting for further analysis.
- Integrate WRDS data with Python workflows, preparing it for use in packages such as `pandas` and `statsmodels`.
- Apply best practices for reproducible research, including documenting queries and saving data pipelines.

Our class is based on [3-1_WRDS_with_Python_Final.ipynb](<Module 3-Data Collection/3-1_WRDS_with_Python_Final.ipynb>).

An accompanying exercise, [3-1e_Option_Volatility_Smirk.ipynb](<Module 3-Data Collection/3-1e_Option_Volatility_Smirk.ipynb>), applies these WRDS querying skills to OptionMetrics data to construct an implied-volatility smirk (in development).

### 3.2. Web Scraping

In modern AccFin research, valuable data is often "locked" inside company websites, regulatory documents, and other websites. While numerical datasets (CRSP, Compustat, WRDS) are well-structured and easy to query, textual and legal disclosures frequently require researchers to gather data directly from the web.

This session introduces students to web scraping in Python as a tool to collect, clean, and analyze information from online sources. Using the SEC Accounting and Auditing Enforcement Releases (AAER) archive as our central case study, you will learn how to extract structured datasets from unstructured web pages, handling the unique challenges of financial text.

The AAER example highlights both the opportunities (building novel datasets for empirical analysis) and responsibilities (respecting site terms, rate limits, and ethical research practices) that come with web scraping. By the end of the class, you will have practical skills for transforming online financial disclosures into research-ready data.

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

Our class is based on [3-2_Web_Scraping_Final.ipynb](<Module 3-Data Collection/3-2_Web_Scraping_Final.ipynb>).

### 3.3. Using LLMs for Research

Generative LLMs are increasingly used in accounting research for textual-analysis tasks that used to require either dictionary/bag-of-words methods or costly manual human coding — for example, classifying disclosure tone, extracting structured facts from filings, or detecting evasive "non-answers" in earnings call Q&As. This session introduces the Python client libraries for two major generative LLM providers — OpenAI and Google Gemini — covering the mechanics you need before using an LLM as a research tool: sending prompts, getting structured (JSON) output, holding multi-turn conversations, and passing multimodal input such as images.

**Prerequisite reading**

de Kok, T. (2025). ChatGPT for textual analysis? How to use generative LLMs in accounting research. *Management Science* 71(9): 7888-7906. ([link](https://doi.org/10.1287/mnsc.2023.03253))

**Learning Outcomes**

By the end of this session, you will be able to:

- Set up API keys securely via a `.env` file for both OpenAI and Google Gemini.
- Send basic text prompts and read model output using both providers' Python clients.
- Request structured (JSON) output from a model using a defined schema (e.g., a Pydantic model).
- Hold a multi-turn conversation (chat) with an LLM.
- Pass images as multimodal input alongside text prompts.

Our class is based on [3-3_LLM_API_Final.ipynb](<Module 3-Data Collection/3-3_LLM_API_Final.ipynb>).

An optional follow-on exercise, [3-3o_Identifying_Images.ipynb](<Module 3-Data Collection/3-3o_Identifying_Images.ipynb>), applies these skills to a real annual report: extracting embedded photographs from a PDF, captioning each with Gemini, and summarizing the most common visual themes — motivated by Obaid, N., and K. Pukthuanthong (2022). Alt-text: Photo pessimism in newspaper articles and stock returns. *Journal of Financial Economics* 144(3): 903-925. ([link](https://doi.org/10.1016/j.jfineco.2021.06.002))

Two further exercises apply LLM-based textual analysis to accounting-research settings (in development):

- [3-3e-1_Detecting_GenAI_Text.ipynb](<Module 3-Data Collection/3-3e-1_Detecting_GenAI_Text.ipynb>)
- [3-3e-2_No_Answer_in_CC.ipynb](<Module 3-Data Collection/3-3e-2_No_Answer_in_CC.ipynb>) — detecting evasive "non-answers" in earnings conference calls, the case study featured in de Kok (2025).

### 3.4o. Using the SEC EDGAR API (Optional)

The U.S. Securities and Exchange Commission's (SEC) EDGAR database is a critical resource for financial and accounting research, providing open access to corporate filings such as 10-K/Qs, 8-Ks, and proxy statements. This optional session introduces the `secedgar` Python package, which provides a convenient interface to the SEC EDGAR API.

**Learning Outcomes**

By the end of this class, you will be able to:

- Explain the role of SEC EDGAR in financial markets and academic research.
- Install and configure `secedgar` to access SEC filings through the EDGAR API.
- Retrieve corporate filings programmatically, including annual reports (10-K), quarterly reports (10-Q), and event-driven filings (8-K), by company CIK.
- Automate large-scale data collection, including batch downloads across firms and time periods.
- Organize and manage raw filings for downstream textual analysis.

Our class is based on [3-4o_SEC_API.ipynb](<Module 3-Data Collection/3-4o_SEC_API.ipynb>).

### 3.5o. Using the Google Maps API (Optional)

Many datasets in AccFin research include a street address somewhere — a corporate headquarters, an audit office, a plant. Once that address is geocoded into latitude/longitude, geography becomes a source of research variables in its own right. This optional session covers Google's Python clients for the Google Maps Platform — `googlemaps` for geocoding, and the `google-maps-routing`/`google-maps-places` clients for directions, distances, and place search.

**Prerequisite reading**

- Ma, S., et al. (2024). Auditor office locations and audit quality. *The Accounting Review* 99(6). ([link](https://doi.org/10.2308/TAR-2021-0862))
- Chen, X., et al. (2022). Sunshine and managerial sentiment. *The Accounting Review* 97(4). ([link](https://doi.org/10.2308/TAR-2020-0215))

**Learning Outcomes**

By the end of this session, you will be able to:

- Geocode an address to latitude/longitude, and reverse-geocode coordinates back to an address.
- Compute travel routes, distances, and durations between locations using the Routes API.
- Search for nearby places and retrieve place details using the Places API.

Our class is based on [3-5o_Google_Map_API.ipynb](<Module 3-Data Collection/3-5o_Google_Map_API.ipynb>).

[Back to ToC](#toc)

## 4. Natural Language Processing <a name="section4"></a>

AccFin research nowadays is no longer limited to numerical disclosures and structual data. Textual data — such as Management Discussion & Analysis (MD&A) sections of 10-K filings, risk factor disclosures (RFD), and earnings call transcripts — provides rich information about firms’ strategies, risks, and performance, which provides many research opportunities.

This module introduces you to Natural Language Processing (NLP) in Python, moving from simple pattern-matching to a large language model built specifically for finance:

- Regular expressions (Regex) and the `textstat` package: for identifying, extracting, and cleaning patterns in text, and for computing readability metrics.
- Dictionary-based textual analysis: scoring text with the Loughran-McDonald word lists, the standard "bag-of-words" approach in AccFin research.
- Vectorizing text (bag-of-words, TF-IDF, n-grams) with `scikit-learn`, and visualizing term frequencies as word clouds.
- **FinBERT**: a large language model pretrained on financial text (10-Ks, 10-Qs, analyst reports, earnings calls) that you'll use to classify sentiment, and fine-tune on your own labeled data.

By the end of the module, you will have the skills to replicate influential textual-analysis studies in AccFin and apply modern NLP tools — from a handful of keywords to a domain-specific LLM — to your own research.

**Prerequisite reading**

- Section 3.3 of [Teoh (2018)](https://doi.org/10.1016/j.aos.2018.03.008)
- Merkley, K. J. (2014). Narrative disclosure and earnings performance: Evidence from R&D disclosures. *The Accounting Review* 89(2): 725-757. ([link](https://doi.org/10.2308/accr-50649))
- Huang, A. H., H. Wang, and Y. Yang (2023). FinBERT: A large language model for extracting information from financial text. *Contemporary Accounting Research* 40(2): 806-841. ([link](https://doi.org/10.1111/1911-3846.12832))

You can also watch [the video by Corey Schafer (53 mins)](https://youtu.be/K8L6KVGG-7o?si=H83lHipbbrHELfXD) to comprehensively understand the concept of Regex in python before our class.

**Learning Outcomes**

By the end of this module, you will be able to:

- Understand the role of textual analysis in AccFin research, particularly how narrative disclosures affect investors, regulators, and other stakeholders.
- Use Python’s `re` package to identify patterns (financial terms, footnotes, forward-looking statements) and clean raw disclosures by removing tables, formatting artifacts, and boilerplate text.
- Apply the `textstat` package to compute readability measures (e.g., Fog Index, Flesch Reading Ease, Dale-Chall) and interpret their implications for disclosure transparency.
- Score text against the Loughran-McDonald dictionary to measure tone, uncertainty, and complexity, and build a reproducible pipeline that ingests a collection of 10-K text files and outputs a structured dataset.
- Represent text numerically with `scikit-learn`'s `CountVectorizer` and `TfidfVectorizer` (bag-of-words, TF-IDF, n-grams), and visualize term importance with word clouds.
- Explain, at a conceptual level, what distinguishes a domain-pretrained large language model (FinBERT) from dictionary- and classic-machine-learning approaches to textual analysis, and why that distinction matters for accuracy on financial text.
- Use a pretrained FinBERT model to classify the sentiment (and ESG content) of financial text, and aggregate sentence-level output into document-level measures (e.g., earnings-call tone).
- Fine-tune FinBERT on a small, custom-labeled dataset, and critically evaluate the trade-offs (accuracy, cost, interpretability) between dictionary, classic ML, and LLM-based textual analysis.

Our class is based on:

- [4-1_NLP_Basics_and_Regex_Final.ipynb](<Module 4-Natural Language Processing/4-1_NLP_Basics_and_Regex_Final.ipynb>) and [4-1o_textstat.ipynb](<Module 4-Natural Language Processing/4-1o_textstat.ipynb>) (optional)
- [4-2_Dictionary_Based_Textual_Analysis_Final.ipynb](<Module 4-Natural Language Processing/4-2_Dictionary_Based_Textual_Analysis_Final.ipynb>)
- [4-3_Text_Vectorization_and_WordClouds_Final.ipynb](<Module 4-Natural Language Processing/4-3_Text_Vectorization_and_WordClouds_Final.ipynb>)
- [4-4_FinBERT_Sentiment_Final.ipynb](<Module 4-Natural Language Processing/4-4_FinBERT_Sentiment_Final.ipynb>) and [4-4o_FinBERT_Finetuning.ipynb](<Module 4-Natural Language Processing/4-4o_FinBERT_Finetuning.ipynb>) (optional)

[Back to ToC](#toc)

## 5. Machine Learning <a name="section5"></a>

Machine learning has become a core empirical tool in AccFin research: tree ensembles and other flexible models now routinely outperform traditional linear benchmarks at prediction tasks such as forecasting earnings, detecting misstatements, and assessing credit risk. This module builds up from classical statistical inference to modern gradient-boosted trees, replicating three recent AccFin papers along the way — a classification task, a regression/forecasting task, and an explainability exercise that opens up what the model actually learned.

**Prerequisite reading**

- Chen, X., Y. H. (T.) Cho, Y. Dou, and B. Lev (2022). Predicting future earnings changes using machine learning and detailed financial data. *Journal of Accounting Research* 60(2): 467-515.
- Chattopadhyay, A., B. Fang, and P. Mohanram (2025). Machine learning for earnings forecasting - US and international evidence. Working paper. ([link](https://dx.doi.org/10.2139/ssrn.5941658))
- Parker, C. (A.) Z., L. Jiang, S. Cho, and M. A. Vasarhelyi (2025). Predicting material misstatements using machine learning. *The Accounting Review* 100(6): 225-262.

**Learning Outcomes**

By the end of this module, you will be able to:

- Frame a prediction problem as either a binary classification task or a continuous forecasting (regression) task.
- Engineer a wide set of financial-statement predictors (current value, lagged value, percentage change) without hand-picking a small subset, and explain why panel data needs a **chronological** (not random) train/validation/test split.
- Fit and evaluate a linear benchmark (logistic regression / regularized regression) alongside `xgboost` models, tuning the latter with a validation set and early stopping.
- Evaluate classification models with ROC-AUC and ROC curves, and forecasting models with price-scaled MAFE, RMSE, and MDAFE.
- Read a gain-based feature-importance plot, and understand its limitations.
- Use `shap.TreeExplainer` to compute SHAP values for an XGBoost model, and read SHAP bar, beeswarm, dependence, and waterfall plots to understand which features drive individual predictions and in which direction.
- Critically interpret machine-learning output as an attention-directing tool rather than evidence of causation.

### 5.0o. Regression and Statistical Testing Primer (Optional)

An optional refresher on classical statistical inference before the machine-learning sessions: one-sample, independent-samples, and paired t-tests with `scipy.stats`, and linear regression with fixed effects and clustering using `FixedEffectModelPyHDFE`, live-coded through to logistic regression.

Our class is based on [5-0o_Regression.ipynb](<Module 5-Machine Learning/5-0o_Regression.ipynb>).

### 5.1. Classification with XGBoost: Predicting the Direction of Earnings Changes

Following Chen et al. (2022), this class frames the direction of next-year earnings changes as a binary classification problem, engineers a wide set of Compustat-based predictors, and benchmarks a "kitchen sink" logistic regression against `xgboost.XGBClassifier`.

Our class is based on [5-1_Classification.ipynb](<Module 5-Machine Learning/5-1_Classification.ipynb>).

### 5.2. Forecasting Continuous Earnings with XGBoost

Following Chattopadhyay et al. (2025), this class reuses 5-1's data and feature pipeline but predicts next-year EPS directly (a regression task), benchmarking a naive random-walk forecast and a regularized (Ridge) regression against an `xgboost.XGBRegressor` fit with a Huber loss.

Our class is based on [5-2_Earnings_Forecasting.ipynb](<Module 5-Machine Learning/5-2_Earnings_Forecasting.ipynb>).

### 5.3o. Explainable AI: Using SHAP to Understand an XGBoost Model (Optional)

Following Parker et al. (2025), this optional class picks up the classification model from 5-1 and applies SHAP (SHapley Additive exPlanations) to understand which predictors drive it and how — going beyond a single gain-based importance score to directional, per-observation explanations.

Our class is based on [5-3o_Explainable_AI.ipynb](<Module 5-Machine Learning/5-3o_Explainable_AI.ipynb>).

[Back to ToC](#toc)
