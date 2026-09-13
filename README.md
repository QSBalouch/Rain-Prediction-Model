# 🤖 Machine Learning Classification Project

## 📌 Project Overview

This project focuses on predicting a **binary target outcome** using machine learning classification algorithms. The workflow covers data exploration, preprocessing, model training, hyperparameter tuning, and performance comparison across multiple classification models.

Several models are evaluated to determine which approach provides the best generalization to unseen data.

---

## 🎯 Objective

The main objective is to build a classification model that can accurately predict the target outcome and compare different machine learning algorithms based on their performance on unseen validation data.

The project evaluates both simple linear models and tree-based algorithms to understand their strengths, weaknesses, and generalization performance.

---

## 🔧 Machine Learning Workflow

The project follows the following workflow:

```text
Data Loading
     ↓
Data Exploration
     ↓
Data Preprocessing
     ↓
Feature Preparation
     ↓
Train / Validation Split
     ↓
Logistic Regression
     ↓
Decision Tree
     ↓
Decision Tree Hyperparameter Tuning
     ↓
Random Forest
     ↓
Random Forest Hyperparameter Tuning
     ↓
Model Comparison
     ↓
Final Evaluation
```

---

## 🤖 Models Evaluated

### 1. Logistic Regression

Logistic Regression provides the initial machine learning baseline. It learns the relationship between the input features and the binary target and produces predictions for the two classes.

**Training Accuracy:** 87.42%
**Validation Accuracy:** 87.41%

The very small difference between training and validation accuracy indicates good generalization with minimal overfitting.

---

### 2. Decision Tree

Decision Tree is used to capture non-linear relationships and feature interactions that may not be represented effectively by Logistic Regression.

#### Without Hyperparameter Tuning

**Training Accuracy:** 100.00%
**Validation Accuracy:** 79.15%

The extremely high training accuracy combined with substantially lower validation accuracy indicates significant overfitting.

#### After Hyperparameter Tuning

The optimized Decision Tree uses:

* `max_depth = 7`
* `max_leaf_nodes = 58`

**Training Accuracy:** 84.40%
**Validation Accuracy:** 84.35%

The tuned model significantly reduces overfitting and produces much more consistent training and validation performance.

---

### 3. Random Forest

Random Forest combines multiple decision trees to improve predictive performance and capture complex non-linear relationships.

#### Without Hyperparameter Tuning

**Training Accuracy:** 100.00%
**Validation Accuracy:** 85.61%

The model performs considerably better than the untuned Decision Tree, although the difference between training and validation accuracy indicates overfitting.

#### After Hyperparameter Tuning

The optimized Random Forest uses:

```python
RandomForestClassifier(
    n_jobs=-1,
    random_state=42,
    n_estimators=500,
    max_features=7,
    max_depth=30,
    class_weight={'No': 1, 'Yes': 1.5}
)
```

**Training Accuracy:** 100.00%
**Validation Accuracy:** 87.13%

The tuned Random Forest improves validation performance compared with the untuned version.

---

## 📊 Model Comparison

| Model               | Training Accuracy | Validation Accuracy |
| ------------------- | ----------------: | ------------------: |
| Logistic Regression |            87.42% |          **87.41%** |
| Decision Tree       |           100.00% |              79.15% |
| Tuned Decision Tree |            84.40% |              84.35% |
| Random Forest       |           100.00% |              85.61% |
| Tuned Random Forest |           100.00% |          **87.13%** |

---

## 🏆 Final Results

The **Logistic Regression** model achieves the highest validation accuracy at **87.41%**, closely followed by the tuned Random Forest at **87.13%**.

Although the tuned Random Forest provides strong predictive performance, its **100% training accuracy compared with 87.13% validation accuracy indicates some overfitting**. In contrast, Logistic Regression has almost identical training and validation accuracy, demonstrating more stable generalization.

Based strictly on validation accuracy, **Logistic Regression is the best-performing model in this experiment**.

---

## 🔍 Key Findings

* Logistic Regression provides a strong and stable baseline.
* The untuned Decision Tree significantly overfits the training data.
* Hyperparameter tuning substantially improves Decision Tree generalization.
* Random Forest performs better than the individual Decision Tree.
* Hyperparameter tuning improves Random Forest validation accuracy from **85.61% to 87.13%**.
* Logistic Regression achieves slightly higher validation accuracy than the tuned Random Forest.
* Training accuracy alone is not sufficient for model selection; validation performance and the train-validation gap are important indicators of generalization.

---

## 🛠️ Technologies Used

* Python
* Pandas
* NumPy
* Scikit-learn
* Jupyter Notebook
* Matplotlib / Seaborn *(if used in the notebook)*

### Machine Learning Techniques

* Binary Classification
* Logistic Regression
* Decision Tree Classification
* Random Forest Classification
* Hyperparameter Tuning
* Model Evaluation
* Accuracy-based Model Comparison

---

## 📁 Project Structure

```text
Classification-Project/
│
├── Classification_Project.ipynb
├── README.md
└── dataset.csv
```

---

## 📌 Conclusion

The project demonstrates the importance of comparing different classification algorithms and controlling model complexity through hyperparameter tuning. While tree-based models achieve very high training accuracy, they can overfit without appropriate constraints. Logistic Regression provides the most stable generalization in this experiment, achieving **87.41% validation accuracy**, while the tuned Random Forest achieves a comparable **87.13% validation accuracy**.
