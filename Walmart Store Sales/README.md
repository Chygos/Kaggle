<h2><pre>Walmart Recruiting - Store Sales Forecasting
Use historical markdown data to predict store sales</pre></h2>


## Data Description
<a href="https://www.kaggle.com/c/walmart-recruiting-store-sales-forecasting/data">LINK TO DATASET</a>

You are provided with historical sales data for 45 Walmart stores located in different regions. Each store contains a number of departments, and you are tasked with predicting the department-wide sales for each store.

In addition, Walmart runs several promotional markdown events throughout the year. These markdowns precede prominent holidays, the four largest of which are the Super Bowl, Labor Day, Thanksgiving, and Christmas. The weeks including these holidays are weighted five times higher in the evaluation than non-holiday weeks. Part of the challenge presented by this competition is modeling the effects of markdowns on these holiday weeks in the absence of complete/ideal historical data.

stores.csv
This file contains anonymized information about the 45 stores, indicating the type and size of store.

train.csv
This is the historical training data, which covers to 2010-02-05 to 2012-11-01. Within this file you will find the following fields:

Store - the store number
Dept - the department number
Date - the week
Weekly_Sales -  sales for the given department in the given store
IsHoliday - whether the week is a special holiday week

test.csv
This file is identical to train.csv, except we have withheld the weekly sales. You must predict the sales for each triplet of store, department, and date in this file.

features.csv
This file contains additional data related to the store, department, and regional activity for the given dates. It contains the following fields:

Store - the store number
Date - the week
Temperature - average temperature in the region
Fuel_Price - cost of fuel in the region
MarkDown1-5 - anonymized data related to promotional markdowns that Walmart is running. MarkDown data is only available after Nov 2011, and is not available for all stores all the time. Any missing value is marked with an NA.
CPI - the consumer price index
Unemployment - the unemployment rate
IsHoliday - whether the week is a special holiday week
For convenience, the four holidays fall within the following weeks in the dataset (not all holidays are in the data):

Super Bowl: 12-Feb-10, 11-Feb-11, 10-Feb-12, 8-Feb-13
Labor Day: 10-Sep-10, 9-Sep-11, 7-Sep-12, 6-Sep-13
Thanksgiving: 26-Nov-10, 25-Nov-11, 23-Nov-12, 29-Nov-13
Christmas: 31-Dec-10, 30-Dec-11, 28-Dec-12, 27-Dec-13


## APPROACH
**BASELINE:**
<p>As a baseline, the raw features were used with minor feature engineering (extracting time related features). Four models -A linear model (Ridge regression) and three non-linear models (RandomForest, Ligthgbm  and Catboost Regressors)- were fitted separately to the data.</p>
Firstly, the dataset was split into training and validation sets, where the models were fit to the training data and validated on the validation set.
<p>For the Ridge regression, categorical features were handled as thus: Target encoding for categorical features with high cardinality and One-Hold Encoding of low cardinality features. Because target encoding is prone to overfitting, it was fit on the training dataset and then transformed on both the train and validation sets, with some smoothing value.</p>
<p>The target (dependent) variable was higly right-skewed. It was transformed using the fourth root and retransformed back to the original in the powers of 4</p>
<p>The Lightgbm and Catbost Regressors (boosting regressors) were weight-averaged</p>

Baseline LederBoard scores include:
<pre>
                              Private              Public 
Ridge:                        9198.62970         8842.37452
RandomForest:                 7024.50207         6692.94328
LGBRegressor:                 3363.43185         3242.61268
CatBoostRegressor:            3681.95941         3584.77631
Voting(catboost+Lightgbm):    3398.73423         3290.16334
</pre>

### Ideas for model Improvement
<ol>
  <li>Feature Engineering and Selection: Some features may not be predictive of the Weekly sales.</li>
  <li>Hyperparameter Tuning to find optimal values </li>
  <li>Ensembling or stacking models</li>
</ol>
   
 ### Packages
 scikit learn, lighgbm, catboost, missingno, pandas, numpy, matplotlib, scipy



