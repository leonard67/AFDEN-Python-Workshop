# 1. Data Collection

## Web Scraping:
- `requests`
- `BeautifulSoup`

## Saving data:
- `pickle`
- .json
- .csv

# 2. Data Cleaning

## 2.1. Format 1: Corpus

Corpus is a collection of texts.

- Just using `pandas.DataFrame`.
- Each row is an observation (document, transcript, etc.), having the value of the text.

## 2.2. Format 2: Document-Term Matrix

1. Clean Text: Remove excess, unnecessary parts of the text;
    - Remove *punctuation*
    - Remove numbers
    - Lowercase letters
    - using `re`

2. Tokenization: Split the text into smaller pieces;
    - Can be by word, sentences, or two/three words (bi-grams / tri-grams)
    - Remove *stop words*
    - Stemming / Lemmatization

**Bag of words model**: simple format of a list of tokens that ignore order.

3. Document-Term Matrix: Put the tokens into a matrix
    - Each row is a different observation (document, transcript, etc.)
    - Each column is a different term (words, sentences, or n-grams)
    - The values are word counts.
    - Example: [Loughran-McDonald 10X Document Dictionaries](https://sraf.nd.edu/sec-edgar-data/10x-document-dictionaries/)
    - 
