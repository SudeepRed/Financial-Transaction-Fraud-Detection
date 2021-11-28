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




