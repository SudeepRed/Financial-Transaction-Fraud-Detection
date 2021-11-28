# Financial Transaction Fraud Detection
## Motivation
- Fraud Detection is a vital topic that applies to many industries including banking, insurance, law enforcement and government agencies. 
- Fraud instances have seen a rise in the past few years so this topic is as critical as ever. Thus we need to be able to distinguish between authentic and fraudulent financial transactions. As the world moves towards digitization more transactions become cashless. 
- The use of credit cards and online payment methods have increased. Increase in fraud rates in these kinds of transactions causes huge losses for financial institutions and users. Thus we did a comprehensive review of the various methods to detect fraud.
### Papers used for Literature review
1. [Credit card Fraud Detection Using Machine Learning and Data Science](https://www.researchgate.net/publication/336800562_Credit_Card_Fraud_Detection_using_Machine_Learning_and_Data_Science)
2. [A Predicting Model For Accounting Fraud Based On Ensemble Learning](https://ieeexplore.ieee.org/abstract/document/9557545?casa_token=Cn5XE1XPJsAAAAAA:fy2z6aH_pb1TtHtq6WdfqYdfOndMGh1w4VTR-MV1tza59nGCR2XwSj3TCwo_UNEjFzwyXEVZVUMJ)

## Dataset description
- [Kaggle Dataset Link](https://www.kaggle.com/ealtman2019/credit-card-transactions)

We used a synthetic Credit Card Transaction Dataset from kaggle. Most credit card transaction data contains privileged information and having PCA done on the columns and feature analysis is not possible. The data contains 24,000,000  transactions for 2,000 synthetic consumers from the US. The data also covers gender, debt, income and Fico Score data. Analysis on the data shows that it is a reasonable match for real data in terms of fraud rates, purchase amounts etc. 
Out of the transactions only 30,000 are fraudulent in nature. Thus it is highly skewed in nature and the authentic transactions are downsampled to 270,000 to help increase precision and f1 scores.

1. The dataset consisted of 3 csv files containing transaction, user and card data. These were merged using customer id and card index values as keys. 
2. The dataset is composed of attributes such as user, card, amount, transaction error, card type, age, gender, yearly income, fico score etc. 
3. Attributes such as year, month, state, zip code, card cvv, number of cards issued, expiry date, card number, latitude and longitude of users, name etc. were dropped as they have low correlation with the nature of transaction.
4. All the categorical variables were encoded to suit the model. 
5. All string objects were mapped to integer values. 

## Pre Processing
- After merging the dataset was shuffled. We plotted the distributions and box plots of the features.  Made a correlation heat map of the features. The data was split 8:2 for test and train. 
- Copies of the dataset were made with min-max scaling, standard scaling and robust scaling pre-processing techniques were used to determine optimal pre-processing methods.

## Methodology
- **Logistic Regression**  
  - It was used over different sets of pre processed data and metrics such as confusion matrix, f1_score, precision and recall were recorded. 
  - Precision-recall vs thresholds were plotted to find the optimal value at which both precision and recall were high. 
  - Implemented Grid search to find the best permutation of parameters which would give the maximum precision-recall and accuracy. 
  - Parameters over which grid search was implemented include different solvers, l2 penalty and different values of regularisation strengths
- **Naive Bayes**
  - The naive bayes classifier was used against different sets of pre processed data. 
  - We then used different metrics to determine how different preprocessing steps performed.

- **Decision Trees**
  - We used a Decision Tree classifier on the same dataset with 3 different types of preprocessing. 
  - Then compared it with different metrics such as accuracy, precision, recall and f1 scores.

- **Random Forest Classifier**
  - Random Forest builds multiple decision trees and merges for a more accurate and stable prediction. This allows it to correct the overfitting problem of decision trees.  
  - Number of trees taken in the forest is 100.

- **Support Vector Machine**
  - SVM was used after doing PCA of the dataset. The number of components required were selected by taking the components comprising 95% variance of the data, which came out to be 10 components from 16 . 
  - The regularization parameter was set to 0.1,1,10 and gamma was set to 0.1, 0.01. The kernel was set to “rbf”.
- **Neural Network**
  - A multi-layered perceptron was used on the training data.A Neural Network with hidden layer sizes 16, 8, 4, 2  and max iterations of 1200. 
  - The models were compared over different activations namely relu, sigmoid and tanh. Precision, recall, f1 score and accuracy were computed and plotted as well as the ROC curves.
## Analysis
- **Logistic Regression**  
  - Training Accuracy-0.894
  - Testing Accuracy-0.891
  - Logistic Regression performs best when the preprocessing is robust scaling
  - The optimal threshold for the model was approximately 0.15 where the precision and recall value is approximately 0.3
  - Standard model gave best results as compared to results obtained from models part of grid search.

- **Naive Bayes**
  - Training Accuracy - 0.881
  - Testing Accuracy - 0.883
  - Naive bayes performs best when the preprocessing is robust scaling
  - The optimal threshold for the model was approximately 0.82 where the precision and recall value is approximately 0.2


- **Decision Trees**
  - Training Accuracy - 0.999
  - Testing Accuracy - 0.941
  - Decision Tree performs best when the preprocessing is robust scaling. It has a max depth of 38.


- **Random Forest Classifier**
  - Training Accuracy-0.999
  - Testing Accuracy-0.961
  - Random Forest performs best with raw data.


- **Support Vector Machine**
  - Training Accuracy - 0.9018
  - Testing Accuracy - 0.9022
  - Precision Score For training - 0.676
  - Precision Score For testing - 0.660
  - Recall for testing- 0.1914 
  - F1 for testing - 0.296
  - SVM performed best with regularization set to 1 and gamma set to 0.1.

- **Neural Network**
  - Best Training Accuracy - 0.94184
  - Best Testing Accuracy - 0.93996
  - Best Precision Score For training - 0.81244
  - Best Precision Score For testing - 0.80132
  - Best Recall for training- 0.60666
  - Best Recall for testing- 0.59188
  - Best F1 for training- 0.69463
  - Best F1 for testing - 0.68086
  - Neural networks worked best with tanh activation
 
| Model | Accuracy | Presicion | Recall | F1 |
| ----------- | ----------- |---|---|---|
| Logistic Regression | 89.3 | 4.9 | 60.3 | 9.08 |
|  Random Forest |  96.1 | 90.2|72.0|80.60|
| Decision Trees | 94.2 | 72.5|74.2|73.30|
| Naive Bayes|  88.3| 40.7|18.8|25.70|
| SVM |  90.22|66.0|19.14|29.6|
| Nueral Nets |  93.99|80.13|59.18|68.08|

## Conclusion
1. With all the tested models the best results were seen with Random Forest Classifiers with an accuracy of 96.1% and with high precision, recall and f1 score of 90.2, 72.0 and 80.6 respectively. 
2. It was seen that oversampling fraud data and undersampling non-fraudulent data allowed for the models to train better and have better f1 scores and were robust enough to detect outliers.
3. In the majority of the models the best results were seen with robust scaling of the data.

## Member Contributions
1. **Aruj Deshwal**-Random Forest, Pre-Processing, Literature Review, finding Dataset, Hyperparameter tuning, Neural Network.
2. **Abhinav Rawat**- Pre-Processing, Logistic Regression, Data Cleaning, Feature analysis ,Finding Dataset, Hyperparameter tuning.
3. **Sudeep Reddy**- Literature Review, feature analysis, Decision Tree, Naive Bayes, Pre-processing , SVM.





