# Project: Sparkify Churn Prediction using PySpark

## Backgound
Sparkify is a fictional music streaming service invented by Udacity. It is similar to Spotify or Pandora streaming services.
With Sparkify, users can listen to music for free (with ads) or subscribe to the platform at a flat rate fee. Users can upgrade, downgrade, or cancel their subscriptions. Every time a user interacts with the streaming service, it generates user event data. All these data contain the key insights for us to perform data analysis and to observe the behavior of users who stayed vs users who churned. **Our task is to predict the users who plan to cancel their service (i.e., potential subscribers about to churn) so we can take action**. For example: we can offer them a great discount or provide an incentive (e.g., to use the paid service free for several months) to keep them from cancelling their subscriptions so we can potentially save the business millions in revenue.

## Project Motivation
This is a Capstone project done in conjuction with Udacity as part of the requirement for the Data Science Nanodegree program.

The goal of this project is to learn how to manipulate large and realistic datasets with Spark to engineer relevant features for predicting churn. We learn how to use Spark MLlib to build machine learning models with large datasets, far beyond what could be done with non-distributed technologies like scikit-learn. Additionally, the ability to efficiently manipulate large datasets with Spark is one of the highest-demand skills in the field of data science or data engineering.


## Project Steps
The project consists of these steps:
1. **Loading and Cleaning Dataset**
2. **Exploratory Data Analysis (EDA)**
3. **Feature Engineering**
4. **Modeling Building**
5. **Model Evaluation**
6. **Compare Model results**
7. **Conclusion**

## Instructions
This project requires Python 3.x version. In order to complete this project, you need to install the following libraries:
- [pyspark](http://spark.apache.org/docs/latest/api/python/)
- [numpy](https://numpy.org/)
- [pandas](https://pandas.pydata.org/)
- [matplotlib](https://matplotlib.org/)
- [seaborn](https://seaborn.pydata.org/)
  
You will also need to have software installed to run and execute an [Jupyter Notebook](https://jupyter.org).

## Data needed for the project
This project has utilized mini subset (128MB) of the full dataset available (12GB). Optionally, you can choose to deploy a Spark cluster on the cloud using [AWS](https://aws.amazon.com/) to analyze a larger amount of data. 

**Full Sparkify Dataset:** s3n://udacity-dsnd/sparkify/sparkify_event_data.json

**Mini Sparkify Dataset:** s3n://udacity-dsnd/sparkify mini_sparkify_event_data.json

## Files Description
There are two files in this repository
1. **README.md**  
It is the file that we currrently read. It provide high level information of this project. It also provide information how to install require software and data set to run the application of this project.
2. **Sparkify_Churn.ipynb** 
It is a notebook contains all steps involved in running the application of this project

## Summary of the steps taken and Results
In this project, we start by studying the Sparkify streaming service's user event dataset. Since each user event is associated with a specific user, the user event has empty userId does not convey meaningful information when we want to predict the specific users will churn (leave/cancel the streaming services) or not. Thus, we delete user event records in which the userId is a empty string as part of the "data cleaning" process. We found that there are 225 users in total. There are 52 users who had the “Cancellation Confirmation” user event. We create a "churnFlag" to indicate the user will churn or not based on the specific users have who had the “Cancellation Confirmation” user event or not. We will use F1 scores to evaluate the model performance because of the data imbalance between churn vs non-churn users. Once we have defined churn, we perform some "exploratory data analysis" to observe the behavior for users who stayed vs users who churned. We can start by exploring aggregates on these two groups of users, observing how much of a specific action they experienced per a certain time unit or number of songs played and how it impacted churn. For example:
- Gender Distribution of No churn vs Churn Users
- The average length of the songs listened by Non churn vs churn users
- The average number of songs listened by non churn vs churn users
- The number of songs played in each hour of the day between Non Churn vs Churn users 
- User Activity Events Distribution grouped by page-action between Non Churn vs Churn users

The main point here is to find features that might be used for the churn model prediction. We then went ahead to create features that were later used in **building these four machine learning models namely: Logistic regression, Support Vector Machine(SVM), RandomForest Classification and Gradient Boosted Tree (GBT)**. We then fine-tune these four machine learning models by applying hyperparameters to each model and use 3-fold cross validation to identify the optimal hyperparameters. **Amongst these four models, the GBT performed best with the best f1 scores and accuracy although it took the longest time to train.**

## Additional
The project results are based mainly on a mini subset of the data (128MB), so it is recommended to finish the project with the full dataset (12GB). It would be beneficial and effective to observe the results with the full dataset and see the differences.

More detailed findings and analysis illustrated with graphs can be found in **the blog post on** ***[Medium website](https://medium.com/@thanhta2010/do-you-know-it-professionals-for-both-males-and-females-in-us-got-paid-much-better-comparing-with-e0a4e16187a8)***

## Acknowledgments:
Thanks the Udacity team for providing this project and work space to work on as part of the ***[Data Science Nanodegree Program](https://www.udacity.com/course/data-scientist-nanodegree--nd025)***. I have gained a lot of knowledge about Big data environments using Spark and learn how to use Spark MLlib to build machine learning models with large datasets, far beyond what could be done with non-distributed technologies like scikit-learn. 
