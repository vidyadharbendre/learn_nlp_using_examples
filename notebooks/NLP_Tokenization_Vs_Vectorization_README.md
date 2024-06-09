# Understanding Tokenization and Vectorization in NLP

## Overview

This repository aims to provide a clear understanding of two fundamental concepts in Natural Language Processing (NLP): tokenization and vectorization. These steps are crucial for preparing text data for machine learning models.

## Table of Contents
- [Tokenization](#tokenization)
  - [Unigram Tokenization](#unigram-tokenization)
  - [Bigram Tokenization](#bigram-tokenization)
  - [N-gram Tokenization](#n-gram-tokenization)
  - [Example of Tokenization](#example-of-tokenization)
- [Vectorization](#vectorization)
  - [Count Vectorization](#count-vectorization)
  - [TF-IDF Vectorization](#tf-idf-vectorization)
  - [One-Hot Encoding](#one-hot-encoding)
  - [Word Embeddings](#word-embeddings)
  - [Example of Vectorization](#example-of-vectorization)
- [Usage](#usage)
- [Contributing](#contributing)
- [License](#license)

## Tokenization

Tokenization is the process of breaking down text into smaller units called tokens. These tokens can be words, subwords, or characters. Tokenization helps in converting the text into a format that can be more easily analyzed.

### Unigram Tokenization

Unigram tokenization involves breaking text into individual words.

**Example:**
"I love machine learning." -> ['I', 'love', 'machine', 'learning', '.']

### Bigram Tokenization

Bigram tokenization involves breaking text into pairs of consecutive words.

**Example:**
"I love machine learning." -> ['I love', 'love machine', 'machine learning', 'learning .']


### N-gram Tokenization

N-gram tokenization involves breaking text into sequences of N consecutive words.

**Example:**
For N=3: "I love machine learning." -> ['I love machine', 'love machine learning', 'machine learning .']


### Example of Tokenization

Given the text:
"I love machine learning."


**Unigram Tokenization:**
```python
import nltk

nltk.download('punkt')
text = "I love machine learning."
tokens = nltk.word_tokenize(text)
print(tokens)
```

**Bigram Tokenization:**
```python
from nltk.util import bigrams

text = "I love machine learning."
tokens = list(bigrams(nltk.word_tokenize(text)))
print(tokens)
```

**Ngram Tokenization:**
```python
from nltk.util import ngrams

text = "I love machine learning."
tokens = list(ngrams(nltk.word_tokenize(text), 3))
print(tokens)
```

## Vectorization

Vectorization is the process of converting text tokens into numerical vectors. These vectors are used as features for machine learning models. Common methods of vectorization include Count Vectorization, TF-IDF, One-Hot Encoding, and Word Embeddings.

### Count Vectorization

Count Vectorization converts text into a matrix of token counts.

**Example:**

```python
from sklearn.feature_extraction.text import CountVectorizer

text = ["I love machine learning."]
vectorizer = CountVectorizer()
X_bow = vectorizer.fit_transform(text)
print("Count Vectorization:\n", X_bow.toarray())

```
**TF-IDF Vectorization:**
TF-IDF (Term Frequency-Inverse Document Frequency) Vectorization weighs terms based on their importance in a document relative to a corpus.

**Example:**
```python
from sklearn.feature_extraction.text import TfidfVectorizer

text = ["I love machine learning."]
vectorizer = TfidfVectorizer()
X_tfidf = vectorizer.fit_transform(text)
print("TF-IDF Vectorization:\n", X_tfidf.toarray())
```

**One-Hot Encoding:**
One-Hot Encoding represents text tokens as binary vectors, where each vector has a single high (1) value for the corresponding token and low (0) values elsewhere.

**Example:**
```python

from sklearn.preprocessing import OneHotEncoder
import numpy as np

text = ["I love machine learning."]
vectorizer = CountVectorizer()
X = vectorizer.fit_transform(text)
onehot_encoder = OneHotEncoder(sparse=False)
X_onehot = onehot_encoder.fit_transform(X.toarray())
print("One-Hot Encoding:\n", X_onehot)

```
**Word Embedings:**
Word Embeddings represent words as dense vectors in a continuous vector space, capturing semantic relationships between words. Popular methods include Word2Vec, GloVe, and fastText.
**Example using GloVe**
```python

from gensim.models import KeyedVectors

# Assuming you have the GloVe vectors file glove.6B.100d.txt downloaded and saved
word_vectors = KeyedVectors.load_word2vec_format('glove.6B.100d.txt', binary=False, no_header=True)
vector = word_vectors['love']
print("Word Embedding for 'love':\n", vector)

```

**Example using GloVe:**
```python
from gensim.models import KeyedVectors

# Assuming you have the GloVe vectors file glove.6B.100d.txt downloaded and saved
word_vectors = KeyedVectors.load_word2vec_format('glove.6B.100d.txt', binary=False, no_header=True)
vector = word_vectors['love']
print("Word Embedding for 'love':\n", vector)

```