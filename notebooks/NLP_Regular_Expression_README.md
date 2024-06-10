# Text Preprocessing with Regular Expressions (Regex)

Regular expressions (regex) are sequences of characters that define search patterns, primarily used for string matching and manipulation. In text preprocessing, regex can be used to clean and normalize text data by removing unwanted characters, extracting specific patterns, and more.

## Table of Contents
1. [Introduction to Regular Expressions](#introduction-to-regular-expressions)
2. [Installation](#installation)
3. [Basic Regex Operations](#basic-regex-operations)
    - [Pattern Matching](#pattern-matching)
    - [Replacing Patterns](#replacing-patterns)
    - [Splitting Strings](#splitting-strings)
4. [Text Preprocessing Examples](#text-preprocessing-examples)
    - [Removing Punctuation](#removing-punctuation)
    - [Removing Digits](#removing-digits)
    - [Extracting Email Addresses](#extracting-email-addresses)
    - [Normalizing Whitespace](#normalizing-whitespace)
5. [Conclusion](#conclusion)

## Introduction to Regular Expressions

Regular expressions are used to identify patterns in text. They are supported by most programming languages, including Python, and are very powerful for text processing tasks.

## Installation

In Python, the `re` module provides support for working with regular expressions. No additional installation is required as it is part of the standard library.

## Basic Regex Operations

### Pattern Matching

To search for patterns in text, use the `re.search` function.

```python
import re

text = "Hello, my name is Radhika."
pattern = r"Radhika"
match = re.search(pattern, text)

if match:
    print("Pattern found:", match.group())
else:
    print("Pattern not found")
```

### Replacing Patterns
To replace patterns in text, use the re.sub function.

```python

text = "Hello, my name is Radhika."
pattern = r"Radhika"
replacement = "John"
new_text = re.sub(pattern, replacement, text)
print(new_text)

```
### Splitting Strings
To split strings based on patterns, use the re.split function.

```python
text = "Hello, my name is Radhika."
pattern = r"\s+"  # Split by whitespace
tokens = re.split(pattern, text)
print(tokens)

```

## Text Preprocessing Examples
### Removing Punctuation
Use regex to remove punctuation from text.

```python
import re

text = "Hello, my name is Radhika!"
pattern = r"[^\w\s]"
clean_text = re.sub(pattern, "", text)
print(clean_text)
```
## Removing Digits
Use regex to remove digits from text.
```python
text = "I have 2 apples and 3 bananas."
pattern = r"\d"
clean_text = re.sub(pattern, "", text)
print(clean_text)

```

## Extracting Email Addresses
Use regex to extract email addresses from text.
```python

text = "Please contact us at support@example.com for further information."
pattern = r"\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Z|a-z]{2,}\b"
emails = re.findall(pattern, text)
print(emails)
```

## Normalizing Whitespace
Use regex to normalize whitespace by replacing multiple spaces with a single space.

```python
text = "This  is    an example  text."
pattern = r"\s+"
normalized_text = re.sub(pattern, " ", text).strip()
print(normalized_text)

```

## Conclusion
Regular expressions are a versatile tool for text preprocessing, allowing for complex pattern matching and manipulation. With regex, you can clean and prepare your text data efficiently, making it suitable for various NLP tasks.