# Cybersecurity Threat Detection using Deep Learning

## Overview

This project focuses on detecting **suspicious system events** using a deep learning model trained on system-level logs. The goal is to classify whether a given event is **malicious (1)** or **normal (0)**.

The dataset is highly **imbalanced**, making this a challenging binary classification problem where correctly identifying rare suspicious events is critical.

---

## Objective

- Build a binary classification model to detect suspicious events  
- Handle **class imbalance effectively**  
- Optimize for **high recall** (catch all threats) while maintaining good precision  
- Evaluate model using **F1-score, Precision, Recall, and ROC-AUC**

---

## Dataset Description

| Column | Description |
|--------|-------------|
| **processId** | Unique identifier for the process generating the event |
| **threadId** | ID of the thread spawning the log |
| **parentProcessId** | ID of the parent process |
| **userId** | ID of the user generating the event |
| **mountNamespace** | Namespace isolation for the process |
| **argsNum** | Number of arguments passed to the event |
| **returnValue** | Return value from the system call (usually 0) |
| **sus_label** | Target label (1 = suspicious, 0 = normal) |

---


## Approach

### 1. Data Preprocessing
- Train / Validation / Test split
- Feature scaling using `StandardScaler`
- Conversion to PyTorch tensors

### 2. Model Architecture
A fully connected neural network:# Cybersecurity Threat Detection using Deep Learning

## Overview

This project focuses on detecting **suspicious system events** using a deep learning model trained on system-level logs. The goal is to classify whether a given event is **malicious (1)** or **normal (0)**.

The dataset is highly **imbalanced**, making this a challenging binary classification problem where correctly identifying rare suspicious events is critical.

---

## 🚀 Objective

- Build a binary classification model to detect suspicious events  
- Handle **class imbalance effectively**  
- Optimize for **high recall** (catch all threats) while maintaining good precision  
- Evaluate model using **F1-score, Precision, Recall, and ROC-AUC**

---

## 📊 Dataset Description

| Column | Description |
|--------|-------------|
| **processId** | Unique identifier for the process generating the event |
| **threadId** | ID of the thread spawning the log |
| **parentProcessId** | ID of the parent process |
| **userId** | ID of the user generating the event |
| **mountNamespace** | Namespace isolation for the process |
| **argsNum** | Number of arguments passed to the event |
| **returnValue** | Return value from the system call (usually 0) |
| **sus_label** | Target label (1 = suspicious, 0 = normal) |

---

## Key Challenges

- **Severe class imbalance**
- Most features are **ID-based (high cardinality)**
- Risk of **data leakage via identifiers**
- Precision-recall trade-off due to imbalance

---

##  Approach

### 1. Data Preprocessing
- Train / Validation / Test split
- Feature scaling using `StandardScaler`
- Conversion to PyTorch tensors

### 2. Model Architecture
A fully connected neural network:
#  Cybersecurity Threat Detection using Deep Learning

### 3. Handling Imbalance

- Used **Weighted Binary Cross Entropy Loss**
- Ensured the model focuses on minority class (suspicious events)

---

### 4. Training Strategy

- Batch training with DataLoader
- Manual training loop in PyTorch
- Tracking:
  - Loss (train + validation)
  - Accuracy
  - Precision
  - Recall
  - F1 Score

---

## Evaluation Metrics

Due to imbalance, accuracy alone is misleading. We focus on:

- **Precision** → How many predicted threats are correct  
- **Recall** → How many actual threats are detected  
- **F1 Score** → Balance between precision & recall  
- **ROC-AUC** → Overall separability of classes  

---

## Results

-  **High Recall (~1.0)** → All suspicious events detected  
- **Improved Precision** after including `userId`  
- **Stable training after initial fluctuations**  
- **ROC-AUC ≈ 0.99** → Excellent class separation  

### Interpretation

- Model effectively distinguishes between normal and suspicious events  
- ROC curve close to **top-left corner** → high TPR, low FPR  
- Indicates strong detection capability with minimal false alarms  

---

##  Key Insights

- `userId` turned out to be a **highly predictive feature**  
- Removing it reduced performance significantly  
- ID-based features can lead to **memorization**, but also provide strong signals  
- Weighted loss improves recall but can initially reduce precision  

---

## Observations During Training

- Precision fluctuated early due to:
  - Imbalance  
  - Threshold sensitivity  
- Stabilized after model convergence  
- Recall remained consistently high  

---

##  Tech Stack

- Python  
- PyTorch  
- Scikit-learn  
- NumPy  
- Matplotlib  

---


## Author

**Aahan Charak**

