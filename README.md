# SVM Hyperparameter Optimization on Wine Quality Dataset 🍷

This project demonstrates Support Vector Machine (SVM) classification with random hyperparameter search on the **Wine Quality (White Wine)** dataset from the UCI Machine Learning Repository. The goal is to explore the effect of different kernel types and regularization parameters (C) over multiple samples and iterations.

---

## 📂 Dataset

- **Source:** [UCI Machine Learning Repository – Wine Quality](https://archive.ics.uci.edu/ml/datasets/wine+quality)
- **File Used:** `winequality-white.csv`
- **Rows:** ~4898
- **Classes:** Wine quality ratings (multi-class, typically from 3 to 9)

---

## 🧠 Objective

- Run SVM on 10 different train-test splits (70%-30%)
- In each sample, perform **100 iterations** of randomized hyperparameter search:
  - Vary kernel type (`linear`, `rbf`, `poly`, `sigmoid`)
  - Vary `C` parameter between 0.1 and 10
- Track and report:
  - Best accuracy for each sample
  - Best kernel and `C` parameter
  - Convergence graph for the best-performing sample

---

## 🛠️ Libraries Used

- `numpy`
- `pandas`
- `matplotlib`
- `scikit-learn`
- `requests`

---

## 📊 Outputs

1. **Results Table** (top 10 samples):
    - Saved as: `svm_wine_quality_results.csv`
2. **Convergence Plot** (for best-performing sample):
    - Saved as: `svm_wine_quality_convergence.png`

---

## 📁 File Structure

```bash
.
├── svm_wine_quality_optimization.py     # Main Python script
├── svm_wine_quality_results.csv         # Best accuracies + parameters for each sample
├── svm_wine_quality_convergence.png     # Convergence graph of accuracy over iterations
└── README.md                            # Project description and instructions
