# 📚 Text Preprocessing and Bag of Words (BoW)

> A complete guide and implementation of **Text Preprocessing**, **Tokenization**, **Vectorization**, and the **Bag of Words (BoW)** model for Natural Language Processing (NLP).

---

# 📖 Overview

Before machine learning algorithms can understand textual data, raw text must be transformed into numerical representations. This process involves several stages, including:

- Text Cleaning
- Tokenization
- Normalization
- Feature Extraction (Vectorization)
- Model Training

This repository focuses on one of the most fundamental feature extraction techniques in NLP: **Bag of Words (BoW)**, while also introducing the preprocessing steps that are commonly applied before vectorization.

---

# 🧹 Text Preprocessing

Text preprocessing is the process of cleaning and standardizing raw text before feature extraction. Proper preprocessing improves the quality of features and often leads to better model performance.

---

## 1. Lowercasing

Converts all characters to lowercase.

Example:

```
Machine Learning
```

↓

```
machine learning
```

Why?

- Prevents duplicate words.
- "Machine" and "machine" become the same token.

---

## 2. Removing Punctuation

Punctuation usually carries little meaning in traditional machine learning models.

Example:

```
Hello!!!
```

↓

```
Hello
```

Characters commonly removed:

```
.
,
?
!
:
;
(
)
[
]
{
}
"
'
-
_
/
\
```

---

## 3. Removing Numbers

Depending on the application, numerical values may be removed.

Example

```
Python 3.12 was released in 2023
```

↓

```
Python was released in
```

This step is optional and depends on the dataset.

---

## 4. Removing Stop Words

Stop words are extremely common words that usually contribute little semantic information.

Examples:

```
the
is
are
was
were
and
of
to
in
for
```

Sentence:

```
The movie was very interesting.
```

↓

```
movie interesting
```

Popular stop-word lists:

- NLTK Stopwords
- spaCy Stopwords
- Scikit-Learn Stopwords

---

## 5. Removing Extra Whitespaces

Example

```
Machine      Learning
```

↓

```
Machine Learning
```

---

## 6. Stemming

Stemming reduces words to their root form by removing prefixes and suffixes.

Example:

| Original | Stem |
|-----------|------|
| playing | play |
| played | play |
| player | player |
| studies | studi |
| studying | studi |

Popular stemmers:

- Porter Stemmer
- Snowball Stemmer
- Lancaster Stemmer

Advantages

- Fast
- Reduces vocabulary size

Disadvantages

- May produce non-dictionary words

Example:

```
studies → studi
```

---

## 7. Lemmatization

Lemmatization converts a word into its dictionary (lemma) form.

Example:

| Word | Lemma |
|-------|--------|
| running | run |
| better | good |
| studies | study |
| mice | mouse |

Advantages

- Produces valid dictionary words
- Preserves semantic meaning

Disadvantages

- Slower than stemming
- Requires linguistic knowledge

---

## 8. Text Normalization

Normalization includes multiple operations such as:

- Lowercasing
- Unicode normalization
- Removing accents
- Standardizing contractions

Example:

```
can't
```

↓

```
cannot
```

---

# 🔠 Tokenization

Tokenization is the process of splitting text into smaller units called **tokens**.

---

## Word Tokenization

Splits text into individual words.

Example:

```
Artificial Intelligence is amazing.
```

↓

```
[
Artificial,
Intelligence,
is,
amazing
]
```

Applications:

- Bag of Words
- TF-IDF
- Word Embeddings

Popular libraries:

- NLTK
- spaCy
- Hugging Face Tokenizers

---

## Sentence Tokenization

Splits text into sentences.

Example:

```
I love NLP. It is fascinating.
```

↓

```
Sentence 1:
I love NLP.

Sentence 2:
It is fascinating.
```

Applications:

- Text summarization
- Document segmentation
- Machine translation

---

# 📊 Vectorization

Machine learning algorithms cannot process raw text directly.

Vectorization converts text into numerical features.

---

## 1. Count Vectorizer (Bag of Words)

CountVectorizer counts the number of occurrences of each word.

Example

Sentence:

```
Machine learning is fun
```

Vocabulary

```
Machine
Learning
is
fun
```

Vector

```
[1,1,1,1]
```

If another sentence is

```
Machine Machine Learning
```

Vector

```
[2,1,0,0]
```

Advantages

- Very simple
- Fast
- Easy to interpret

Limitations

- Ignores word importance
- Ignores word order
- Produces sparse matrices

---

## 2. Binary Vectorizer

Instead of counting frequencies, Binary Vectorizer records only whether a word exists.

Example

Sentence

```
Machine Machine Learning
```

Count Vector

```
[2,1]
```

Binary Vector

```
[1,1]
```

Useful for:

- Document classification
- Spam filtering

---

## 3. TF-IDF Vectorizer

TF-IDF (Term Frequency–Inverse Document Frequency) assigns higher weights to informative words and lower weights to common words.

Instead of simple counts, TF-IDF computes:

- Term Frequency (TF)
- Inverse Document Frequency (IDF)

Advantages

- Reduces the impact of common words
- Highlights informative terms
- Often performs better than Bag of Words

---

## 4. N-Gram Vectorizer

Instead of considering single words, N-Grams capture sequences of words.

Example

Sentence

```
Machine Learning is Fun
```

Unigrams

```
Machine
Learning
is
Fun
```

Bigrams

```
Machine Learning
Learning is
is Fun
```

Trigrams

```
Machine Learning is
Learning is Fun
```

Advantages

- Preserves some contextual information
- Improves classification performance

Disadvantages

- Increases vocabulary size dramatically

---

## 5. Hashing Vectorizer

Hashing Vectorizer maps words into fixed-size vectors using a hash function.

Advantages

- Memory efficient
- Suitable for very large datasets
- No vocabulary storage

Disadvantages

- Hash collisions
- Cannot recover original words

---

# 🧠 Bag of Words Workflow

```
Raw Text
    │
    ▼
Cleaning
    │
    ▼
Lowercase
    │
    ▼
Remove Punctuation
    │
    ▼
Stop Word Removal
    │
    ▼
Stemming / Lemmatization
    │
    ▼
Tokenization
    │
    ▼
Vocabulary Creation
    │
    ▼
Count Vectorizer
    │
    ▼
Feature Matrix
    │
    ▼
Machine Learning Model
```

---

# 📚 Applications

The techniques covered in this repository are widely used in:

- Sentiment Analysis
- Spam Detection
- Fake News Detection
- Topic Classification
- Search Engines
- Recommendation Systems
- Text Mining
- Document Classification
- Email Filtering
- Information Retrieval

---

# ⭐ If you found this repository helpful, please consider giving it a star!
