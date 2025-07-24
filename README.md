# 🛠️ Triplex Pump Fault Diagnosis using MATLAB

This project demonstrates how to use MATLAB's **Diagnostic Feature Designer** and **Classification Learner** to diagnose multiple mechanical faults in a triplex reciprocating pump based on flow and pressure signals.

---

## 📌 Project Overview

Triplex pumps are commonly used in chemical processing and fluid transport applications. Early fault detection is critical for ensuring safety and reliability. This project builds a machine learning–based diagnostic system using:

- Simulated multi-class fault data
- Feature extraction (time and frequency domains)
- Feature ranking (ANOVA)
- Classification using SVM and others

---

## 🔍 Fault Types Considered

The dataset includes **240 samples** under various fault conditions:

| Fault Code | Meaning                               |
|------------|----------------------------------------|
| 0          | No fault                               |
| 1          | Increased bearing friction             |
| 10         | Blocked pump inlet                     |
| 100        | Leaking pump cylinder                  |
| 101, 110…  | Combinations of multiple faults        |

---

## 🧪 Tools Used

- MATLAB (R2022b+)
- Diagnostic Feature Designer
- Classification Learner App
- Signal Processing Toolbox
- Statistics and Machine Learning Toolbox

---

## 📈 Key Steps & Screenshots

### 1. Raw Signal Visualization

<p align="center">
  <img src="plots/signal_trace_flow.png" width="600"/>
</p>

Grouped raw flow signals by `faultCode` using Signal Trace. Raw data overlaps significantly between fault types, necessitating feature engineering.

---

### 2. Time-Domain Feature Extraction

Extracted features like:
- Mean
- Standard deviation
- RMS
- Peak-to-peak amplitude

Applied separately on `flow` and `pressure` signals.

---

### 3. Frequency-Domain Feature Extraction

Used **autoregressive spectrum estimation (order 20)** between 23–250 Hz. Extracted:
- Spectral peaks
- Modal coefficients
- Band power

---

### 4. Feature Histogram by Fault Type

<p align="center">
  <img src="plots/histogram_features.png" width="600"/>
</p>

Visualized feature distributions to evaluate separation across fault types.

---

### 5. Feature Ranking (ANOVA)

<p align="center">
  <img src="plots/feature_ranking.png" width="600"/>
</p>

Top-ranked features:
- Flow RMS
- Pressure Mean
- Pressure RMS

---

### 6. Classification Using ML Models

<p align="center">
  <img src="plots/svm_confusion_matrix.png" width="500"/>
</p>

Trained multiple classifiers using Classification Learner with 5-fold cross-validation. Best model: **SVM with ~79% validation accuracy.**

---

## 🧠 Insights

- Raw sensor signals alone are not sufficient for fault separation.
- Frequency-domain features (especially spectral peaks) are highly informative.
- SVM outperformed other models (e.g., KNN, decision trees) in fault classification.

---

## 📁 Project Structure

