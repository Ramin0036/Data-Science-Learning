# 🧠 RNN, GRU & LSTM Deep Learning Guide

# Introduction

Recurrent Neural Networks are designed for sequential data such as text, speech and time series.

Unlike traditional neural networks, RNNs maintain memory through hidden states.

---

# 🔁 What is RNN?

An RNN processes data step by step while keeping information from previous steps.

```
x1 ---> x2 ---> x3 ---> x4

h1 ---> h2 ---> h3 ---> h4
```

---

# 🏗️ RNN Architecture

```
Previous Hidden State
          |
          v
     +---------+
xt ->|   RNN   |----> yt
     |  Cell   |
     +---------+
          |
          v
     New Hidden State
```

Formula:

```
h(t)=tanh(Wxh*x(t)+Whh*h(t-1)+b)
```

---

# 🧠 Hidden State

Hidden state is the memory of RNN.

It stores information from previous inputs:

```
h0 -> h1 -> h2 -> h3
```

---

# 🔄 Backpropagation Through Time (BPTT)

RNNs are trained by unfolding the network through time.

```
x1      x2      x3      x4

RNN -> RNN -> RNN -> RNN

h1      h2      h3      h4
```

---

# ⚠️ Vanishing & Exploding Gradient

## Vanishing Gradient

Gradients become very small:

```
1 -> 0.1 -> 0.01 -> 0
```

## Exploding Gradient

Gradients become extremely large:

```
1 -> 10 -> 100 -> 1000
```

Solutions:
- Gradient clipping
- GRU
- LSTM

---

# 🟢 GRU (Gated Recurrent Unit)

GRU improves RNN by introducing gates.

Advantages:

- Faster training
- Fewer parameters
- Good performance

GRU has:

1. Update Gate
2. Reset Gate

---

# 🚪 GRU Gates

## Update Gate

Controls how much previous information remains.

```
z(t)=σ(Wz[h(t-1),x(t)])
```

## Reset Gate

Controls ignored previous information.

```
r(t)=σ(Wr[h(t-1),x(t)])
```

Architecture:

```
x(t)
 |
 v
+---------+
|   GRU   |
| Gates   |
+---------+
 |
 v
h(t)
```

---

# 🔵 LSTM

Long Short-Term Memory networks solve long-term dependency problems.

They use:

```
Cell State
```

Architecture:

```
x(t)

 |
 v

+----------------+
|     LSTM       |
| Forget Gate    |
| Input Gate     |
| Output Gate    |
+----------------+

 |
 v

h(t), C(t)
```

---

# 🚪 LSTM Gates

## Forget Gate

Removes unnecessary information.

```
$$f(t)=σ(Wf[h(t-1),x(t)])$$
```

## Input Gate

Stores new information.

```
i(t)=σ(Wi[h(t-1),x(t)])
```

## Output Gate

Controls output information.

```
o(t)=σ(Wo[h(t-1),x(t)])
```

---

# ⚔️ RNN vs GRU vs LSTM

| Feature | RNN | GRU | LSTM |
|-|-|-|-|
| Memory | Low | Medium | High |
| Gates | No | 2 | 3 |
| Speed | Fast | Faster | Slower |
| Complexity | Low | Medium | High |

---

# 🧭 When To Use Each Model

## RNN
- Short sequences
- Simple problems

## GRU
- Faster training
- Limited resources

## LSTM
- Long sequences
- Complex dependencies

---

# 🌍 Applications

## NLP
- Sentiment Analysis
- Translation
- Text Generation

## Speech
- Voice Recognition

## Time Series
- Forecasting
- Financial Prediction

## Healthcare
- Medical Signals

---

⭐ If this project helped you, consider giving it a star!
