# 🧠 Word Embeddings for Natural Language Processing (NLP)

> A comprehensive introduction to **Word Embeddings**, their relationship to **Bag of Words (BoW)**, preprocessing, embedding methods, and best practices.

# 📖 Overview

Traditional methods such as **Bag of Words (BoW)** and **TF-IDF** represent text using sparse vectors. While simple and effective for many classical machine learning tasks, they ignore semantic relationships between words.

**Word Embeddings** solve this limitation by learning dense vector representations where semantically similar words are located close together in vector space.

Embeddings are now the foundation of most modern NLP systems, including search engines, recommendation systems, chatbots, machine translation, question answering, and Large Language Models (LLMs).

---

# 🤔 Why Do We Need Word Embeddings?

BoW treats every word as an independent feature.

Example:

Car → [1,0,0,0]

Automobile → [0,1,0,0]

Although both words have nearly identical meanings, BoW considers them completely different.

Word Embeddings instead learn:

Car ≈ Automobile

and assign them similar dense vectors.

---

# ⚖️ Word Embeddings vs Bag of Words (BoW)

| Feature | Bag of Words | Word Embeddings |
|---|---|---|
| Representation | Sparse | Dense |
| Captures semantics | ❌ | ✅ |
| Captures similarity | ❌ | ✅ |
| Word order | ❌ | ⚠️ (contextual models do) |
| Handles synonyms | ❌ | ✅ |
| Handles polysemy | ❌ | Contextual models only |
| Feature size | Vocabulary size | Fixed embedding size |
| Memory usage | High | Lower |

## Example

Sentence A:

`The car is fast.`

Sentence B:

`The automobile is fast.`

### Bag of Words

Vocabulary:

`[car, automobile, fast, is, the]`

Vectors:

Sentence A → `[1,0,1,1,1]`

Sentence B → `[0,1,1,1,1]`

BoW cannot recognize that *car* and *automobile* have the same meaning.

### Word Embeddings

The learned vectors are close:

Car → `[0.71,-0.12,0.54,...]`

Automobile → `[0.69,-0.10,0.58,...]`

A model can therefore understand their semantic similarity.

Another limitation of BoW:

`Dog bites man`

`Man bites dog`

These produce nearly identical BoW features because word order is ignored. Sequence models using embeddings (RNN, LSTM, Transformers, BERT, GPT) can learn the difference.

---

# 🧩 Sparse vs Dense Representations

## Sparse (BoW / TF-IDF)

- High dimensional
- Mostly zeros
- No semantic information

## Dense (Embeddings)

- Compact vectors
- Rich semantic information
- Better computational efficiency

---

# 📊 Distributional Hypothesis

> "Words that occur in similar contexts tend to have similar meanings."

Example:

The cat drinks milk.

The dog drinks milk.

The model learns that **cat** and **dog** are semantically related.

---

# 📐 Embedding Dimensions

Typical embedding sizes:

| Dimension | Usage |
|---:|---|
| 50 | Small models |
| 100 | General NLP |
| 200 | Better semantics |
| 300 | Word2Vec / GloVe |
| 768 | BERT Base |
| 1024+ | Large language models |

---

# 🏛 Types of Word Embeddings

## 1. Word2Vec

Google (2013)

### CBOW

Predicts the target word from surrounding context.

Advantages

- Fast
- Excellent for frequent words

Disadvantages

- Weaker on rare words

### Skip-Gram

Predicts surrounding words from the target word.

Advantages

- Better for rare words
- Higher-quality embeddings

Disadvantages

- Slower training

---

## 2. GloVe

Developed by Stanford.

Uses global word co-occurrence statistics.

Pros

- Strong semantic relationships
- Stable pretrained vectors

---

## 3. FastText

Developed by Meta AI.

Represents words using character n-grams.

Pros

- Handles unseen words
- Excellent for morphologically rich languages

Cons

- Larger models

---

## 4. Contextual Embeddings

Examples:

- BERT
- RoBERTa
- GPT
- ELMo
- DeBERTa

Unlike static embeddings, the vector depends on context.

Example:

"I deposited money in the bank."

"The boat reached the river bank."

The word **bank** receives different vectors.

---

# 🔄 Comparison

| Method | Context Aware | Rare Words | Static |
|---|---|---|---|
| Word2Vec | ❌ | Limited | ✅ |
| GloVe | ❌ | Limited | ✅ |
| FastText | ❌ | ✅ | ✅ |
| BERT | ✅ | ✅ | ❌ |
| GPT | ✅ | ✅ | ❌ |

---

# ✅ Advantages

- Dense vectors
- Semantic similarity
- Better generalization
- Lower dimensionality
- Improved downstream performance
- Pretrained models available

---

# ❌ Limitations

- Static methods assign one vector per word.
- Can inherit bias from training data.
- Training from scratch requires large corpora.
- Context-independent methods cannot distinguish multiple meanings.

---

# 🚀 Applications

- Sentiment Analysis
- Machine Translation
- Search Engines
- Chatbots
- Recommendation Systems
- Text Classification
- Named Entity Recognition
- Question Answering
- Large Language Models (LLMs)

---

# 💡 Best Practices

- Clean and normalize text before training.
- Use pretrained embeddings whenever possible.
- Use FastText for morphologically rich languages.
- Use BERT/GPT for context-dependent tasks.
- Fine-tune contextual models for downstream tasks.

# ⭐ If this repository helped you, consider giving it a star!
