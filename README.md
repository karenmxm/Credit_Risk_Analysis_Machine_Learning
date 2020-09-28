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

- [Confusion Matrix](https://github.com/karenmxm/Credit_Risk_Analysis/blob/master/Images/Confusion_Matrix.png)
 
 <img src=https://github.com/karenmxm/Credit_Risk_Analysis/blob/master/Images/Confusion_Matrix.png>



- Imbalanced Classification Report

 |               | pre | rec | spe | f1 | geo | iba | sup |
 | :-------------|-----|-----|-----|----|-----|-----|-----|

 | high_risk     | 0.01 | 0.74 | 0.58 | 0.02 | 0.66 | 0.44 | 101 |
 | low_risk      | 1.00 | 0.58 | 0.74 | 0.73 | 0.66 | 0.42 | 17104 |
 |avg / total    | 0.99 | 0.58 | 0.74 | 0.73 | 0.66 | 0.42 | 17205 |

