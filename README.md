# 📊 Customer High Revenue Classification using AutoGluon

## 🧾 Project Overview

This project uses the **AutoGluon** library to build a classification model that predicts whether a customer will generate high revenue (`high_revenue`). The input data contains user information such as demographics, browser details, IP location, and browsing behavior.

---

## 🛠️ Technologies Used

- Python 3.12.5  
- AutoGluon v1.3.0  
- Scikit-learn  
- Pandas

---

## 📁 Input Data Structure (`customers_labeled.csv`)

The dataset contains 10 columns and 10,787 records:

| Column               | Description                                        |
|----------------------|----------------------------------------------------|
| `customerID`         | Unique customer identifier                         |
| `gender`             | Gender                                             |
| `age_first_order`    | Age at first purchase                              |
| `user_agent_brand`   | Browser used                                       |
| `user_agent_os`      | Operating system                                   |
| `ip_address_geopoint`| IP location (geospatial point)                     |
| `ip_address_country` | Country derived from IP address                    |
| `campaign`           | Whether the user came from a marketing campaign    |
| `pages_visited_avg`  | Average number of pages visited                    |
| `high_revenue`       | Target label (binary: True/False)                  |

---

## 🔄 Modeling Pipeline

### 1. Data Preparation
- Load data from `.csv` file
- Split into training and testing sets (80/20, stratified)
- Combine features and labels for training/testing

### 2. Model Training
A model is trained using AutoGluon’s `TabularPredictor` with `accuracy` as the evaluation metric, a 60-second time limit, and the `best_quality` preset.

Algorithms used:
- LightGBM
- CatBoost
- XGBoost
- Random Forest
- Neural Networks (PyTorch)

### 3. Prediction & Evaluation
- Predict class labels and probabilities
- Display confusion matrix
- Display model leaderboard

---

## 📈 Results

The best-performing model achieved **~90.9% accuracy** on the validation set. AutoGluon automatically performed model stacking and ensemble selection.

---

## ▶️ How to Run

1. Install required dependencies:
   ```bash
   pip install autogluon pandas scikit-learn
2.	Run the Jupyter Notebook or execute the code in a Python environment.
3.	Models and output will be saved automatically in the AutogluonModels/ directory.

## 📌 Notes
- The file customers_labeled.csv should be placed in the data/ folder.
- AutoGluon handles preprocessing and feature encoding automatically.
- If you encounter Ray or CatBoost-related errors (TimeLimitExceeded), reduce model complexity or increase the training time limit.

Project developed as part of predictive modeling exercises for PUM class at PJATK
