# SUPERNOVA @ DravidianLangTech-ACL 2026
## Transformer and Ensemble Approaches for Abusive Tamil Text Detection Targeting Women

This repository contains the implementation of the **SUPERNOVA** system submitted to the shared task on **Abusive Tamil Text Targeting Women on Social Media** at **DravidianLangTech@ACL 2026**.

Our system explores transformer-based and ensemble learning approaches for detecting abusive Tamil text targeting women in social media contexts.

---

# 📌 Task Overview

The shared task focuses on detecting abusive language directed at women in Tamil social media text.

The problem is formulated as a **binary classification task**:

- **Abusive**
- **Non-Abusive**

The dataset consists of annotated Tamil YouTube comments released by the task organizers.

---

# 📊 Dataset Statistics

| Split | Total | Abusive | Non-Abusive |
|-------|-------|---------|-------------|
| Train | 25,945 | 12,971 | 12,974 |
| Test  | 913 | 441 | 472 |

The dataset is manually annotated following task-specific guidelines.

---

# 🧠 System Overview

We investigate three complementary modeling strategies:

---

## 🔹 Run 1 — MuRIL Fine-Tuning (Best Submission)

### Model
- **MuRIL (Multilingual Representation for Indian Languages)**
- Pre-trained on 17 Indian languages including Tamil

### Method
- End-to-end supervised fine-tuning
- Class balancing
- Label smoothing
- Cross-entropy loss
- Softmax classification head

### Why MuRIL?
MuRIL is specifically trained for Indic languages and handles:
- Code-mixing
- Morphological complexity
- Low-resource settings

### Official Performance
- **Accuracy:** 0.8007  
- **Macro F1-score:** 0.7994  
- **Rank:** 11th

---

## 🔹 Run 2 — MuRIL + XGBoost

### Pipeline
1. Extract contextual embeddings from MuRIL
2. Use embeddings as feature vectors
3. Train XGBoost classifier
4. Apply threshold tuning

### Model Components
- MuRIL embeddings
- XGBoost (gradient boosting decision trees)
- Hyperparameter tuning (learning rate, tree depth, estimators)

### Motivation
Combines deep contextual features with powerful gradient boosting classification.

---

## 🔹 Run 3 — TF-IDF + SentenceBERT + Ensemble (CPU-Friendly)

### Features
- Character-level TF-IDF
- SentenceBERT embeddings

### Classifiers
- Random Forest
- Extra Trees
- Decision Tree

### Why This Run?
- No GPU required
- Efficient in low-resource environments
- Competitive baseline

### Performance
- Macro F1-score ≈ 0.74
- Fully CPU executable

---

# 🔍 Data Preprocessing

- Removal of URLs and special characters
- Whitespace normalization
- Minimal normalization to preserve semantic content
- Subword tokenization for transformer models
- TF-IDF vectorization for classical ML models

---

# 🧪 Experimental Setup

- Python 3.10+
- PyTorch
- HuggingFace Transformers
- scikit-learn
- XGBoost
- SentenceTransformers
- NumPy
- Pandas

Training:
- Optimizer: AdamW
- Loss: Cross-Entropy
- Evaluation Metrics:
  - Accuracy
  - Precision
  - Recall
  - Macro F1-score

---

# 📈 Results Summary

| Run | System | Accuracy | Macro F1 |
|-----|--------|----------|----------|
| Run 1 | MuRIL Fine-Tune | **0.8007** | **0.7994** |
| Run 2 | MuRIL + XGBoost | ~0.80 | ~0.80 |
| Run 3 | TF-IDF + SBERT + Ensemble | ~0.74 | ~0.74 |

---

# ▶️ How to Run

## Clone Repository
```bash
git clone https://github.com/Kiruthi001/SuperNova-DravidianLangTech-ACL2026.git
cd SuperNova-DravidianLangTech-ACL2026
