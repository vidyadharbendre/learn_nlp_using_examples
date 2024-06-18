# Natural Language Processing (NLP)

## Introduction
This is a structured approach to learning Natural Language Processing (NLP), starting from basic concepts and gradually moving to more advanced topics. Each section includes code examples to illustrate the concepts.

## Table of Contents
1. [Introduction to NLP](#introduction-to-nlp)
2. [Text Preprocessing](#text-preprocessing)
    - [Tokenization](#tokenization)
    - [Normalization](#normalization)
    - [Stemming and Lemmatization](#stemming-and-lemmatization)
3. [Part-of-Speech (POS) Tagging](#part-of-speech-pos-tagging)
4. [Named Entity Recognition (NER)](#named-entity-recognition-ner)
5. [Syntactic Parsing](#syntactic-parsing)
6. [Semantic Analysis](#semantic-analysis)
    - [Sentiment Analysis](#sentiment-analysis)
    - [Word Embeddings](#word-embeddings)
7. [Advanced Topics](#advanced-topics)
    - [Text Classification](#text-classification)
    - [Machine Translation](#machine-translation)
    - [Question Answering](#question-answering)
8. [Practical Projects](#practical-projects)
9. [Evaluation and Optimization](#evaluation-and-optimization)

## Introduction to NLP
Natural Language Processing (NLP) is a field of Artificial Intelligence (AI) that focuses on the interaction between computers and humans through natural language. It has applications in various domains such as chatbots, sentiment analysis, machine translation, and more.

## Text Preprocessing
Text preprocessing is a crucial step in NLP. It involves preparing and cleaning the text data to make it suitable for further analysis.

### Tokenization
Tokenization is the process of breaking down text into smaller units called tokens. These tokens can be words, phrases, or even characters.

Example:
```python
import spacy
nlp = spacy.load("en_core_web_sm")
text = "Radhika lives in New Delhi."
doc = nlp(text)
tokens = [token.text for token in doc]
print(tokens)
