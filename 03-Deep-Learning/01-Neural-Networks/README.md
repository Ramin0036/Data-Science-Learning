# Neural Networks Fundamentals

## Overview

Artificial Neural Networks (ANNs) are machine learning models inspired by the human brain. They consist of interconnected neurons organized into layers that learn patterns from data.

Neural networks are widely used for classification, regression, computer vision, natural language processing, and many other AI applications.

This project introduces the essential concepts required to build, train, evaluate, and regularize neural network models using TensorFlow/Keras.

---

# Building a Neural Network Model

A neural network is typically composed of:

- Input Layer
- Hidden Layer(s)
- Output Layer

Each neuron receives inputs, applies weights and a bias, computes a weighted sum, and passes the result through an activation function.

---

# Activation Functions

Activation functions introduce non-linearity, enabling neural networks to learn complex relationships.

## 1. ReLU (Rectified Linear Unit)

Formula:

$$
f(x)=\max(0,x)
$$

**Output Range:** `[0,+∞)`

**Common Usage**

- Hidden Layers
- CNNs
- Deep Neural Networks

**Advantages**

- Fast computation
- Reduces vanishing gradients
- Most widely used hidden-layer activation

**Limitation**

- May suffer from the Dead ReLU problem.

---

## 2. Leaky ReLU

Formula:

$$
f(x)=
\begin{cases}
x,&x>0\\
\alpha x,&x\le0
\end{cases}
$$

**Output Range:** `(-∞,+∞)`

**Common Usage**

- Hidden Layers
- Alternative to ReLU

**Advantages**

- Prevents dead neurons
- Better gradient flow

---

## 3. ELU (Exponential Linear Unit)

Formula:

$$
f(x)=
\begin{cases}
x,&x>0\\
\alpha(e^x-1),&x\le0
\end{cases}
$$

**Common Usage**

- Hidden Layers
- Deep Networks

**Advantages**

- Faster convergence
- Reduces bias shift

---

## 4. Sigmoid

Formula:

$$
f(x)=\frac{1}{1+e^{-x}}
$$

**Output Range:** `(0,1)`

**Common Usage**

- Output Layer for Binary Classification

**Advantages**

- Produces probabilities

**Limitations**

- Vanishing gradient
- Not recommended for hidden layers

---

## 5. Tanh

Formula:

$$
f(x)=\tanh(x)
$$

**Output Range:** `(-1,1)`

**Common Usage**

- Hidden Layers (small networks)

**Advantages**

- Zero-centered output

**Limitations**

- Vanishing gradient

---

## 6. Softmax

Formula:

$$
\text{Softmax}(x_i)=\frac{e^{x_i}}{\sum_j e^{x_j}}
$$

**Output Range:** `(0,1)` (outputs sum to 1)

**Common Usage**

- Output Layer for Multi-class Classification

**Advantages**

- Produces probability distribution across classes

---

## 7. Linear

Formula:

$$
f(x)=x
$$

**Output Range:** `(-∞,+∞)`

**Common Usage**

- Output Layer for Regression

**Advantages**

- Preserves continuous values without bounding the output

---

## Activation Function Comparison

| Function | Hidden Layer | Output Layer | Typical Task |
|-----------|--------------|--------------|--------------|
| ReLU | ✅ | ❌ | Hidden layers |
| Leaky ReLU | ✅ | ❌ | Hidden layers |
| ELU | ✅ | ❌ | Hidden layers |
| Tanh | ✅ | ❌ | Small networks |
| Sigmoid | ❌ | ✅ | Binary Classification |
| Softmax | ❌ | ✅ | Multi-class Classification |
| Linear | ❌ | ✅ | Regression |

---

# Model Compilation

Before training, a model must be compiled.

Compilation defines:

- Optimizer
- Loss Function
- Evaluation Metrics

Example:

```python
model.compile(
    optimizer="adam",
    loss="categorical_crossentropy",
    metrics=["accuracy"]
)
```

---

# Optimizers

Optimizers update model weights to minimize the loss.

## SGD

- Simple Gradient Descent
- Stable and memory efficient
- May converge slowly

## Adam

- Adaptive learning rate
- Fast convergence
- Default choice for most projects

## RMSprop

- Adaptive learning rate
- Performs well for sequential data and RNNs

## AdamW

- Adam with decoupled weight decay
- Better regularization than Adam
- Common in modern deep learning

## Adagrad

- Adapts learning rate for each parameter
- Effective for sparse features
- Learning rate may decay too quickly

---

## Optimizer Comparison

| Optimizer | Adaptive LR | Fast Convergence | Typical Usage |
|------------|------------|-----------------|---------------|
| SGD | ❌ | Medium | General optimization |
| Adam | ✅ | ✅ | Default choice |
| RMSprop | ✅ | ✅ | RNNs |
| AdamW | ✅ | ✅ | Modern deep learning |
| Adagrad | ✅ | Medium | Sparse data |

---

# Loss Functions

Loss functions measure prediction error.

| Loss Function | Task | Typical Output Layer |
|---------------|------|----------------------|
| Binary Crossentropy | Binary Classification | Sigmoid |
| Categorical Crossentropy | Multi-class Classification (One-Hot Labels) | Softmax |
| Sparse Categorical Crossentropy | Multi-class Classification (Integer Labels) | Softmax |
| Mean Squared Error (MSE) | Regression | Linear |
| Mean Absolute Error (MAE) | Regression | Linear |
| Huber Loss | Regression (robust to outliers) | Linear |

Lower loss indicates better model performance.

---

# Accuracy

Accuracy measures the proportion of correctly predicted samples.

Formula:

$$
Accuracy=\frac{Correct\ Predictions}{Total\ Predictions}
$$

Higher accuracy generally indicates better classification performance.

---

# Model Training (fit)

Training is performed using:

```python
model.fit(
    X_train,
    y_train,
    epochs=20,
    batch_size=32,
    validation_split=0.2
)
```

The model updates its weights after each batch to minimize the loss.

---

# Epoch

An **Epoch** is one complete pass through the entire training dataset.

- More epochs improve learning.
- Too many epochs may cause overfitting.

---

# Batch Size

Batch Size is the number of samples processed before updating model weights.

Common values:

- 16
- 32
- 64
- 128

---

# Validation Data

Validation data is used during training to evaluate generalization.

It is **not** used to update model weights.

It helps monitor:

- Validation Loss
- Validation Accuracy
- Overfitting

---

# Preventing Overfitting

## Dropout

Randomly disables a percentage of neurons during training.

**Benefits**

- Reduces overfitting
- Improves generalization

---

## Early Stopping

Stops training automatically when validation performance no longer improves.

**Benefits**

- Prevents overfitting
- Saves training time

---

## Kernel Regularizer

Adds penalties to large weights.

Common types:

- L1 Regularization
- L2 Regularization

**Benefits**

- Simpler models
- Better generalization
- Reduces overfitting

---

# Technologies Used

- Python
- TensorFlow
- Keras
- NumPy
- Matplotlib
- Scikit-learn

---

# Conclusion

Building an effective neural network requires selecting suitable activation functions, optimizers, loss functions, and training parameters.

For most modern applications:

- Hidden Layers → ReLU / Leaky ReLU / ELU
- Binary Classification Output → Sigmoid
- Multi-class Classification Output → Softmax
- Regression Output → Linear activation

Regularization techniques such as **Dropout**, **Early Stopping**, and **Kernel Regularization** improve model generalization and help prevent overfitting.
