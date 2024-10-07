# fraudprediction

# Introduction
Fraud is constantly on the rise alongside technology. This makes fraud detection important. The big obstacle is to understand how to detect fraud. This project aims to understand which features have better ability to predict fraud. This is done with a credit card fraud dataset that gets analysed with supervised machine learning using the XGBoost algorithm. 

# Dataset
The dataset is taken from Kaggle (https://www.kaggle.com/datasets/kartik2112/fraud-detection). It consists of 23 columns and X transactions. 

# Insights from EDA with visualisations

Insights:
- Transactions amounts are very skewed and fraudulent transactions only take on values from around 1 to 1400 USD
- Most transactions are made during weekends and during 21:00-22:00 in the evening
- Grocery shopping on location and shopping online are the most common categories of fraudulent transactions. 
- Age does not have a clear pattern when it comes to fraud, as it is very unevenly distributed.


Make dashboard with amount, categories, age, time


# Analysis and conclusion

To understand the most important features, I am using four measures:
- Feature importance: The XGBoost model can list the features that most contributed to the predictions.
- Permutation importance: explain
- SHAP values: explain
- Correlation matrix: Thsi matrix showcases how correlated the feature is to the fraud. 

insert correlation matrix
- Amount, merchant fraud percentage, zip code fraud percentage, and category are the most correlated with the is_fraud variable, while distance between user and merchant, weekday, and state are the least correlated.

Insert feature importance and permutation importance plots. shap plot

In general, amount, category, and hour have the most effect on predicting fraud. 
Amount seems to have higher predicting power according to permutation importance, correlation matrix, and SHAP values. 
Category is the most important feature according to the feature importance, with amount being a close second. Category and hour switches between being on the second and third places as important feature. The exception is the correlation analysis, where previous fraud in the form of percentage of fraud for merchants and zip codes were more important than hour. Age is also an important factor. 

Amount should be examined further. It was the feature with highest explaining power, but the relationship between amount and fraud seems quite fragmented. All fraudulent transactions in the dataset were in the 0-2000 USD group, with no high outliers. The overwhelming majority of all transactions were in the same range, with some outliers. Therefore, it is difficult to say if a certain amount predicts fraud and the feature should be examined for how it predicts fraud. CAtegory seems to interact with amount and should also be examined further. 

Age: according to the SHAP summary plot, higher age seems to both increase and decrease the likelihood of being scammed. Age seems to be mildly important according to the correlation and feature importance, but low importance with SHAP. 

Previous fraud: Previous fraud seen to zip codes and merchants are moderately correlated with fraud, but is less important to predict fraud with the machine learning model. Zip code previous fraud percentage has low importance seen to the SHAP values, but is higher seen to the feature importance, while merchant previous fraud is the other way around. 

Location and time based variables did not have effect on predicting fraud, with the exception of hour. This could infer that the hour can predict fraud, as the EDA showed that most fraud take place during 21:00-22:22 in the evening. Month was moderately correlated with fraud but did lose all its importance for the machine learning model. 

Recommendations: Focus on amount, categories, hour, with previous fraud and age as complement. The variables amount and category should be explored to understand how they predict fraud and how they interact. 
