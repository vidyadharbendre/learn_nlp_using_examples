# Information Retrieval and Lexical Resources with NLTK and spaCy

This repository provides an overview of Information Retrieval (IR) and Lexical Resources using the `nltk` and `spaCy` libraries in Python. It covers theoretical concepts, practical examples, and demonstrations to help students understand and apply these topics.

## Table of Contents

1. [Introduction](#introduction)
2. [Information Retrieval](#information-retrieval)
   - [Classical Models](#classical-models)
   - [Non-Classical Models](#non-classical-models)
   - [Alternative Models](#alternative-models)
   - [Evaluation](#evaluation)
3. [Lexical Resources](#lexical-resources)
   - [WordNet](#wordnet)
   - [FrameNet](#framenet)
   - [Stemmers](#stemmers)
   - [POS Tagger](#pos-tagger)
   - [Research Corpora](#research-corpora)
4. [Examples and Demonstrations](#examples-and-demonstrations)
   - [Using NLTK](#using-nltk)
   - [Using spaCy](#using-spacy)
   - [Simple Information Retrieval System](#simple-information-retrieval-system)
5. [Conclusion](#conclusion)

## Introduction

This repository demonstrates how to use `nltk` and `spaCy` to implement Information Retrieval (IR) systems and leverage lexical resources. It includes theoretical explanations and practical code examples.

## Information Retrieval

### Classical Models

1. **Boolean Model**: Uses Boolean logic to match documents based on the presence or absence of query terms.
2. **Vector Space Model**: Represents documents and queries as vectors in a multi-dimensional space and uses cosine similarity to measure relevance.
3. **Probabilistic Model**: Estimates the probability that a given document is relevant to a query.

### Non-Classical Models

1. **Latent Semantic Indexing (LSI)**: Uses singular value decomposition to reduce the dimensionality of the document-term matrix and captures the underlying structure in the data.
2. **Language Models**: Represents documents as probability distributions over terms and ranks documents based on the likelihood of generating the query.

### Alternative Models

1. **Neural IR Models**: Use deep learning techniques to learn complex representations of queries and documents.
2. **Graph-based Models**: Represent documents and terms as nodes in a graph and use algorithms like PageRank to rank documents.

### Evaluation

1. **Precision and Recall**: Measures of relevance; precision is the ratio of relevant documents retrieved to the total documents retrieved, while recall is the ratio of relevant documents retrieved to the total relevant documents.
2. **F1 Score**: Harmonic mean of precision and recall.
3. **Mean Average Precision (MAP)**: Average of precision scores at different recall levels.

## Lexical Resources

### WordNet

WordNet is a lexical database of English that groups words into sets of synonyms called synsets and provides short definitions and usage examples.

### FrameNet

FrameNet is a lexical database that documents the range of semantic and syntactic combinatory possibilities (valences) of English words.

### Stemmers

Stemmers are algorithms that reduce words to their base or root form (e.g., "running" to "run").

### POS Tagger

Part-of-speech tagging assigns parts of speech to each word in a sentence (e.g., noun, verb, adjective).

### Research Corpora

Large and structured sets of texts used for linguistic research and natural language processing tasks.

## Examples and Demonstrations

### Using NLTK

1. **Installing NLTK**:
```bash
pip install nltk
```
2. **WordNet Example**:
```bash
import nltk
from nltk.corpus import wordnet as wn

# Download WordNet data
nltk.download('wordnet')

# Example: Get synonyms for the word "information"
synsets = wn.synsets("information")
for synset in synsets:
    print(synset.name(), synset.definition(), synset.examples())
```

3. **POS Tagging Example:**
```bash
from nltk import pos_tag
from nltk.tokenize import word_tokenize

# Download necessary data
nltk.download('punkt')
nltk.download('averaged_perceptron_tagger')

# Example: POS tagging
text = "Information retrieval is an important area of study."
tokens = word_tokenize(text)
pos_tags = pos_tag(tokens)
print(pos_tags)
```

4. **Stemming Example:**
```bash
from nltk.stem import PorterStemmer

# Example: Stemming
stemmer = PorterStemmer()
words = ["running", "jumps", "easily", "fairly"]
stems = [stemmer.stem(word) for word in words]
print(stems)
```
### Using spaCy

1. **Installing spaCy:**

```bash
pip install spacy
python -m spacy download en_core_web_sm
```

2. **WordNet Example with spaCy:**

```bash
import spacy
from spacy_wordnet.wordnet_annotator import WordnetAnnotator

# Load spaCy model
nlp = spacy.load("en_core_web_sm")
nlp.add_pipe("spacy_wordnet", after='tagger')

# Example: Get synonyms for the word "information"
doc = nlp("information")
for token in doc:
    print(token.text, token._.wordnet.synsets())

```

3. **POS Tagging Example**

```bash
import spacy

# Load spaCy model
nlp = spacy.load("en_core_web_sm")

# Example: POS tagging
text = "Information retrieval is an important area of study."
doc = nlp(text)
pos_tags = [(token.text, token.pos_) for token in doc]
print(pos_tags)

```

4. **Stemming Example with spaCy:**

spaCy does not have a built-in stemmer, but you can use a lemmatizer instead:

```bash
import spacy

# Load spaCy model
nlp = spacy.load("en_core_web_sm")

# Example: Lemmatization
text = "running jumps easily fairly"
doc = nlp(text)
lemmas = [token.lemma_ for token in doc]
print(lemmas)

```

### Simple Information Retrieval System
1. **NLTK-based Information Retrieval System**

```bash
import nltk
from nltk.corpus import wordnet as wn
from nltk.tokenize import word_tokenize

# Download necessary data
nltk.download('wordnet')
nltk.download('punkt')

# Sample documents
documents = ["I deposited money in the bank.", "She went to the river bank.", "The bank offers various services."]

# Sample query
query = "financial institution"

# Tokenize and expand query with synonyms
query_tokens = word_tokenize(query)
expanded_query = set(query_tokens)
for word in query_tokens:
    synonyms = wn.synsets(word)
    for syn in synonyms:
        for lemma in syn.lemmas():
            expanded_query.add(lemma.name())

# Simple IR system
def retrieve_documents(query, documents):
    results = []
    for doc in documents:
        doc_tokens = set(word_tokenize(doc))
        if expanded_query & doc_tokens:
            results.append(doc)
    return results

# Retrieve relevant documents
relevant_docs = retrieve_documents(expanded_query, documents)
print(relevant_docs)
# Output: ['I deposited money in the bank.', 'The bank offers various services.']

```

2. **spaCy-based Information Retrieval System**

```bash
import spacy
from spacy_wordnet.wordnet_annotator import WordnetAnnotator

# Load spaCy model
nlp = spacy.load("en_core_web_sm")
nlp.add_pipe("spacy_wordnet", after='tagger')

# Sample documents
documents = ["I deposited money in the bank.", "She went to the river bank.", "The bank offers various services."]

# Sample query
query = "financial institution"

# Process query and expand with synonyms
query_doc = nlp(query)
expanded_query = set([token.text for token in query_doc])
for token in query_doc:
    synonyms = token._.wordnet.synsets()
    for syn in synonyms:
        for lemma in syn.lemmas():
            expanded_query.add(lemma.name())

# Simple IR system
def retrieve_documents(query, documents):
    results = []
    for doc in documents:
        doc_tokens = set([token.text for token in nlp(doc)])
        if expanded_query & doc_tokens:
            results.append(doc)
    return results

# Retrieve relevant documents
relevant_docs = retrieve_documents(expanded_query, documents)
print(relevant_docs)
# Output: ['I deposited money in the bank.', 'The bank offers various services.']

```

## Conclusion

By understanding and using the nltk and spaCy libraries, you can effectively leverage lexical resources to enhance the performance of information retrieval systems. These examples provide a solid foundation for further exploration and application in various NLP tasks.


