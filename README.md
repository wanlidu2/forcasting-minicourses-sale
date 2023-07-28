# forcasting-minicourses-sale
This is a weekly playground competition held by Kaggle. The datasets can be found at https://www.kaggle.com/competitions/playground-series-s3e19.
As the dataset has a date column, I want to explore ideas about time series and xgboost in machine learning.

## Overview of data and forecast requirements

-1 Datasets

Train.csv has 6 columns: id, date, country, store, product, and num_sold. 

Test.csv has 5 columns: id, date, country, store, and product.

The sample_submission shows that we must submit a csv document with id and num_sold prediction.

The target value as the y variable is the number of mini-courses sold with a given id and other features.

-2 Evaluation

Submissions are evaluated on SMAPE between forecasts and actual values. We define SMAPE = 0 when the actual and predicted values are both 0.
https://en.wikipedia.org/wiki/Symmetric_mean_absolute_percentage_error

Symmetric mean absolute percentage error (SMAPE or sMAPE) is an accuracy measure based on percentage (or relative) errors. It is usually defined[citation needed] as follows:

![image](https://github.com/wanlidu2/forcasting-minicourses-sale/assets/121735612/06ec5345-ef6d-4588-8954-8e50a5a32ee5)

## Analytical Approach

-1 Data Wrangling

First of all, we need to import libraries that will be used in the next steps. After we read the files successfully, we can take a overview of it. For example, we can use df.dtypes, df.info(), df.describe() to take a look at the columns and the features of that. Commonly, we will have numerical and catigorical features, which can help us make further analysis and prediction.

Besides, there are some useful commands to check the data condition, such as df.nunique() to check the unique value of each column, df.duplicated().sum() to check whether there exists duplicate rows, df.corr() to see the correlation between every two columns, df.isnull().sum() to find out whether there is the missing value we need to fix.

-2 EDA Exploratory Data Analysis

In the training dataset, we can divide the features which can be useful to predict the target value as well as y. Simply we have these techniques:

summary statistics;

data visualization;

correlation analysis;

checking for missing values;

identifying outliers;

dimensionality reduction.

-3 Data Type Convert

For the datasets with date column, we can use 'pd.to_datetime' to extract useful time information such as year, month, day.

-4 Data Visualization

-5 Machine Learning

-6 Feature Engineering

-7 Time Regression

-8 Prediction on Test File
