Module 3: Data Collection

[Back to main syllabus](../README.md)

Empirical AccFin research relies its data. This module covers the three ways researchers get it into Python:

* querying the structured databases on **WRDS** (Compustat, CRSP, IBES, OptionMetrics),
* **scraping** disclosures that are only available as web pages, and
* calling **third-party APIs** (SEC EDGAR, Google Maps) for filings and geographic data.

Each session is built around a real research task: constructing an option-implied crash-risk measure, building a dataset of SEC enforcement actions, geocoding firm addresses.

## 3.1. Accessing WRDS with Python

Access to high-quality financial and economic data is fundamental for empirical research in AccFin. The Wharton Research Data Services (WRDS) platform, which provides a gateway to a wide range of leading databases such as Compustat, CRSP and IBES, is the most commonly used data platform for AccFin empirical research. In this session, we will learn how to use the `wrds` Python package to connect programmatically to WRDS, query structured datasets, and efficiently download and manage data for analysis. The session emphasizes both the technical skills required for accessing large-scale databases and the research practices necessary to ensure data integrity, reproducibility, and efficiency in academic and applied settings.

**Prerequisite reading**

- You can preview the [tutorial provided by WRDS](https://wrds-www.wharton.upenn.edu/pages/support/programming-wrds/programming-python/querying-wrds-data-python/).
- Kim, J. B., Li, L., Lu, L. Y., & Yu, Y. (2016). Financial statement comparability and expected crash risk. *Journal of Accounting and Economics* 61(2-3): 294-312. ([link](https://doi.org/10.1016/j.jacceco.2015.12.003))

**Learning Outcomes**

By the end of this class, you will be able to:

- Understand the role of WRDS as a central platform for accessing accounting and financial datasets.
- Establish a secure connection to WRDS using the `wrds` Python package, including creating a `.pgpass` file for password authentication.
- Query the dataset structure: list available libraries and tables, and inspect a table's column headers.
- Formulate and execute SQL queries within Python using `raw_sql()` to retrieve specific datasets, including joins across Compustat and the CRSP-Compustat Merged (CCM) link table.
- Download and manage large datasets, including filtering, merging, and exporting to Stata or CSV.
- Integrate WRDS data with Python workflows, preparing it for use in packages such as `pandas` and `statsmodels`.
- Apply best practices for reproducible research, including documenting queries and saving data pipelines.

Our class is based on [3-1-WRDS_with_Python-Final.ipynb](3-1-WRDS_with_Python-Final.ipynb).

### 3.1e. Exercise: Building the Option Volatility Smirk from OptionMetrics

This exercise builds a firm-year panel of the option-implied volatility smirk from scratch, using the WRDS querying skills from 3.1. Following [Kim, Li, Lu and Yu (2016)](https://doi.org/10.1016/j.jacceco.2015.12.003), it aggregates OptionMetrics' daily option-price files server-side in SQL to get the open-interest-weighted implied volatility of at-the-money calls and out-of-the-money puts, caching each year to Parquet, linking identifiers across OptionMetrics, CRSP and Compustat with range joins on validity dates, building the accounting controls, and collapsing the daily smirk into a firm-year measure of expected crash risk.

**Prerequisite reading**

- Appendix B of Kim, J. B., Li, L., Lu, L. Y., & Yu, Y. (2016). Financial statement comparability and expected crash risk. *Journal of Accounting and Economics* 61(2-3): 294-312. ([link](https://doi.org/10.1016/j.jacceco.2015.12.003))

**Learning Outcomes**

- Aggregating a very large table server-side in SQL, so that only the summarised rows travel over the network.
- Looping over year-partitioned WRDS tables and caching each year's result to disk.
- Linking identifiers across three databases (OptionMetrics, CRSP, Compustat) with range joins on validity dates.
- Collapsing daily data to a firm-year panel over a custom event window, without blowing up memory.

Our class is based on [3-1e-Option_Volatility_Smirk-Final.ipynb](3-1e-Option_Volatility_Smirk-Final.ipynb).

## 3.2. Web Scraping

In modern AccFin research, valuable data is often "locked" inside company websites, regulatory documents, and other websites. While numerical datasets (CRSP, Compustat, WRDS) are well-structured and easy to query, textual and legal disclosures frequently require researchers to gather data directly from the web. This session introduces web scraping in Python as a tool to collect, clean, and analyze information from online sources. Working through a single web page, you will learn the core `requests` + `BeautifulSoup` workflow — fetching HTML, locating elements with `find()`/`find_all()` and CSS selectors, extracting text and tag attributes, and navigating the parse tree — together with the responsibilities (site terms, rate limits, ethical research practices) that come with automated data collection. The hands-on exercise in 3.2e then applies these skills to a real dataset.

**Prerequisite reading**

- Karpoff, J. M., Koester, A., Lee, D. S., & Martin, G. S. (2017). Proxies and databases in financial misconduct research. *The Accounting Review* 92(6): 129-163. ([link](https://doi.org/10.2308/accr-51766))

**Learning Outcomes**

By the end of this session, you will be able to:

- Understand the role of web scraping in AccFin research, and identify cases where scraping is necessary to build novel datasets.
- Use `requests` to fetch a web page and `BeautifulSoup` to parse its HTML.
- Locate elements with `find()` / `find_all()` (by tag, by attribute/`class`, by matching string), nest these calls to drill into the tree, and use CSS selectors via `select()`.
- Extract content with `.get_text()` / `.text` and read tag attributes with `.attrs` (e.g., pulling `href` values out of links).
- Navigate the parse tree using parent, child, descendant, and sibling relationships.
- Practice responsible scraping by setting custom User-Agents, respecting rate limits and `robots.txt`, and following ethical/legal guidelines for automated data collection.

Our class is based on [3-2-Web_Scraping-Final.ipynb](3-2-Web_Scraping-Final.ipynb).

### 3.2e. Exercise: Parsing SEC AAER Cases into a Dataset

This exercise applies the scraping skills from 3.2 to a real research task: building a structured dataset of the SEC's Accounting and Auditing Enforcement Releases (AAER) from the enforcement archive's web pages. It starts from a single results page — locating the release table, walking its rows, and turning the cells into a `pandas` DataFrame — then cleans the raw text into research variables: parsing dates with `pd.to_datetime`, splitting the respondents field into a list of defendants, and using regular expressions to extract the release and AAER numbers. The final step wraps the whole pipeline into a reusable `Extract_AAER(page_num)` function that can be looped over the archive's pagination to collect the full history.

**Prerequisite reading**

- Karpoff, J. M., Koester, A., Lee, D. S., & Martin, G. S. (2017). Proxies and databases in financial misconduct research. *The Accounting Review* 92(6): 129-163. ([link](https://doi.org/10.2308/accr-51766))

**Learning Outcomes**

- Parsing an HTML table into a `pandas` DataFrame by iterating over `<tr>`/`<td>` elements.
- Cleaning scraped text into structured variables: parsing mixed-format dates, splitting multi-value fields, and extracting patterns with regular expressions.
- Refactoring an ad-hoc scraping script into a parameterised function that can be run page by page over a paginated archive.

Our class is based on [3-2e-Parsing_AAER_Cases-Final.ipynb](3-2e-Parsing_AAER_Cases-Final.ipynb).

## 3.3o. Using the Google Maps API (Optional)

Many datasets in AccFin research include a street address somewhere — a corporate headquarters, an audit office, a plant. Once that address is geocoded into latitude/longitude, geography becomes a source of research variables in its own right. This optional session covers Google's Python clients for the Google Maps Platform — `googlemaps` for geocoding, and the `google-maps-routing` / `google-maps-places` clients for directions, distances, and place search.

**Optional reading**

- Chen, C., Chen, Y., Pittman, J. A., Podolski, E. J., & Veeraraghavan, M. (2022). Emotions and managerial judgment: Evidence from sunshine exposure. *The Accounting Review* 97(3): 179-203. ([link](https://doi.org/10.2308/TAR-2020-0215))
- Ma, T., Wan, C., Wang, Y., & Zhao, Y. (2024). Individual auditor turnover and audit quality—Large sample evidence from US audit offices. *The Accounting Review* 99(6): 297-324. ([link](https://doi.org/10.2308/TAR-2021-0862))

**Learning Outcomes**

By the end of this session, you will be able to:

- Geocode an address to latitude/longitude, and reverse-geocode coordinates back to an address.
- Compute travel routes, distances, and durations between locations using the Routes API.
- Search for nearby places and retrieve place details using the Places API (New).

Our class is based on [3-3o-Google_Map_API.ipynb](3-3o-Google_Map_API.ipynb).

## 3.4o. Using the SEC EDGAR API (Optional)

The U.S. Securities and Exchange Commission’s (SEC) EDGAR database is a critical resource for financial and accounting research, providing open access to corporate filings such as 10-K/Qs, 8-Ks, and proxy statements. However, navigating and retrieving this information manually can be time-consuming and inefficient. This session introduces you to `secedgar` Python package, which provides a convenient interface to the SEC EDGAR API services. In this optional module, you will learn how to automate the process of searching and downloading regulatory filings to build structured datasets for empirical analysis. The class emphasizes both technical implementation and research applications, highlighting how SEC filings can be leveraged for corporate disclosure studies, textual analysis, and financial statement research.

**Learning Outcomes**

By the end of this class, you will be able to:

- Explain the role of SEC EDGAR in financial markets and academic research.
- Install and configure `secedgar` to access SEC filings through the EDGAR API.
- Look up company CIKs, and retrieve corporate filings programmatically, including annual reports (10-K), quarterly reports (10-Q), and event-driven filings (8-K).
- Automate large-scale data collection, including batch downloads across firms and time periods.
- Organize and manage raw filings for downstream textual analysis.

Our class is based on [3-4o-SEC_API.ipynb](3-4o-SEC_API.ipynb).

[Back to main syllabus](../README.md)
