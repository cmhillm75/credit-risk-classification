# Credit Risk Classification Module 20 Supervised Learning

## Repo Setup

* Folder Credit_Risk - `lending_data.csv` and `credit_risk_classification.ipynb`

## Imports Used

* numpy, pandas, pathlib, matplotlib, seaborn
* sklearn.metrics, train_test_split
* LogisticRegression, confusion_matrix, classification_report

## Overview of the Analysis

I completed 2 models, LogisticRegression `lr_model` and RandomForest `rf_model`.

* The purpose of the analysis is to build a model that can identify the creditworthiness of borrowers and correctly identify low_risk (0) and high_risk (1) loans.
* The dataset included 77,536 specific loan data with a breakdown of loans in low risk (0) n = 75,036 and high risk (1) n = 2,500.
* Both the lr_model and rf_model trained on 19,384 loans which is 25% of the dataset. I did not change from the default training setup.

## Logistic Regression Model

* The use of a logistic regression model in anaylyzing the credit worthiness is appropriate due the prediciton of the probablities in the outcome that the loan is low risk or high risk.
* Separate the data into variable labels (y) and features (X).
* Split the data into training and testing with train_test_split.
* Scale the data with StandardScaler for the lr_model only.
* Create the `lr_model = LogisticRegression`
* Make predictions with the (X_test_scaled).
* Created a scatterplot with the features of `debt_to_income` and `loan_size`. This showed that the dataset was setup perfectly to show that as the dollar amount of the loan increaseed, so did the `debt_to_income` level. The plot shows that all the high risk (1) loans are the higher dollar amount loans.

## Model Evaluation

### Confusion Matrix - lr_model

* 18,652 Low_Risk loans correctly indentified, 99.95%.
* 113 High_Risk loans incorrectly identified, 15.63%.
* 9 Low_Risk loans incorrectly identified, 0.05%.
* 610 High_Risk loans correctly identified, 84.37%.

### Classification Report - lr_model

```plaintext
precision    recall  f1-score   support

  Low_Risk       1.00      0.99      1.00     18765
 High_Risk       0.84      0.99      0.91       619

  accuracy                           0.99     19384
 macro avg       0.92      0.99      0.95     19384
 weighted avg    0.99      0.99      0.99     19384
```

## Random Forest Model

* The use of a Random Forest model in anaylyzing the credit worthiness is usefule in managing imbalanced data.
* Separate the data into variable labels (y) and features (X).
* Split the data into training and testing with train_test_split.
* Scaling applied as already completed.
* Create the `rf_model = RandomForestClassifier(class_weight='balanced', random_state=1)`
* Trained the modeul using the training data
* Make predictions with the (X_test).

## Confusion Matrix rf_model

* 18,664 Low_Risk loans correctly indentified, 99.70%.
* 101 High_Risk loans incorrectly identified, 15.23%.
* 57 Low_Risk loans incorrectly identified, 0.30%.
* 562 High_Risk loans correctly identified, 84.77%.

### Classification Report - rf_model

```plaintext
precision    recall  f1-score   support

  Low_Risk       1.00      0.99      1.00     18765
 High_Risk       0.85      0.91      0.88       619

  accuracy                           0.99     19384
 macro avg       0.92      0.95      0.94     19384
 weighted avg    0.99      0.99      0.99     19384
```

## Summary

* The total accuracy of the models are both 99%. high_risk loans performed slightly better with the Random Forest model however Low-Risk loans performed worse. Low-risk loans are highly predictable based on their features, and the majority of the loans in the dataset are low risk but 48 more low risk loans were incorrectly identified in the random forest model. The offset to that incorrect classification is the slight decrease in high risk loans being misclassified however 60 less high risk loans were included in the random forest model. Given the class imbalance, with a significantly larger number of low-risk loans compared to high-risk loans, these findings are very strong for both models. Both models have very high accuracy in selecting correct low risk loans and the variance on the high risk loans does mirror the difficulty in analyzing higher risk credit.

* However, determining the features of high-risk loans can be more challenging for a seasoned loan underwriter. Default risk cannot typically be assessed based on a single criterion. Multiple features need to be considered, and significant risk offsets should be present to help mitigate. A reason why there are less high risk loans in the dataset is that the majority of high risk loan applications do not get approved. So yes it is more important to find the loans that are labeled high risk but it is more complicated as the data shows. The model must also present fairly and align with the Equal Credit Opportunity Act.
[ECOA](https://www.fdic.gov/resources/supervision-and-examinations/consumer-compliance-examination-manual/documents/5/v-7-1.pdf)

## References

Data for this dataset was generated by edX Boot Camps LLC, and is intended for educational purposes only.

## License

This project is licensed under the terms of the GNU General Public License v3.0. For more details, see the [LICENSE](https://www.gnu.org/licenses/gpl-3.0.en.html) file.
