# Tokenization in Natural Language Processing (NLP)

## Overview

Tokenization is a fundamental step in Natural Language Processing (NLP) that involves breaking up text into smaller pieces called tokens. Tokens are often words, but they can also be phrases or other meaningful units. This document explores the concept of tokenization and addresses common challenges encountered during the process.

## Table of Contents
- [What is Tokenization?](#what-is-tokenization)
- [Basic Tokenization](#basic-tokenization)
- [Challenges in Tokenization](#challenges-in-tokenization)
  - [Non-Alphanumeric Characters](#non-alphanumeric-characters)
  - [Apostrophes](#apostrophes)
  - [Two-Word Entities](#two-word-entities)
  - [Compound Words](#compound-words)


## What is Tokenization?

Tokenization is the process of breaking down text into smaller units, typically words, that can be used for further analysis. Each of these smaller units is called a token.

**Example:**
Text: "Radhika saved the puppy"
Tokens: ['Radhika', 'saved', 'the', 'puppy']

```python

## Basic Tokenization

A simple way to tokenize text is to split it at spaces and punctuation marks. However, this approach can be too simplistic for more complex text.

**Example:**


## Basic Tokenization

A simple way to tokenize text is to split it at spaces and punctuation marks. However, this approach can be too simplistic for more complex text.

**Example:**

```python
import re

text = "Radhika saved the puppy"
tokens = re.findall(r'\b\w+\b', text)
print(tokens)

```
## Challenges in Tokenization

# Non-Alphanumeric Characters
Splitting text at all non-alphanumeric characters can help in tokenization, but it may not always be ideal.

**Example:**

```python

text = "Hello, world! It's a beautiful day."
tokens = re.findall(r'\b\w+\b', text)
print(tokens)
```

# Apostrophes
Handling apostrophes can be tricky as they can signify contractions or possessives.

**Example:**

```python
text = "It's Radhika's puppy."
tokens = re.findall(r"\b\w+(?:'\w+)?\b", text)
print(tokens)
```

# Two-Word Entities
Recognizing two-word entities, such as proper nouns or named entities, requires more advanced techniques like Named Entity Recognition (NER).

**Example:**

```python
import spacy

nlp = spacy.load("en_core_web_sm")
text = "Radhika lives in New Delhi."
doc = nlp(text)
tokens = [token.text for token in doc]
print(tokens)

```

# Compound Words
Compound words, especially in languages like Sanskrit and German, need careful handling to preserve their meaning.

**Example:**

```python
text = "Bhagavad-gita"
tokens = re.findall(r'\b\w+\b', text)
print(tokens)
```
