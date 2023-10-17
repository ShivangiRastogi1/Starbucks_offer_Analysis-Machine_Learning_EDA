# Starbucks_offer_Analysis-Machine_Learning_EDA

## Project Overview:

Maintaining customer satisfaction is a particular element Starbucks does excellently. As competition rises, though, it will be interesting to see if this is just a sociological phenomenon or if Starbucks actually values its customers' patronage. In this project, I'll describe how I use experimental data provided by Starbuck which contains simulated data that mimics customer behavior on the Starbucks rewards mobile app and it is based on customer's past purchases to identify the groups and deals that individuals are most interested in. Starbucks delivers offers to customers who use its mobile app every few days. An offer might BOGO (buy one, get one free) or it might be free drinks deal. To identify which group responds favorably to which offers, I have utilized this dataset to examine transactions, demographics, and the offer portfolio.

## Problem Statement:
Analyzing client behavior and interactions with promotional offers provided via the app is the aim of this project. I am trying to find a reliable technique to link customers' offer selections with their demographic data by first understanding the types of people they are. The project's goal is to determine the most profitable offer based on the customer's demographics.

* I will first investigate customers demographics and transcript data.
* Then I will combine the offer portfolio, customer profile, and transaction data. One DataFrame will be generated representing the total amount of transaction with an offer's attributes and customer demographic data. Data visulisation will be performed on the data.
* Clustering was used to help group the members based on their purchasing behavior, which should further our understanding. Further, combined data will be split into training and testing sets. Regression will be used to predict the transaction amount based on demographic.
* I will assess Sum of Squares (SSE) which calculates the sum of the squared differences between each observation and its group's mean. It can be used as a measure of variation within a cluster.Parameters will be optimized for the regression models. The performance of each regression model will be compared.


Structure Of the Project:

* Analysis: Data exploration and visualization
* Clustering:
  1. k-means clustering
* Modelling
 *    Decision Tree, Random forest
* Discussion and Conclusion

After performing analysis below questions can be answered:

##### Q1 - Who are our customers, and what are their demographics?
##### Q2 - What is the age ranges for starbucks customer?
##### Q3 - What is the relationship between Gender , Income and age?
##### Q4 - What age group affects Starbucks income?
##### Q5 - Is the subscription program useful and used by customers?
##### Q6 - What is the relationship between the customer attributes?
##### Q7 - What is the age and gender distribution in Starbucks customers?
##### Q8 - What is the most preferred channel and offers?
##### Q9 - What are the characteristics of cutomers transcripts?
##### Q10 - What is  the completion rate and view rate of offers?
##### Q11 - What is the customers retention rate, and customer churn rate?
##### Q12 - What is the average completion time of an offer?
##### Q13 - What are the characteristics of customers interactions with the offers?
##### Q14 - Gender distribution in each offer type
  
## Metrics
The evaluation of model will be using The sum of squares error

* **The sum of squares error (SSE)** or residual sum of squares (RSS, where residual means remaining or unexplained) is the difference between the observed and predicted values.

* ## Data Loading and Preprocessing

* ### Data Sets

The dataset utilized for this project was a simulation of the information that Starbucks gathered about its customers' past purchases over the course of one month. There were three sets of data in json format:

* Portfolio: contains offer type (BOGO, discount, informational), difficulty (minimum required to spend to complete an offer), reward (reward given for completing an offer), duration (time for the offer to be open), and channels (email, web, mobile, social) for the offers. [*portfolio.json*](https://github.com/ShivangiRastogi1/Starbucks_offer_Analysis-Machine_Learning_EDA/blob/main/portfolio.json) 

* Profile: contains information of each individual customer including: age, the date when customers created an app account, gender, customer id, and income.  [*profile.json*](https://github.com/ShivangiRastogi1/Starbucks_offer_Analysis-Machine_Learning_EDA/blob/main/profile.json) 

* Transcript: a record of all activities relating to the customers in Profile. Data includes: record description (ie transaction, offer received, offer viewed, etc.), customer id, time in hours since start of test. The data begins at time t=0, offer id, and transaction amount. https://www.kaggle.com/datasets/blacktile/starbucks-app-customer-reward-program-data

Here is the schema and explanation of each variable in the files:

**portfolio.json** 
* id (string) - offer id
* offer_type (string) - type of offer ie BOGO, discount, informational
* difficulty (int) - minimum required spend to complete an offer
* reward (int) - reward given for completing an offer
* duration (int) - time for offer to be open, in days
* channels (list of strings)

**profile.json**
* age (int) - age of the customer
* became_member_on (int) - date when customer created an app account
* gender (str) - gender of the customer (note some entries contain 'O' for other rather than M or F)
* id (str) - customer id
* income (float) - customer's income

**transcript.json** 
* event (str) - record description (ie transaction, offer received, offer viewed, etc.)
* person (str) - customer id
* time (int) - time in hours since start of test. The data begins at time t=0
* value - (dict of strings) - either an offer id or transaction amount depending on the record
