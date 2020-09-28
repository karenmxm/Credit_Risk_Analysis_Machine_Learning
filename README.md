# Credit_Risk_Analysis

In this analysis, we build and evaluate several machine learning models to assess credit risk, using data from LendingClub, a peer-to-peer lending services company.
We first compared four resampling methods using logistic regression model. Then we evaluated the performences of two ensemble classifiers and made recomendations.

Credit card companies usually have many more non-fraudulent transactions than fraudulent ones. This is a class imbalance problem. It occurs when one class is much larger than the other class. It is a common problem in classification. We used three techniques to address class imbalance: oversampling, undersampling, and a combination approach of oversampling and undersampling. 

## Credit Risk Resampling Techniques

We compared two oversampling algorithms to determine which algorithm results in the best performance. We oversample the data using the naive random oversampling algorithm and the SMOTE algorithm. For each algorithm, be sure to complete the folliowing steps:

### Naive Random Oversampling

1. View the count of the target classes using `Counter` from the collections library. 
3. Use `imblearn.over_sampling` `RandomOverSampler` to resample data to train a logistic regression model.
3. Calculate the balanced accuracy score from sklearn.metrics.
4. Print the confusion matrix from `sklearn.metrics`.
5. Generate a classication report using the `imbalanced_classification_report` from `imbalanced-learn`.

- [Confusion Matrix](https://github.com/karenmxm/Credit_Risk_Analysis/blob/master/Images/Naive_Confusion_Matrix.png)
 
  <img src=https://github.com/karenmxm/Credit_Risk_Analysis/blob/master/Images/Naive_Confusion_Matrix.png>
 
- Balanced Accuracy Score: 66.03%

- Imbalanced Classification Report

  |               | pre | rec | spe | f1 | geo | iba | sup |
  | :-------------|-----|-----|-----|----|-----|-----|-----|
  | high_risk     | 0.01 | 0.74 | 0.58 | 0.02 | 0.66 | 0.44 | 101 |
  | low_risk      | 1.00 | 0.58 | 0.74 | 0.73 | 0.66 | 0.42 | 17104 |
  | avg / total   | 0.99 | 0.58 | 0.74 | 0.73 | 0.66 | 0.42 | 17205 |


### SMOTE Oversampling

1. View the count of the target classes using `Counter` from the collections library. 
3. Use `imblearn.over_sampling` `SMOTE` to resample data to train a logistic regression model.
3. Calculate the balanced accuracy score from sklearn.metrics.
4. Print the confusion matrix `sklearn.metrics`.
5. Generate a classication report using the ` classification_report_imbalanced` from `imbalanced-learn`.

- [Confusion Matrix](https://github.com/karenmxm/Credit_Risk_Analysis/blob/master/Images/SMOTE_Confusion_Matrix.png)

  <img src=https://github.com/karenmxm/Credit_Risk_Analysis/blob/master/Images/SMOTE_Confusion_Matrix.png>

- Balanced Accuracy Score: 65.37%

- Imbalanced Classification Report

  |               | pre | rec | spe | f1 | geo | iba | sup |
  | :-------------|-----|-----|-----|----|-----|-----|-----|
  | high_risk     | 0.01 | 0.62 | 0.68 | 0.02 | 0.65 | 0.42 | 101 |
  | low_risk      | 1.00 | 0.68 | 0.62 | 0.81 | 0.65 | 0.43 | 17104 |
  | avg / total   | 0.99 | 0.68 | 0.62 | 0.81 | 0.65 | 0.43 | 17205 | 


### Undersampling

We also used an undersampling algorithms to determine which algorithm results in the best performance compared to the oversampling algorithms above. We undersample the data using the Cluster Centroids algorithm and complete the folliowing steps:

1. View the count of the target classes using `Counter` from the collections library. 
3. Use `imblearn.under_sampling` `ClusterCentroids` method to resample the data to train a logistic regression model.
3. Calculate the balanced accuracy score using `sklearn.metrics` `balanced_accuracy_score` method.
4. Print the confusion matrix `sklearn.metrics`.
5. Generate a classication report using the `classification_report_imbalanced` from `imblearn.metrics`.

- [Confusion Matrix](https://github.com/karenmxm/Credit_Risk_Analysis/blob/master/Images/Undersampling_Confusion_Matrix.png)

  <img src=https://github.com/karenmxm/Credit_Risk_Analysis/blob/master/Images/Undersampling_Confusion_Matrix.png>

- Balanced Accuracy Score: 54.75%

- Imbalanced Classification Report

  |               | pre | rec | spe | f1 | geo | iba | sup |
  | :-------------|-----|-----|-----|----|-----|-----|-----|
  | high_risk     | 0.01 | 0.68 | 0.41 | 0.01 | 0.53 | 0.29 | 101 |
  | low_risk      | 1.00 | 0.41 | 0.68 | 0.58 | 0.53 | 0.27 | 17104 |
  | avg / total   | 0.99 | 0.41 | 0.68 | 0.58 | 0.53 | 0.27 | 17205 | 
  
  
### Combination (Over and Under) Sampling

We test a combination over- and under-sampling algorithm to determine if the algorithm results in the best performance compared to the other sampling algorithms above. We resample the data using the SMOTEENN algorithm and complete the folliowing steps:

1. View the count of the target classes using `Counter` from the collections library. 
3. Use the `imblearn.combine` `SMOTEENN` method to resample data to train a logistic regression model.
3. Calculate the balanced accuracy score using `sklearn.metrics` `balanced_accuracy_score` method.
4. Print the confusion matrix from `sklearn.metrics`.
5. Generate a classication report using the `classification_report_imbalanced` from `imblearn.metrics`.

- [Confusion Matrix](https://github.com/karenmxm/Credit_Risk_Analysis/blob/master/Images/CombinationSampling_Confusion_Matrix.png)

  <img src=https://github.com/karenmxm/Credit_Risk_Analysis/blob/master/Images/CombinationSampling_Confusion_Matrix.png>
  
- Balanced Accuracy Score: 64.48%

- Imbalanced Classification Report

  |               | pre | rec | spe | f1 | geo | iba | sup |
  | :-------------|-----|-----|-----|----|-----|-----|-----|
  | high_risk     | 0.01 | 0.72 | 0.57 | 0.02 | 0.64 | 0.42 |  101 |
  | low_risk      | 1.00 | 0.57 | 0.72 | 0.72 | 0.64 | 0.40 | 17104 |
  | avg / total   | 0.99 | 0.57 | 0.72 | 0.72 | 0.64 | 0.40 | 17205 | 

## Credit Risk Ensemble Techniques

We compared two ensemble algorithms to determine which algorithm results in the best performance. We trained a Balanced Random Forest Classifier and an Easy Ensemble AdaBoost classifier. For each algorithm, we complete the folliowing steps:

1. Train the model using the training data.
2. Calculate the balanced accuracy score from `sklearn.metrics`.
3. Print the confusion matrix from `sklearn.metrics`.
4. Generate a classification report using the `classification_report_imbalanced` from `imblearn.metrics`.
5. For the Balanced Random Forest Classifier only, print the feature importance sorted in descending order (most important feature to least important) along with the feature score

### Balanced Random Forest Classifier

 - [Confusion Matrix](https://github.com/karenmxm/Credit_Risk_Analysis/blob/master/Images/Rf_Confusion_Matrix.png)
 
   <img src=https://github.com/karenmxm/Credit_Risk_Analysis/blob/master/Images/Rf_Confusion_Matrix.png>

 - balanced_accuracy_score is: 78.55%
 
 - Imbalanced Classification Report

  |               | pre | rec | spe | f1 | geo | iba | sup |
  | :-------------|-----|-----|-----|----|-----|-----|-----|
  | high_risk     | 0.04 | 0.67 | 0.90 | 0.07 | 0.78 | 0.59 | 101 |
  | low_risk      | 1.00 | 0.90 | 0.67 | 0.95 | 0.78 | 0.62 | 17104 |
  | avg / total   | 0.99 | 0.90 | 0.67 | 0.94 | 0.78 | 0.62 | 17205 |


### Easy Ensemble AdaBoost Classifier

 - [Confusion Matrix]()
 
 - <img src=>
 
 - balanced_accuracy_score is: 93.17%
 
 - Imbalanced Classification Report

  |               | pre | rec | spe | f1 | geo | iba | sup |
  | :-------------|-----|-----|-----|----|-----|-----|-----|
  | high_risk     | 0.09 | 0.92 | 0.94 | 0.16 | 0.93 | 0.87 |  101 |
  | low_risk      | 1.00 | 0.94 | 0.92 | 0.97 | 0.93 | 0.87 | 17104 |
  | avg / total   | 0.99 | 0.94 | 0.92 | 0.97 | 0.93 | 0.87 | 17205 |

