# AFDEN Python Workship for Accounting and Finance Research
### Creator: <a href="https://www.unsw.edu.au/staff/leonard-leye-li" target="_blank">Leonard Leye Li</a> 
### Edition: *2025 Sep* 
---

**Welcome to AFDEN Python Workship for Accounting and Finance Research**

## 0. Python Environment Setup

Before our first session, please follow the steps below to set up the required Python environment on your computer.

The python version we use is 3.12, and the IDE I will use for demostration is VS Code. If you prefer other IDEs such as PyCharm or jupyter notebook, you are welcome to use the one you are familar with.

I set up the python environment using `uv`, which is fast and easy for begginers. If you have already known how to use `pip` or `conda` to set up your Python virtual environment, you can use your preferred method and ignore the following steps. Just make sure you have installed all the packages in [requirements file](./requirements.txt).

1. **Install `uv`**: See https://docs.astral.sh/uv/getting-started/installation/
    - If you are using Windows: open Command Prompt, type `winget install --id=astral-sh.uv  -e`
    - If you are using Mac OS: open Terminal, type `wget -qO- https://astral.sh/uv/install.sh | sh`
    - To check if `uv` is successfully installed, type `uv --version`
2. **Install VS Code** from https://code.visualstudio.com. In VS Code, Install the following Extensions (one the left column):
   - Data Wrangler
   - Jupyter
   - Python
3. Download this Github repository to your local disk.   
   - Click the  green "<> Code" button and click "Download ZIP".
   - Create a new folder on your computer and extra the ZIP file in that directory
   - Open the directory using VS Code (or your IDE). In Terminal, run `uv sync`.

## 1. Introduction to Python Fundamentals in Research
In this first module, we will quickly go through the Python Basics, from data types to control flows. This module is designed with beginners in mind. You will be introduced to the essential building blocks of Python, moving step by step from basic concepts to more practical applications. Along the way, you will practice coding through short examples and exercises. I will also share the functions that I frequently uesed in my own research such as list conprehension and lambda functions. By the end, you’ll put everything together in a fun project: building a simple chat bot.

**Learning Outcomes**

By completing this module, you will be able to:

- Understand Python’s core data types (integers, floats, strings, booleans) and how they are used.

- Work with collections such as lists and dictionaries to store and manage groups of data.

- Define and use functions to organize and reuse code effectively.

- Apply control flows (if statements, loops) to make decisions and repeat tasks in your programs.

- Handle errors gracefully using Python’s exception handling features.

- Import and use packages to extend Python’s functionality.

- Integrate your knowledge by developing a simple chat bot that responds to user input.

You can go through the [1-Intro to Python.ipynb](https://github.com/leonard67/AFDEN-Python-Workshop/blob/main/1-Intro%20to%20Python.ipynb) file before class.

## 2. Data Science with Pandas

`pandas` is the most useful Python library for data analysis in our research. In the second module, you will learn how to use `pandas` to handle data in tabular form. We will cover the fundamental operations needed to load data, explore it, clean it, and prepare it for further analysis. By the end, you’ll have the skills to manage real-world datasets and apply `pandas` to replicate a saminal paper.

**Learning Outcomes**

By completing this tutorial, you will be able to:

- Create and explore *Series* and *DataFrames*, the two core data structures in `pandas`.

- Import and export datasets from common formats such as CSV and Stata.

- Inspect and summarize data using built-in functions.

- Select, filter, and slice data to focus on what matters.

- Clean and transform datasets by handling missing values, renaming columns, and changing data types.

- Perform basic data analysis with sorting, grouping, and simple aggregations.

- Integrate pandas workflows into larger Python projects.

Our class will be based on the [2-Pandas.ipynb](https://github.com/leonard67/AFDEN-Python-Workshop/blob/main/2-Pandas.ipynb) file.

## 3. WRDS with Python and Textual Analysis

## 4. Empirical Methods in Python
