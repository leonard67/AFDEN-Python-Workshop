# Module 4: Natural Language Processing

[Back to main syllabus](../README.md)

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

## 4.1. NLP Basics and Regular Expressions

This session introduces NLP in Python with a focus on **regular expressions** (the `re` module): patterns used to match, search, extract, and replace text. You will process unstructured disclosure text — identifying financial terms, footnotes, and forward-looking statements, and stripping tables, formatting artifacts, and boilerplate — and turn it into features that can be linked to financial and capital-market outcomes.

**Learning Outcomes**

By the end of this session, you will be able to:

- Understand the role of textual analysis in AccFin research, particularly how narrative disclosures affect investors, regulators, and other stakeholders.
- Use Python's `re` package with `re.findall()` and `re.sub()` to identify patterns (financial terms, footnotes, forward-looking statements) and clean raw disclosures.
- Build reproducible pipelines that ingest a collection of text files (e.g., 10-K sections), extract features, and output structured datasets.
- Critically evaluate the limitations of preprocessing methods and discuss best practices for textual analysis in academic work.

Our class is based on [4-1-NLP_Basics_and_Regex-Final.ipynb](4-1-NLP_Basics_and_Regex-Final.ipynb).

### 4.1o. Readability with `textstat` (Optional)

A short introduction to the `textstat` package: character/word/syllable/sentence counts, and the readability indices most cited in the disclosure literature (Gunning Fog, SMOG, Flesch Reading Ease, Flesch-Kincaid, Coleman-Liau, Dale-Chall), computed for single texts and across a corpus.

Our class is based on [4-1o-textstat.ipynb](4-1o-textstat.ipynb).

## 4.2. Dictionary-Based Textual Analysis

This session applies the standard "bag-of-words" approach: scoring disclosure text against curated word lists. Using the Loughran-McDonald master dictionary and a stop-word list, and the R&D keyword list from Merkley (2014), you build a reproducible pipeline that ingests a collection of 10-K text files, flags R&D-related sentences, and outputs a structured dataset of readability and tone (positive, negative, uncertainty, complexity) measures.

**Learning Outcomes**

By the end of this session, you will be able to:

- Load and use textual-analysis resources (Loughran-McDonald dictionary, generic stop words, keyword lists).
- Tokenize text into sentences and words with `nltk`, and flag sentences containing target phrases.
- Score text against the Loughran-McDonald dictionary to measure tone, uncertainty, and complexity.
- Compute readability of a specific disclosure passage, and assemble filing-level variables keyed to CIK and accession number.

Our class is based on [4-2-Dictionary_Based_Textual_Analysis-Final.ipynb](4-2-Dictionary_Based_Textual_Analysis-Final.ipynb).

## 4.3. Text Vectorization and Word Clouds

Dictionary methods only check whether specific words are present. This session builds the bag-of-words / document-term matrix properly — representing each piece of text as a vector of *all* its words — reusing the R&D-flagged sentences saved in 4.2.

**Learning Outcomes**

By the end of this session, you will be able to:

- Represent text numerically with `scikit-learn`'s `CountVectorizer` and `TfidfVectorizer` (bag-of-words, TF-IDF).
- Explain why TF-IDF reweights frequent-but-undistinctive words downward, and capture multi-word phrases with `ngram_range`.
- Visualize term importance as word clouds, from raw counts, TF-IDF weights, or raw text.
- Recognize the limitations of keyword-based extraction by comparing word clouds across filings.

Our class is based on [4-3-Text_Vectorization_and_WordClouds-Final.ipynb](4-3-Text_Vectorization_and_WordClouds-Final.ipynb).

## 4.4. FinBERT Sentiment

Dictionary counts and TF-IDF weights both treat text as a *bag* of words — order and context are discarded. **FinBERT** (Huang, Wang, and Yang 2023) is a large language model pretrained on 4.9 billion words of financial text that reads a sentence in context instead. This session uses an already fine-tuned FinBERT to classify sentiment, compares it against the Loughran-McDonald dictionary sentence by sentence, and aggregates sentence-level output into a document-level tone measure — applied to R&D disclosures and to real Tesla earnings-call transcripts.

**Learning Outcomes**

By the end of this session, you will be able to:

- Explain what distinguishes a domain-pretrained large language model (FinBERT) from dictionary- and classic-ML approaches, and why that matters for financial text.
- Load `yiyanghkust/finbert-tone` and classify the sentiment of financial sentences in batches with `transformers`.
- Compare FinBERT against a Loughran-McDonald rule, and interpret the disagreements.
- Aggregate sentence-level labels into a document-level *Tone* measure (share positive minus share negative), and apply it to an earnings-call transcript.

Our class is based on [4-4-FinBERT_Sentiment-Final.ipynb](4-4-FinBERT_Sentiment-Final.ipynb).

### 4.4o. Fine-Tuning FinBERT (Optional)

An optional, more advanced class that fine-tunes the *pretrained* FinBERT on a small labeled dataset (the Financial PhraseBank), following the FinBERT repository's own recipe. It replicates the paper's small-sample finding — a few hundred task-specific sentences is often enough — and quantifies what fine-tuning buys over an already fine-tuned model.

**Learning Outcomes**

- Tokenize a labeled dataset and wrap it as a Hugging Face `datasets.Dataset`.
- Fine-tune `BertForSequenceClassification` with the `transformers` `Trainer` API (learning rate, epochs, early evaluation).
- Evaluate a fine-tuned model on a held-out test set, and compare it against a zero-shot model.
- Weigh the trade-offs (accuracy, cost, interpretability) between dictionary, classic ML, and LLM-based textual analysis.

Our class is based on [4-4o-FinBERT_Finetuning.ipynb](4-4o-FinBERT_Finetuning.ipynb).

[Back to main syllabus](../README.md)
