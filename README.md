# Anomaly Detection in Network Traffic Using Autoencoder (Keras + TensorFlow)

An end-to-end deep learning project to detect anomalous behavior in network traffic using an unsupervised **autoencoder neural network**. Built around the **KDD Cup 1999 dataset**, this project follows the **CRISP-DM methodology** for a real-world data science workflow.

---

## CRISP-DM Workflow Overview

### 1. **Business Understanding**
Anomalies in network traffic may indicate cyber attacks or unusual behaviors. Manual detection is unreliable at scale.  
> **Goal:** Use unsupervised deep learning to identify anomalies from network connection logs using reconstruction error.

---

### 2. **Data Understanding**

- **Dataset**: [KDD Cup 1999](https://kdd.ics.uci.edu/databases/kddcup99/kddcup99.html)
- Contains ~500,000 network connection records with 41 features.
- Each record represents a session labeled as normal or a type of attack (DoS, Probe, R2L, etc.).
- Used **only numeric features** for the Autoencoder model (after one-hot encoding).

---

### 3. **Data Preparation**

- Removed non-numeric or highly redundant columns.
- Applied `MinMaxScaler` to normalize all features to [0, 1].
- Splitted dataset into train and test using unsupervised approach (same input and output).
- Engineered a reconstruction error for each sample.

---

### 4. **Modeling**

- **Architecture**: Symmetric autoencoder using `Dense` layers.
  - Encoder: 64 → 32 → 16 (bottleneck)
  - Decoder: 32 → 64 → output
- **Loss Function**: `Mean Squared Error (MSE)`
- **Optimizer**: Adam
- **EarlyStopping** and `ReduceLROnPlateau` used for regularization
- **Threshold**: 99th percentile of reconstruction error used to define anomalies

---

### 5. **Evaluation**

- Plotted histogram of reconstruction errors
- Marked anomaly threshold (top 1%) visually
- Anomalies were flagged without labels (unsupervised)
- (Optional) Labels available for downstream evaluation using precision, recall, F1

---


## Results Summary

- Unsupervised model effectively separated normal and anomalous sessions
- Autoencoder reconstruction error provides interpretable metric
- Easily extendable to log monitoring, fraud detection, or system health checks

---

##  Future Work

- Incorporate categorical features (e.g., protocol type) with embeddings
- Evaluate with ROC/AUC if labels are included
- Try different architectures: convolutional autoencoders, variational autoencoders

---

##  Key Learnings

- Autoencoders are powerful tools for unsupervised anomaly detection
- Scaling and threshold tuning are critical for performance
- Deep learning can uncover structural outliers in large tabular datasets

## Author

**Yusif Mammadov**  
📬 [LinkedIn](https://www.linkedin.com/in/yusif-m%C9%99mm%C9%99dov40/) • [GitHub](https://github.com/Yusif617)
