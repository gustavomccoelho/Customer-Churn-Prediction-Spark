## Problem definition

The goal of this project is to predict customer churn* by using the given features. 

*Churn definition: Amount of customers that stopped using your company's product or service during a certain time frame

##  Data description

train.csv - the training set
test.csv - the test set 

Both the train and test datasets are made of 20 features, including the target feature ("churn").

##  Script strategy

The scrip is entirely made on Apache Spark framework.

Exploratory-Analysis.ipynb:

After the basic exploratory analysis is in place, e.g. looking for NA values, data balance, etc., we see the following correlation matrix:  

![corr-1](/pictures/corr-1.png)

We can see from this matrix that there are features with very high correlation with each other, such as total_day_minutes x total_day_charge (probably because the customer is charged by minutes of use).

The first step is to remove this features, resulting in the following correlation matrix:

![corr-2](/pictures/corr-2.png)

Following, two specific features are analysed more deeply, and new level features are made according to their clear relation to the target:

![number_customer_service_calls](/pictures/number_customer_service_calls.png)
![number_customer_service_calls_level](/pictures/number_customer_service_calls_level.png)
![total_day_charge](/pictures/total_day_charge.png)
![total_day_charge_level](/pictures/total_day_charge_level.png)

Finally, the least significant features related to the target are removed (correlation less than 0.1)

Predictive-Model.ipynb:

The data created from the previous script is loaded and the predictions are taken place.

Gradient Boosting Classifier was used, giving the following result in the test dataset:

Gradient Boosting Classifier accuracy: 0.91
