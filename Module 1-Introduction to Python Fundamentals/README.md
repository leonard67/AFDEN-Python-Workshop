# Module 1: Introduction to Python Fundamentals

[Back to main syllabus](../README.md)

In this first module, we will quickly go through the Python Basics, from data types to control flows. This module is designed with beginners in mind. You will be introduced to the essential building blocks of Python, moving step by step from basic concepts to more practical applications. Along the way, you will practice coding through short examples and exercises. I will also share the functions that I frequently uesed in my own research such as list conprehension and lambda functions. By the end, you’ll put everything together in a fun project: building a simple chat bot.

## 1.1 Introduction to Python

**Prerequisite reading**

You can go through the [1-1-Intro_to_Python.ipynb](1-1-Intro_to_Python.ipynb) file before class.

**Learning Outcomes**

By completing this module, you will be able to:

- Understand Python’s core data types (integers, floats, strings, booleans) and how they are used.
- Work with collections such as lists and dictionaries to store and manage groups of data.
- Define and use functions to organize and reuse code effectively.
- Apply control flows (if statements, loops) to make decisions and repeat tasks in your programs.
- Handle errors gracefully using Python’s exception handling features.
- Import and use packages to extend Python’s functionality.
- Integrate your knowledge by developing a simple chat bot that responds to user input.

Our class is based on [1-1-Intro_to_Python.ipynb](1-1-Intro_to_Python.ipynb).

## 1.2. Opening Files: the `with` Context Manager

Research work involves more than data living inside Python's memory — it means reading data from files (a `.txt` file of a 10-K filing, a `.csv` of Compustat data) and writing results back to disk. This session introduces Python's `with` statement (the **context manager**) as the safe, Pythonic way to open and close files, contrasting it with the error-prone manual `open()`/`close()` pattern. You will practice reading and writing text files, choosing the correct file mode, and applying these skills to a research example — loading an R&D keyword list used to measure innovation disclosure in 10-Ks.

**Learning Outcomes**

By completing this session, you will be able to:

- Explain why files must be explicitly closed, and the risks of forgetting (lost writes, locked files) — especially when an error interrupts execution before `close()` is reached.
- Use the `with` statement to open a file safely, so it is closed automatically even if the code inside the block raises an error.
- Choose the correct file mode (`"r"`, `"w"`, `"a"`, `"x"`, and their binary variants) for a given task, and recognize the destructive effect of `"w"` mode on an existing file.
- Read a file back with `.read()`, `.readlines()`, or by iterating line by line, and choose the right method based on file size.
- Open two files in a single `with` statement to read from one and write to another.
- Recognize the `with` pattern beyond files — e.g., WRDS database connections, Excel writers, network sessions — and apply the rule of thumb: if a library gives you something you are supposed to `close()`, open it with `with`.

Our class is based on [1-2-Context_Manager.ipynb](1-2-Context_Manager.ipynb).

## 1.3o. Object-Oriented Programming Basics (Optional)

A brief, optional follow-on session introducing Object-Oriented Programming (OOP) in Python, using a running `FirmYear`/Compustat-style example.

**Learning Outcomes**

By completing this session, you will be able to:

- Explain what Object-Oriented Programming is and why it is useful in AccFin research.
- Create and use **classes** and **objects**, including composing one class from another.
- Apply core OOP concepts: **attributes**, **methods**, and **encapsulation** (public/protected/private access, getters/setters, and the `@property` decorator).
- Distinguish instance-level from static (class-level) attributes and methods.
- Recognize **inheritance** and **polymorphism** through a simple example.

Our class is based on [1-3o_OOP_Basics.ipynb](<1-3o_OOP Basics.ipynb>).

[Back to main syllabus](../README.md)
