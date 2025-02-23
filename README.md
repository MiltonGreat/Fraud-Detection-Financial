# Fraud Detection in Financial Transactions

This project focuses on detecting fraudulent transactions in a dataset of financial transactions using **machine learning techniques**. The goal is to build a robust system that can identify fraudulent activities while minimizing false positives and false negatives.

While the classification model performed exceptionally well, the anomaly detection model requires further refinement to reduce false positives and false negatives. By combining supervised learning (classification) and unsupervised learning (anomaly detection), we created a system that not only detects known patterns of fraud but also identifies unusual transactions that may indicate new or evolving fraud schemes.

---

## Project Overview

Fraud detection is a critical task in financial institutions to prevent financial losses and protect customers. This project uses a combination of **classification models** and **anomaly detection** to identify fraudulent transactions. The key steps include:
- **Exploratory Data Analysis (EDA)**: Understanding the dataset and identifying patterns.
- **Feature Engineering**: Creating new features to improve model performance.
- **Classification Model**: Training a Random Forest classifier to predict fraudulent transactions.
- **Anomaly Detection**: Using Isolation Forest to detect unusual transactions that may indicate fraud.
- **Model Evaluation**: Assessing the performance of the models using metrics like precision, recall, and ROC-AUC.

---

## Dataset

The dataset contains financial transactions with the following columns:
- `step`: Maps a unit of time (1 step = 1 hour).
- `type`: Type of transaction (e.g., CASH-IN, CASH-OUT, DEBIT, PAYMENT, TRANSFER).
- `amount`: Amount of the transaction.
- `nameOrig`: Customer who initiated the transaction.
- `oldbalanceOrg`: Balance of the origin account before the transaction.
- `newbalanceOrig`: Balance of the origin account after the transaction.
- `nameDest`: Customer who is the recipient of the transaction.
- `oldbalanceDest`: Balance of the destination account before the transaction.
- `newbalanceDest`: Balance of the destination account after the transaction.
- `isFraud`: Indicates whether the transaction is fraudulent (1) or not (0).
- `isFlaggedFraud`: Indicates whether the transaction was flagged as fraud by the system.

---

## Approach

1. **Exploratory Data Analysis (EDA)**:
   - Analyze the distribution of transactions, fraud cases, and key features.
   - Visualize correlations and patterns in the data.

2. **Feature Engineering**:
   - Create new features such as:
     - `balance_change_org`: Change in the origin account balance.
     - `balance_change_dest`: Change in the destination account balance.
     - `transaction_ratio`: Ratio of the transaction amount to the origin account balance.
     - `is_large_transaction`: Flag for transactions over a certain threshold (e.g., 200,000).

3. **Classification Model**:
   - Train a Random Forest classifier to predict fraudulent transactions.
   - Handle class imbalance using techniques like SMOTE or class weights.
   - Evaluate the model using metrics like precision, recall, F1-score, and ROC-AUC.

4. **Anomaly Detection**:
   - Use Isolation Forest to detect unusual transactions.
   - Compare detected anomalies with actual fraud labels to evaluate performance.

5. **Model Evaluation**:
   - Assess the performance of both the classification model and anomaly detection.
   - Analyze feature importance to understand the key drivers of fraud detection.

---

## Results

### Classification Model
- **Confusion Matrix**:
  [[1906133 218]
    [ 10 2425]]

- **Classification Report**:

          precision    recall  f1-score   support
       0       1.00      1.00      1.00   1906351
       1       0.92      1.00      0.96      2435

  - **ROC-AUC Score**: 0.9985

### Anomaly Detection
- **Detected Anomalies**: 31,282 false positives and 531 true positives.
- **Anomaly Detection Performance**:

          precision    recall  f1-score   support
       0       1.00      1.00      1.00   6354407
       1       0.02      0.06      0.03      8213

  
---

## Future Improvements

1. **Tune Anomaly Detection**:
 - Adjust the `contamination` parameter and experiment with other algorithms (e.g., Local Outlier Factor, One-Class SVM).

2. **Feature Engineering**:
 - Explore additional features or transformations to improve model performance.

3. **Real-Time Deployment**:
 - Deploy the model as an API for real-time fraud detection.
 - Continuously monitor and retrain the model with new data.

4. **Hyperparameter Tuning**:
 - Use GridSearchCV or RandomizedSearchCV to optimize model hyperparameters.

---

## Source

https://www.kaggle.com/datasets/ealaxi/paysim1/data
