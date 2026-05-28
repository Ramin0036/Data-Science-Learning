# Missing Values Handling with SimpleImputer and KNNImputer

### Overview
This repository demonstrates how to handle **missing values** in datasets using two common imputation techniques from **scikit-learn**:

- **SimpleImputer**
- **KNNImputer**

Missing data is a common issue in real-world datasets and can negatively affect model performance if not handled properly. This project provides practical examples of how to detect, analyze, and impute missing values using these methods.

---

### Objectives
- Identify missing values in a dataset
- Understand different imputation strategies
- Apply **SimpleImputer** for basic replacement
- Apply **KNNImputer** for neighbor-based imputation
- Compare the behavior of both methods

---

### Methods Used

#### 1. SimpleImputer
`SimpleImputer` fills missing values using a statistical strategy such as:

- **mean**
- **median**
- **most_frequent**
- **constant**

It is simple, fast, and useful as a baseline approach.

#### 2. KNNImputer
`KNNImputer` fills missing values based on the values of the **nearest neighbors**.  
It estimates missing entries by looking at similar samples in the dataset.

This method can produce better results in some cases, but it is usually more computationally expensive than `SimpleImputer`.

---

### Technologies
- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib / Seaborn (optional for visualization)
