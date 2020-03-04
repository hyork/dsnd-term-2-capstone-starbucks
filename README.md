# Udacity Data Science NanoDegree Capstone Project
## Overview
This project's goal is to comprehensively capture the process of data science from beginning to end to solve a real world industry problem using a provide dataset. In this project, I aim to apply what I have learned throughout the Data Science NanoDegree and demonstrate my understanding and my ability to apply learning effectively. 

### Problem Statement
This data science project aims to provide insights into how Starbucks can better offer promotionals to the Starbucks rewards app users. Using demographics, transactional, and offer data, I will perform data wrangling, provide exploratory data analysis,  perform feature engineering, and build analytic models to classify users, in order "to identify which groups of people are most responsive to each type of offer, and how best to present each type of offer" (source: Starbucks Capstone Challenge Project Overview). 
The data is simulated based on real Starbucks reward app usage data.

### Metrics
Identifying and classifying users into responsive and non-responsive groups fall into the category of binary classification in data science, where we use input data as features or independent variables, to predict output data, or dependent variables. To evaluate the effectiveness of binary classification models, it is common to use **confusion matrix** and its associated measures:
1.  True Positive Rate (TPR) or Hit Rate or Recall or Sensitivity = TP / (TP + FN)
2.  False Positive Rate(FPR) or False Alarm Rate = 1 - Specificity = 1 - (TN / (TN + FP))
3.  Accuracy = (TP + TN) / (TP + TN + FP + FN)
4.  Error Rate = 1 – accuracy or (FP + FN) / (TP + TN + FP + FN)
5.  Precision = TP / (TP + FP)
6.  F-measure: 2 / ( (1 / Precision) + (1 / Recall) )
7.  ROC (Receiver Operating Characteristics) = plot of FPR vs TPR
8.  AUC (Area Under the Curve)
9.  Kappa statistics
(source: [KDnuggets](https://www.kdnuggets.com/2017/04/must-know-evaluate-binary-classifier.html)) 

## Prerequisites
This project uses the following Python libraries and versions

- `pandas` : 
- `numpy` :
- `scikit-learn` : `0.22.1`
- `matplotlib` :
- `seaborn`: 

## Data Wrangling - Profile Notebook
In this notebook, transcript and profile data are wrangled to provide a clean dataset about Rewards app users from which EDA and data modeling steps can be built later.

**Data wrangling steps**
1. Remove missing data
2. Use became_member_on to calculate a user's length of membership on the Rewards app. Drop became_member_on column
3. Add calculated columns

**Calculated features**
We don't have lots of data about an user out of the box to make predictions about their response to an offer. It only gives us 6 features: age, income, became_member_on, and gender. So we need to add calculated fields from transcript data to provide more features about the users by asking these questions:
4. What is each user's total spending amount on the app?
5. What is each user's influenced rate? Influenced rate is the number of offers that users viewed and completed divided by the number of offers that users received
6. How many total transactions each user made?
7. What is the average amount spent per transaction per user?
8. What is total amount of reward points earned by a user?

The final data set is exported as `profile_cleaned.csv` for data exploration and has an additional 5 columns: 
- total_spending
- response_rate
- total_transactions
- avg_spent_per_transaction
- total_rewards

### Transcript data
For transcript data, I separate this dataset into 4 dataframes corresponding to 4 types of activity: received offers, viewed offers, completed offers, and monetary transaction. I then merge and filter the dataframes back into 1 complete dataframe where each row records whether a user responds Yes or No to an offer type. 

The final transcript data set is exported as `offer_response.csv` for data exploration and has a total of 3 columns:
 - person
 - completed_offer
 - offer_type

## Exploratory Data Analysis
Although "informational" offer type is included in the dataset, we should remove it from the data analysis. "Informational" offers have difficulty value of 0, which means that they do not cost Starbucks anything to send out, so we assume that Starbucks should send informational offers to _all_ of its reward users to inform them of new products. 

In this analysis, I treat the other 2 offer types, bogo and discount, separately. At this point, we do not know whether or not users who are responsive to bogo offers are also responsive to discount offers, hence, we should analyze data for these two categories of offers separately. 

For each offer type, I compare Respond Yes group to Respond No group using these guidance questions and common assumptions:
1. Do users who respond yes to offers also spend more on the app in general?
2. How is income correlated with total spending? Do users with higher spending also have higher income? 
3. How is age related to response?
4. How is number of transactions related to response? (Assumption: user who is already more active on the app would be more likely to respond yes to offer)
5. Do users who respond yes also have more reward points? (Assumption: users who are engaged and motivated to earn more points would be more likely to respond yes to offers)
6. How does a user's membership length affect their response?
7. Does a user's gender affect response?
8. Does a user's average spending amount per transaction affect their response?


## Data Modeling 
Choose and build a baseline model: Logistic Regression

Choose and build other models:
- AdaBoost
- KMeanNeighbor 
- SVC
- MLPClassifier

Evaluate models using confusion matrix

## Conclusions
1. Results
2. Concerns
3. Future improvement