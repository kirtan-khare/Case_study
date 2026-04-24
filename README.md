# Self-Pruning Neural Network — AI Engineering Case Study

This project presents a neural network that is capable of **learning its own structure** by identifying and suppressing less important connections during training.

---

## 🔍 Overview

- Each weight is paired with a **learnable gate parameter**  
- Gate values lie between 0 and 1 using a sigmoid function  
- The network gradually reduces the influence of unnecessary connections  

---

## ⚙️ Core Components

### 🔹 Prunable Layer
- Custom implementation of a linear layer with gating  
- Gates scale the weights dynamically during training  
- Effective weights are computed as: `weight × gate`  

---

### 🔹 Sparsity Mechanism
- A regularization term is applied to all gate values  
- Encourages the model to minimize active connections  
- Enables pruning to happen as part of optimization  

---

### 🔹 Loss Function

Total Loss = Classification Loss + λ × Sparsity Loss  

- Classification Loss → improves prediction accuracy  
- Sparsity Loss → encourages model compression  

---

## 📊 Experimental Results

| Lambda | Test Accuracy | Sparsity (%) |
|--------|-------------|--------------|
| 1e-4   | 0.5615      | 0.00         |
| 1e-3   | 0.5394      | 0.00         |
| 1e-2   | 0.5039      | 0.00         |

---

## 📈 Key Observations

- Increasing λ leads to a slight drop in accuracy  
- The model reduces connection strengths instead of fully removing them  
- Measured sparsity remains 0% under strict thresholding  

---

## 📉 Gate Value Distribution

- Gate values are mostly concentrated at lower ranges  
- Very few gates approach zero exactly  
- This indicates **soft pruning behavior** rather than discrete pruning  


---

## 📁 Repository Contents

- `self_pruning_nn.ipynb` — Full implementation  
- `report.md` — Explanation and analysis  

---

## 🧠 Learnings

- Demonstrated differentiable pruning using gating  
- Explored trade-offs between model performance and compression  
- Observed limitations of sigmoid-based pruning methods  

