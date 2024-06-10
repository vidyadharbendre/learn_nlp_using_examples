# Text Normalization in NLP

## Overview

Text normalization is a critical preprocessing step in Natural Language Processing (NLP) that involves transforming text into a standard, consistent format. This process includes various tasks such as removing stop words, converting text to lower case, stemming, and lemmatization. These steps help in reducing the complexity of the text data and improving the performance of NLP models.

## Table of Contents
- [What is Text Normalization?](#what-is-text-normalization)
- [Common Text Normalization Techniques](#common-text-normalization-techniques)
  - [Removing Stop Words](#removing-stop-words)
  - [Lowering the Case](#lowering-the-case)
  - [Stemming](#stemming)
  - [Lemmatization](#lemmatization)
- [Code Examples](#code-examples)
  - [Removing Stop Words](#removing-stop-words-example)
  - [Lowering the Case](#lowering-the-case-example)
  - [Stemming](#stemming-example)
  - [Lemmatization](#lemmatization-example)


## What is Text Normalization?

Text normalization involves converting text into a standard format, making it easier to process and analyze. The primary goals of text normalization are to reduce the vocabulary size and to ensure consistency in the text data, which in turn helps improve the efficiency and accuracy of NLP models.

## Common Text Normalization Techniques

### Removing Stop Words

Stop words are common words that usually do not contribute to the meaning of a sentence and can be removed to reduce the size of the text data. Examples include "is", "and", "the", etc.

### Lowering the Case

Converting all characters in the text to lower case helps in maintaining consistency and avoiding case sensitivity issues.

### Stemming

Stemming involves reducing words to their base or root form. For example, "running" and "runner" might be reduced to "run".

### Lemmatization

Lemmatization is similar to stemming, but it reduces words to their base or dictionary form, considering the context. For example, "better" is reduced to "good".

## Code Examples

### Removing Stop Words Example

```python
from nltk.corpus import stopwords
from nltk.tokenize import word_tokenize

# Sample text
text = "This is an example sentence demonstrating the removal of stop words."

# Tokenize the text
words = word_tokenize(text)

# Remove stop words
stop_words = set(stopwords.words('english'))
filtered_words = [word for word in words if word.lower() not in stop_words]

print(filtered_words)

```
# output
['example', 'sentence', 'demonstrating', 'removal', 'stop', 'words', '.']

### Lowering the Case Example
```python

# Sample text
text = "This is an Example Sentence Demonstrating Lowering the Case."

# Convert text to lower case
lower_case_text = text.lower()

print(lower_case_text)
```
# output
"this is an example sentence demonstrating lowering the case."

### Stemming Example
```python
from nltk.stem import PorterStemmer
from nltk.tokenize import word_tokenize

# Sample text
text = "running runners run easily"

# Initialize the PorterStemmer
stemmer = PorterStemmer()

# Tokenize and stem the text
words = word_tokenize(text)
stemmed_words = [stemmer.stem(word) for word in words]

print(stemmed_words)

```
# output
['run', 'runner', 'run', 'easili']

### Lemmatization Example
```python
from nltk.stem import WordNetLemmatizer
from nltk.tokenize import word_tokenize
import nltk

# Ensure necessary resources are downloaded
nltk.download('wordnet')
nltk.download('omw-1.4')

# Sample text
text = "better best running"

# Initialize the WordNetLemmatizer
lemmatizer = WordNetLemmatizer()

# Tokenize and lemmatize the text
words = word_tokenize(text)
lemmatized_words = [lemmatizer.lemmatize(word) for word in words]

print(lemmatized_words)

```

# output
['better', 'best', 'running']
