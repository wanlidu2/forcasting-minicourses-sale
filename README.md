# forcasting-minicourses-sale
This is a weekly playground competition held by Kaggle. The datasets can be found at https://www.kaggle.com/competitions/playground-series-s3e19.
As the dataset has a date column, I want to sort out ideas about time series and xgboost in machine learning.

## Overview of data and forecast requirements

-1 Datasets

Train.csv has 6 columns: id, date, country, store, product, and num_sold. 

Test.csv has 5 columns: id, date, country, store, and product.

The sample_submission shows that we need to submit a csv document with id and num_sold prediction.

The target value as y variable is the number of mini-courses sold with a given id and other features.

-2 Evaluation

Submissions are evaluated on SMAPE between forecasts and actual values. We define SMAPE = 0 when the actual and predicted values are both 0.
https://en.wikipedia.org/wiki/Symmetric_mean_absolute_percentage_error

Symmetric mean absolute percentage error (SMAPE or sMAPE) is an accuracy measure based on percentage (or relative) errors. It is usually defined[citation needed] as follows:

![image](https://github.com/wanlidu2/forcasting-minicourses-sale/assets/121735612/06ec5345-ef6d-4588-8954-8e50a5a32ee5)

##
