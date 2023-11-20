# credit-risk-classification
Creating a prediction model for credit risk.

​
## Overview of the Analysis
​
​
*  Objective:
​
In the context of lending institutions, risk refers to the potential for financial loss or negative impact resulting from uncertainties in a borrower's ability to repay a loan or return an asset. Lenders face various types of risks, including credit risk, market risk, and operational risk. Credit risk is a significant concern for lending institutions and is associated with the likelihood that a borrower may default on their loan obligations. To assess and manage credit risk, lending institutions often use machine learning (ML) models to predict the likelihood of a borrower being "risky" or having a higher probability of defaulting on their loan. In this study, we will employ machine learning to examine a dataset of past lending transactions from a peer-to-peer lending platform. The objective is to develop a model that can assess the creditworthiness of borrowers.A machine learning model was used to determine healthy (low-risk) from risky (high-risk) loans based on the loan status provided by the lending company.After analyzing the lending company's dataset, a logistic regression model was developed that achieved an impressive accuracy score of 99% for healthy loans. However, when it comes to distinguishing high-risk loans, the model's recall value is lower, at 91%. This suggests that the model performs better at predicting loan status as healthy rather than identifying loan status as high-risk loans. The reason for the discrepency being that the dataset has a huge  imbalance; the majority of the data corresponds to a single class label (in this case, healthy loans greatly outnumber hight_risk loans).
​
 More about the unbalanced data below:
​
​
![Data set inbalanced.](Images/fig1.png)
​
To improve accuracy and enhance the model's ability to classify high_risk loans, the RandomOverSampler module from the imbalanced-learn library can be used. This technique involves adding more copies of the minority class (non-healthy loans) to create a balanced dataset.
​
Oversampled data:
​
![Data set balanced.](Images/fig2.png)
​
​
​
## Results

​
* Machine Learning Model 1:
  * Description of Model 1 Accuracy, Precision, and Recall scores.
  
- In comparison to the original dataset, the number of healthy loans is greater than the number of unhealthy loans.
- The model has an excellent accuracy score of 99%, the precision score for `0` (healthy loans) is 100% and the precision for `1` labels is not bad at 85%.
- The recall score is also quite high at 99% for prediction of `helthy loans` and 91% for `high-risk loans` .
​
​
​
* Machine Learning Model 2:
  * Description of Model 2 Accuracy, Precision, and Recall scores.
  
The accuracy score for both prediction models is extremely high at 99%. Looking at the confusion matrix, the oversampled data model did significantly better at predicting false negatives, meaning only 4 loans were identified as negative. Similarly to the previous model, the precision score for 0 (healthy loans) was 100% and 84% to loan type 1((high-risk loan). The recall score improved for unhealthy loans compared to the previous model (from 91% to 99%) as well as the f1-score. Overall,the original model was accurate but the second model with oversampled data performed slightly better.
​
​
## Summary
​
A lending company wants a model that accurately distinguishes between healthy and non-healthy loans to minimize potential costs. Misclassifying healthy loans as non-healthy can lead to customer loss, while misclassifying non-healthy loans as healthy can result in financial losses for the company. The Logistic Regression model trained with oversampled data performed better than the model trained with imbalanced data. The balanced dataset approach improved accuracy and recall, reducing errors in classifying non-healthy loans.To mitigate risks, the lending company aims to minimize the occurrence of false positives, which represent cases where loans that are not financially sound are incorrectly identified as healthy:
​
## Machine Learning Model 1 with imbalanced data:
​
56 false positives (actual value: healthy, predicted value: non-healthy)
102 false negatives (actual value: non-healthy, predicted value: healthy)
​
## Machine Learning Model 2 with balanced data:
​
4 false positives (actual value: healthy, predicted value: non-healthy)
116 false negatives (actual value: non-healthy, predicted value: healthy)
​
​
Upon analyzing the results, it is advisable to favor Machine Learning Model 2, which was trained on balanced data. This recommendation is based on its notable reduction in false positives (4 instances of healthy loans mistakenly classified as non-healthy) compared to Machine Learning Model 1 (56 instances). The improvement in accuracy, particularly in distinguishing between healthy and non-healthy loans, reinforces the efficacy of utilizing balanced data in training machine learning models for enhanced performance in real-world scenarios. Also, It's important to note that while machine learning models can enhance credit risk assessment, they are not foolproof, and human judgment and expertise remain crucial in the decision-making process. Additionally, ethical considerations, fairness, and transparency in the use of these models are important to ensure responsible lending practices.
