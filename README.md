# Bank Term Deposit Subscription Prediction

## Overview
This project aims to develop a predictive model to identify clients who are likely to subscribe to a term deposit at XYZ Bank. The analysis is based on data from the bank’s direct marketing campaigns, which include client demographics, campaign details, and economic indicators. The project involves exploratory data analysis, data preprocessing, machine learning model development, evaluation, and customer segmentation using clustering techniques.

## Table of Contents
- [Exploratory Data Analysis (EDA) Findings](#exploratory-data-analysis-eda-findings)
- [Data Cleaning & Preprocessing](#data-cleaning-preprocessing)
- [Model Training and Selection](#model-training-and-selection)
- [Results and Evaluation](#results-and-evaluation)
- [Conclusions and Recommendations](#conclusions-and-recommendations)
- [K-means Clustering](#k-means-clustering)

## Exploratory Data Analysis (EDA) Findings
The dataset consists of:
- 10 numerical features, including `age`, `duration`, `campaign`, `pdays`, and `previous`.
- 11 categorical features, including `job`, `marital`, `education`, `contact`, and `poutcome`.
- No missing values were detected, but some categorical values include "unknowns" that need handling.
- Key insights:
  - `duration`, `campaign`, `pdays`, and `previous` have significant differences between subscribed and non-subscribed clients.
  - `contact` type (cellular) and `education` level show predictive power.

## Data Cleaning & Preprocessing
- Replaced 999 in `pdays` with -1 to better reflect missing values.
- Removed collinear variables (`nr_employed`, `euribor3m`) based on Pearson correlation above 0.8.
- Encoded categorical variables using OneHotEncoder and transformed the target variable into numeric format.

## Model Training and Selection
The following machine learning models were trained using PySpark MLlib:
1. **Logistic Regression** (baseline model)
2. **Decision Tree Classifier**
3. **Random Forest Classifier**
4. **Gradient Boosted Trees (GBT)**

### Model Evaluation
| Model | AUC |
|--------|------|
| Logistic Regression | 0.935 |
| Random Forest | 0.929 |
| Gradient Boosted Trees | **0.944** |
| Decision Tree | 0.180 |

- The **GBT model** performed the best with an AUC of 0.944 and was chosen as the final model.
- The model was saved for future deployment and inference.

## Results and Evaluation
- **GBT model achieved the highest accuracy and AUC.**
- Decision Tree performed poorly, likely due to overfitting.
- Logistic Regression and Random Forest performed decently but were outperformed by GBT.

## Conclusions and Recommendations
- Focus marketing efforts on customer segments identified as likely to subscribe.
- Continuously refine the model as new data becomes available.
- Further improve feature engineering and test models on diverse datasets.

## K-means Clustering
- Used K-means clustering to segment customers into **4 clusters**.
- The optimal number of clusters was determined using the **Elbow Method**.
- Each cluster has distinct characteristics, helping to personalize marketing strategies.

### Cluster Insights:
1. **Cluster 1**: Middle-aged clients with moderate interaction duration.
2. **Cluster 2**: Older clients with longer interaction durations.
3. **Cluster 3**: Less engaged clients with lower campaign contacts.
4. **Cluster 4**: Clients showing significant economic factor variations.

