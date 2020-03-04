# Data Science Capstone Project
## Overview
1. Description
Student provides a high-level overview of the project. Background information such as the problem domain, the project origin, and related data sets or input data is provided.

2. Problem Statement
What does this project solve?
The problem which needs to be solved is clearly defined. A strategy for solving the problem, including discussion of the expected solution, has been made.

3. Metrics
Metrics used to measure performance of a model or result are clearly defined. Metrics are justified based on the characteristics of the problem.
Options:
- Accuracy Score
- F1 Score
- ROC Curve

## Tech Specs & Usage
1. Prerequisites
2. How to run these notebooks

## Data Wrangling
### Profile data
There are missing data about app users. These are eliminated from the project for now
Convert columns to more usable format.
Issue: we don't have lots of data about an user out of the box to make predictions about their response to an offer. So we need to use transcript data to provide more data about the user.  
Transcript data allow us to build a behavioral pattern of a user using the app. Answering these questions about the user:
1. What is each user's total spending amount on the app?
2. What is each user's influenced rate? Influenced rate is the number of offers that users viewed and completed divided by the number of offers that users received
3. How many total transactions each user made?
4. What is the average amount spent per transaction per user?

### Transcript data
Every activity is recorded separately. So I had to separate transcript data into 4 dataframes: received offers, viewed offers, completed offers, and monetary transaction. 
Merge viewed and completed offers dataframe back into the received offers so we can have 1 dataframe to keep track of whether an offer sent to a user is "influenced" by the offer

## Exploratory Data Analysis
Although "informational" offer type is included in the dataset, we should remove it from the data analysis. "Informational" offers have difficulty value of 0, which means that they do not cost Starbucks anything to send out, so we assume that Starbucks should send informational offers to _all_ of its reward users to inform them of new products. 

In this analysis, I treat the other 2 offer types, bogo and discount, separately. At this point, we do not know whether or not users who are responsive to bogo offers are also responsive to discount offers, hence, we should analyze data for these two categories of offers separately. 

Compare groups with yes response to offer with group with no response to offer on all of spectrum and observe the results
1. Users who respond yes to offers also spend more on the app in general?
- Show viz
- Use hypothesis testing 
2. How is income correlated with total spending? Do users with higher spending also have higher income? 
3. How is age related to response?
4. How is number of transactions related to response? We would normally assume that a user who is already more active on the app would be more likely to respond yes to offer?
5. We would assume that users with lots of reward points would be more likely to respond yes to offer? Is that so?
6. How does a user's membership length affect response?
7. Does a user's gender affect response?
8. Does a user's average spending amount per transaction affect their response?

Rinse and repeat for discount offer type


## Data Modeling 
Classification models:
- AdaBoost
- KMeanNeighbor 
- SVC
- MLPClassifier



## Conclusions
1. Results
2. Concerns
3. Future improvement