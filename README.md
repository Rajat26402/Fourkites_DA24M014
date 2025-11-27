# 📘 Loss Landscape Geometry & Optimization Dynamics in Neural Networks  
### *A Comparative Study of Batch-Normalized and Non-Normalized CNNs*

This repository contains the full implementation and report for the project **“Loss Landscape Geometry and Optimization Dynamics in Neural Networks”**.  
The goal is to analyze how **neural network architecture choices**—particularly **Batch Normalization (BN)**—affect the loss landscape, optimization behavior, and generalization.

This work was completed as part of a research-oriented machine learning assignment, and includes both **theoretical foundations** and **empirical experiments**.

---

## 📄 **Project Overview**
Modern neural networks operate in extremely high-dimensional, non-convex loss landscapes.  
Yet, stochastic gradient descent (SGD) consistently finds solutions that generalize well.

This project explores **why**, by analyzing:

- Loss surface curvature  
- Sharpness under perturbations  
- Local geometry using 1D loss slices  
- Basin topology via mode connectivity  
- The effect of Batch Normalization on landscape geometry  

Two CNNs with identical architectures were trained on **Fashion-MNIST**, differing only by the inclusion of **BatchNorm**.

---


---

## 🧠 **Theoretical Highlights**

The analysis includes:

### 🔹 Loss Geometry  
- Hessian curvature  
- Gradient behavior  
- Local quadratic approximations  

### 🔹 Perturbation Sharpness  
Sharpness measured using **SAM-style adversarial perturbations**.

### 🔹 SGD as a Stochastic Differential Equation  
Understanding why SGD prefers **broader minima**:

\[
p(\theta) \propto \frac{e^{-L(\theta)/T}}{\sqrt{\det H(\theta)}}
\]

Shows how temperature/noise affects optimization trajectories.

---

## 🧪 **Experimental Setup**

- **Dataset:** Fashion-MNIST  
- **Models:**  
  - A1: CNN + BatchNorm  
  - A2: CNN + BatchNorm (different seed)  
  - B: CNN without BatchNorm  
- **Optimizer:** SGD + Momentum  
- **Epochs:** 6  
- **Batch size:** 128  

Both models share the same architecture; BN is the only difference.

---

## 📊 **Key Results** (with figures)

### 🔹 1. Training & Test Performance  
BatchNorm improves both training stability and generalization.

**Model A1 (with BN)**  
![Model A1](figures/P1A.png)

**Model B (no BN)**  
![Model B](figures/P1B.png)

---

### 🔹 2. Curvature (Hessian Eigenvalue)
\[
\lambda_{\max}(A1) \approx 57.18,\qquad
\lambda_{\max}(B) \approx 37.51
\]

BN → **higher curvature**, yet **better generalization**.

---

### 🔹 3. Perturbation Sharpness
\[
S(A1) \approx 0.1837,\qquad
S(B) \approx 0.0886
\]

BN appears **sharper**, contradicting the naive “flat minima generalize best” claim.

---

### 🔹 4. 1D Loss Slice  
Shows local geometry around the minima.

![1D Slice](figures/P2.png)

---

### 🔹 5. Mode Connectivity (A1 ↔ A2)  
Linear interpolation reveals a **loss barrier**, meaning the minima lie in different basins.

![Mode Connectivity](figures/P3.png)

---

## 🧩 **Discussion: What We Learned**

### ⭐ BatchNorm generalizes better **despite** being sharper  
This challenges the classical belief that flat minima generalize better.

### ⭐ Local curvature ≠ global geometry  
Curvature metrics like λ_max or SAM sharpness are **incomplete** descriptors.

### ⭐ Basin topology matters  
A1 and A2 minima are separated by a loss barrier → distinct basins.

### ⭐ Architecture strongly shapes optimization  
BatchNorm influences:
- gradient flow  
- curvature  
- sensitivity  
- basin structure  

---

## 🏁 **Conclusion**

This project provides a structured and empirical analysis of how architectural choices—specifically **Batch Normalization**—shape the loss landscape in deep networks.  
While BN improves optimization speed and generalization, it also **increases curvature and sharpness**, demonstrating that generalization depends on far more than simply “flatness”.

The work emphasizes the importance of:
- combining multiple geometric probes,  
- understanding global topology, and  
- analyzing the interaction between architecture and optimization noise.

## 📎 **Full Report**

For complete theoretical derivations, plots, and explanations, see:

📄 **[DA24M014_REPORT.pdf](DA24M014_REPORT.pdf)**  

---

## 👤 **Author**
**Rajat Abhijit Kambale**

---




