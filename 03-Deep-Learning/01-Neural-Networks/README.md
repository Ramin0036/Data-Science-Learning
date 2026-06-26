# Neural Networks Fundamentals

## Overview

Artificial Neural Networks (ANNs) are one of the most powerful machine learning models inspired by the structure of the human brain. They consist of interconnected layers of neurons that learn complex patterns from data through training.

Neural networks are widely used in classification, regression, computer vision, natural language processing, and many other artificial intelligence applications.

This project introduces the fundamental concepts required to build, train, and optimize neural network models using TensorFlow/Keras.

---

# Building a Neural Network Model

A neural network model is constructed by stacking multiple layers, where each layer learns increasingly complex representations of the input data.

Typical layers include:

- Input Layer
- Hidden Layers
- Output Layer

Each neuron receives input values, applies weights and biases, passes the result through an activation function, and forwards the output to the next layer.

---

# Activation Functions

Activation functions introduce non-linearity into neural networks, enabling them to learn complex relationships.

## ReLU (Rectified Linear Unit)

```text
f(x) = max(0, x)
```

### Advantages

- Fast and computationally efficient.
- Helps reduce the vanishing gradient problem.
- Most commonly used in hidden layers.

---

## Sigmoid

```text
f(x) = 1 / (1 + e^(-x))
```

### Advantages

- Produces outputs between 0 and 1.
- Suitable for binary classification output layers.

### Limitations

- Suffers from vanishing gradients.
- Slower convergence.

---

## Softmax

Softmax converts outputs into probability distributions whose values sum to one.

### Applications

- Multi-class classification.
- Output layer for categorical prediction.

---

## Tanh

```text
f(x) = tanh(x)
```

### Advantages

- Outputs range between -1 and 1.
- Zero-centered activation.

### Limitations

- Can also suffer from vanishing gradients.

---

# Model Compilation

Before training, a neural network must be compiled.

Compilation defines:

- Loss Function
- Optimizer
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

Optimizers update the model weights during training to minimize the loss function.

## SGD (Stochastic Gradient Descent)

Updates weights using the gradient of the loss function.

### Advantages

- Simple and memory efficient.
- Suitable for many optimization problems.

---

## Adam

Adaptive Moment Estimation (Adam) combines momentum and adaptive learning rates.

### Advantages

- Fast convergence.
- Works well for most deep learning tasks.
- Default optimizer in many applications.

---

## RMSprop

Adjusts learning rates automatically for each parameter.

### Advantages

- Performs well on recurrent neural networks.
- Stable convergence.

---

# Loss Functions

The loss function measures the difference between predicted values and actual targets.

Common loss functions include:

| Loss Function | Application |
|---------------|-------------|
| Binary Crossentropy | Binary Classification |
| Categorical Crossentropy | Multi-class Classification |
| Sparse Categorical Crossentropy | Integer Labels |
| Mean Squared Error (MSE) | Regression |
| Mean Absolute Error (MAE) | Regression |

A lower loss indicates better model performance.

---

# Accuracy

Accuracy measures the proportion of correctly classified samples.

```text
Accuracy = Correct Predictions / Total Predictions
```

Higher accuracy generally indicates better classification performance.

---

# Model Training (Fit)

The `fit()` function trains the neural network using the training dataset.

Example:

```python
model.fit(
    X_train,
    y_train,
    epochs=20,
    batch_size=32,
    validation_split=0.2
)
```

During training, the model repeatedly updates its weights to minimize the loss function.

---

# Epoch

An **Epoch** represents one complete pass of the entire training dataset through the neural network.

- More epochs allow the model to learn more.
- Too many epochs may lead to overfitting.

---

# Batch Size

Batch Size is the number of training samples processed before updating the model parameters.

Common values include:

- 16
- 32
- 64
- 128

Smaller batch sizes require more updates but may improve generalization.

---

# Validation Data

Validation data is a portion of the dataset used during training to evaluate the model on unseen data.

It helps monitor:

- Model performance
- Overfitting
- Generalization ability

Validation data is **not** used to update model weights.

---

# Preventing Overfitting

Overfitting occurs when a neural network memorizes the training data instead of learning general patterns, resulting in poor performance on unseen data.

Several techniques can reduce overfitting.

---

## 1. Dropout

Dropout randomly disables a fraction of neurons during training.

This forces the network to learn more robust representations instead of relying on specific neurons.

### Advantages

- Reduces overfitting.
- Improves model generalization.
- Easy to implement.

---

## 2. Early Stopping

Early Stopping monitors validation performance during training.

If the validation loss stops improving for several epochs, training is automatically stopped.

### Advantages

- Prevents unnecessary training.
- Reduces overfitting.
- Saves computational time.

---

## 3. Kernel Regularizer

Kernel Regularization adds a penalty to large weight values during optimization.

Common regularization techniques include:

- L1 Regularization
- L2 Regularization

These penalties encourage simpler models with better generalization.

### Advantages

- Reduces model complexity.
- Prevents excessively large weights.
- Improves generalization performance.

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

Artificial Neural Networks are powerful models capable of learning complex relationships from data. Building an effective neural network requires selecting appropriate activation functions, optimizers, loss functions, and training parameters such as epochs and batch size.

To improve generalization and avoid overfitting, techniques such as **Dropout**, **Early Stopping**, and **Kernel Regularization** are commonly employed.

Understanding these core concepts is essential for developing accurate and efficient deep learning models.
