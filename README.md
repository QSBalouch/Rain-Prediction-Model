# 🌧️ Rain Tomorrow Prediction

## 📌 Project Overview

This project focuses on predicting whether it will **rain the following day** using historical weather observations from different locations across Australia.

The dataset contains approximately **10 years of daily weather observations** collected from numerous Australian weather stations. It contains **23 attributes**, including the target variable `RainTomorrow`, which indicates whether or not it rains the next day.

Since `RainTomorrow` represents two possible outcomes (`Yes` or `No`), this is a **binary classification problem**.

---

## 🎯 Objective

The main objective is to build a machine learning classification model that can predict whether rain will occur on the following day based on current and historical weather conditions.

Multiple classification algorithms are trained and compared to understand how different models perform on this prediction task.

---

## 📊 Dataset

The dataset contains approximately **10 years of daily weather observations** from different locations across Australia.

The observations include weather-related information such as:

* Temperature
* Rainfall
* Humidity
* Atmospheric pressure
* Wind speed
* Wind direction
* Cloud coverage
* Sunshine
* Evaporation
* Location
* Date

The target variable is:

### `RainTomorrow`

| Value | Meaning                          |
| ----- | -------------------------------- |
| `Yes` | Rain is expected the next day    |
| `No`  | No rain is expected the next day |

---

## 🔍 Problem Type

**Supervised Learning → Binary Classification**

The model learns from historical weather observations where the next day's rainfall outcome is known and uses the learned patterns to predict whether it will rain tomorrow.

---

## 🛠️ Project Workflow

```text
Data Loading
     ↓
Data Exploration
     ↓
Data Cleaning & Preprocessing
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
Final Test Evaluation
```

---

## 🤖 Models Evaluated

### 1. Logistic Regression

Logistic Regression provides the initial classification baseline by learning the relationship between the weather features and the probability of rain occurring the following day.

**Training Accuracy:** 87.42%
**Validation Accuracy:** 87.41%

The very small difference between the training and validation accuracy indicates that the model generalizes well to the validation data.

---

### 2. Decision Tree

Decision Tree can capture non-linear relationships and interactions between weather features.

#### Without Hyperparameter Tuning

**Training Accuracy:** 100.00%
**Validation Accuracy:** 79.15%

The very high training accuracy combined with the substantially lower validation accuracy indicates significant overfitting.

#### After Hyperparameter Tuning

The optimized Decision Tree uses:

```python
max_depth = 7
max_leaf_nodes = 58
```

**Training Accuracy:** 84.40%
**Validation Accuracy:** 84.35%

The tuned model provides much more consistent training and validation performance, reducing the overfitting observed in the initial Decision Tree.

---

### 3. Random Forest

Random Forest combines multiple decision trees to capture complex relationships in the weather data while generally providing better generalization than a single decision tree.

#### Without Hyperparameter Tuning

**Training Accuracy:** 100.00%
**Validation Accuracy:** 85.61%

The model performs better than the untuned Decision Tree, although the difference between training and validation accuracy indicates overfitting.

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

Performance:

* **Training Accuracy:** 100.00%
* **Validation Accuracy:** 87.13%
* **Test Accuracy:** 86.40%

The `class_weight` setting gives additional importance to the `Yes` class, helping the model pay more attention to rain-related predictions.

---

## 📈 Model Comparison

| Model               | Training Accuracy | Validation Accuracy |
| ------------------- | ----------------: | ------------------: |
| Logistic Regression |            87.42% |          **87.41%** |
| Decision Tree       |           100.00% |              79.15% |
| Tuned Decision Tree |            84.40% |              84.35% |
| Random Forest       |           100.00% |              85.61% |
| Tuned Random Forest |           100.00% |              87.13% |

### Final Test Performance

The tuned Random Forest achieves:

**Test Accuracy: 86.40%**

The test set provides an evaluation on data that the model does not use during training or hyperparameter selection.

---

## 🔧 Hyperparameter Tuning

Hyperparameter tuning is applied to the Decision Tree and Random Forest models to control model complexity and improve generalization.

For the Random Forest, the final selected configuration includes:

* `n_estimators = 500`
* `max_features = 7`
* `max_depth = 30`
* `class_weight = {'No': 1, 'Yes': 1.5}`
* `random_state = 42`
* `n_jobs = -1`

---

## 📏 Evaluation Metric

### Accuracy

Accuracy represents the proportion of predictions that the model classifies correctly.

```text
Accuracy = Correct Predictions / Total Predictions
```

For example, a test accuracy of **86.40%** means that approximately 86 out of every 100 test observations receive the correct classification.

Because this is a rainfall prediction problem, additional metrics such as **precision, recall, F1-score, confusion matrix, and ROC-AUC** can provide further insight into how well the model identifies the `RainTomorrow = Yes` class.

---

## 🏆 Final Results

The tuned Random Forest achieves a **validation accuracy of 87.13%** and a **test accuracy of 86.40%**.

The test performance remains relatively close to the validation performance, indicating consistent performance on unseen observations. However, the **100% training accuracy** compared with the validation and test scores indicates that the Random Forest still captures patterns specific to the training data.

Logistic Regression provides a particularly stable baseline, with almost identical training and validation accuracy (**87.42% vs. 87.41%**).

---

## 💡 Key Findings

* Logistic Regression provides a strong and stable baseline.
* The initial Decision Tree heavily overfits the training data.
* Decision Tree hyperparameter tuning substantially reduces the overfitting.
* Random Forest performs better than the individual Decision Tree.
* Hyperparameter tuning improves Random Forest validation accuracy from **85.61% to 87.13%**.
* The tuned Random Forest achieves **86.40% test accuracy**.
* Training accuracy alone does not provide enough information about model generalization.
* Comparing validation and test performance provides a better understanding of how the model performs on unseen weather observations.

---

## 🛠️ Technologies Used

* **Python**
* **Pandas**
* **NumPy**
* **Scikit-learn**
* **Jupyter Notebook**
* **Matplotlib**
* **Seaborn** 

### Machine Learning Techniques

* Binary Classification
* Logistic Regression
* Decision Tree Classification
* Random Forest Classification
* Hyperparameter Tuning
* Model Evaluation
* Accuracy
* Train/Validation/Test Evaluation

---

## 📁 Project Structure

```text
Rain-Tomorrow-Prediction/
│
├── Rain_Tomorrow_Prediction.ipynb
├── README.md
└── dataset/
    └── weatherAUS.csv
```

---

## 📌 Conclusion

This project demonstrates the application of supervised machine learning to predict whether it will rain the following day using Australian weather observations. Logistic Regression provides a stable baseline, while Decision Tree and Random Forest models allow the project to capture more complex relationships in the weather data. Hyperparameter tuning improves the generalization of both tree-based approaches, with the tuned Random Forest achieving **87.13% validation accuracy and 86.40% test accuracy**. The project also highlights the importance of evaluating models on unseen data rather than relying solely on training accuracy.
