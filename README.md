# SVM Hyperparameter Optimization on Wine Quality Dataset 🍷

This project demonstrates **Support Vector Machine (SVM)** classification using random hyperparameter search on the **Wine Quality (White Wine)** dataset from the UCI Machine Learning Repository. The objective is to evaluate the impact of different kernels and regularization parameters on classification accuracy through repeated experiments.

---

## 📂 Dataset

- **Source:** [UCI Machine Learning Repository – Wine Quality](https://archive.ics.uci.edu/ml/datasets/wine+quality)
- **File Used:** `winequality-white.csv`
- **Instances:** 4898 samples
- **Features:** 11 chemical properties (e.g., acidity, alcohol)
- **Target:** Wine quality scores (multi-class, typically from 3 to 9)

---

## 🎯 Methodology

1. **Sampling**:
   - Perform 10 train-test splits using `train_test_split` with a 70-30 ratio.
   - Each split has a different random seed (`random_state = 0` to `9`).

2. **Preprocessing**:
   - Apply `StandardScaler` for feature normalization before training.

3. **Hyperparameter Search**:
   - For each of the 10 samples, run **100 random trials**.
   - In each trial, randomly choose:
     - `C`: Regularization parameter ∈ [0.1, 10]
     - `Kernel`: One from the following (using aliases mapped to sklearn-compatible names):

       | Alias       | Actual Kernel |
       |-------------|----------------|
       | rbfdot      | rbf            |
       | polydot     | poly           |
       | vanilladot  | linear         |
       | tanhdot     | sigmoid        |
       | laplacedot  | rbf            |
       | anovadot    | poly           |

   - Train an SVM using the selected `C` and kernel.
   - Evaluate using `accuracy_score` on the test set.
   - Store the best accuracy and corresponding parameters per sample.

4. **Result Tracking**:
   - Save results in a CSV file.
   - Track the **best performing sample** across all 10 for convergence plotting.

---

## 📊 Results Table

| Sample # | Best Accuracy | Best Parameters (Kernel, C) |
|----------|---------------|------------------------------|
| S1       | 0.6553        | ('rbfdot', 3.52)             |
| S2       | 0.6624        | ('vanilladot', 7.21)         |
| S3       | 0.6683        | ('polydot', 1.14)            |
| ...      | ...           | ...                          |
| S10      | 0.6794        | ('rbfdot', 2.88)             |

📁 **Saved as**: `svm_wine_quality_results.csv`

📝 **Explanation**:
- Each row corresponds to one of the 10 random train-test splits.
- "Best Accuracy" is the highest test set accuracy found after 100 random trials.
- "Best Parameters" shows which kernel and `C` value led to that accuracy.

---

## 📈 Results Graph: Convergence Plot

- The graph shows the **change in best accuracy** over 100 iterations for the **sample that achieved the overall highest accuracy**.
- The y-axis represents the best accuracy found so far.
- The x-axis represents each of the 100 trials.
- This visual helps understand how quickly the optimization converges toward a good solution.

---

## 📁 File Structure

```bash
.
├── SVM.py     # Main Python script
├── svm_wine_quality_results.csv         # Output results table
└── README.md                            # Project description and documentation
