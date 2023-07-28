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

First of all, we need to import libraries that will be used in the next steps. After we read the files successfully, we can take an overview of it. For example, we can use df.dtypes, df.info(), and df.describe() to take a look at the columns and their features of that. Commonly, we will have numerical and categorical features, which can help us make further analyses and predictions.

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

For the datasets with a date column, we can use 'pd.to_datetime' to extract useful time information such as year, month, and day. In the further specification, we can add more new variables as indicators such as day_of_week, is_weekend, holidays_x ( x refers to each country's name given in the dataset, is_holidays. Therefore, we can get more useful numeric and Boolean values which is better for the next feature engineering and prediction.

-4 Data Visualization

In this case, we can use data visualization to have a better understanding. The number of courses sold with the change of different variables are as follows:

i Number of Courses Sold Over Time

![image](https://github.com/wanlidu2/forcasting-minicourses-sale/assets/121735612/ad79772a-c342-4af7-82c7-fdc3a5db5e84)

From the picture, we can find out that the number sold has a periodic trend and seems like appeared at each year's end and beginning.

ii Number of Courses Sold Over Time in Different stores and different countries

![image](https://github.com/wanlidu2/forcasting-minicourses-sale/assets/121735612/4f8b008a-a2ce-4ef1-ac59-010519c831f4)

iii Sales Over Time in different countries

![image](https://github.com/wanlidu2/forcasting-minicourses-sale/assets/121735612/13ff50dd-7c33-4a48-8bd7-4df44879af3d)

From the picture, we can find out that the sales number has a general uploading trend and a periodical peak every year. These generate a motivation to have more concern about periodical effects, such as the holidays and seasonality.

![image](https://github.com/wanlidu2/forcasting-minicourses-sale/assets/121735612/035b26f3-d73f-4269-bf97-b95cd2e31f98)

-5 Feature Engineering and Machine Learning

I choose to use XGBoost for the regression since the target is to predict a numeric variable. The requirement of using XGBoost is that it does not accept the object value. Then I need to get dummies of categorical columns such as countries, stores, and the name of courses first. In this procession, the value of id is not that useful for regression so we drop that when assigning X features variable. Combining with train_test_split, I set the parameters in XGBRegressor and make further predictions.

-6 Prediction on Test File

Remember the inspection standard at the beginning, we need to define a newfunction smape for further check.

When we import the test dataset, we also need to handle in the same as the train dataset in order to garantee the number and content of feature in the train dataset. That's the prerequisite of using XGBoost.

Finally, we can generate predictions and save as a new submission document.
