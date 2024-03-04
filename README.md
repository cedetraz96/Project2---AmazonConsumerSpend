# Amazon Product Stars & Best Seller Prediction

## Project Overview
We developed a predictive model using Amazon consumer spending data from 
Kaggle to forecast product star ratings and best seller status. The dataset 
comprises 1.4M products and was meticulously cleaned and prepared for modeling.

## Data Preparation
- Merged products and categories files to enhance dataset
- Cleaned null values, duplicates, and NaN values.
- Initial column categories after merge, asin, title, imgUrl, productURL,stars, reviews, price, listprice, category_id, isBestSeller, boughtinlastmonth, id, category_name
- Dropped irrelevant columns like imageURLs, productURLs, and IDs.
- Reordered and renamed columns for clarity.
- Updated column headings, Category, Product Description, Stars, Reviews, Price, List Price, Best Seller, Product Volume
- Identified and removed reviews and list price due to having over 1 million 0 values out of 1.4 million listing to improve model accuracy.
- New column headings, Category, Product Description, Stars, Price, Best Seller, Product Volume, Total Spend

## Feature Engineering
- Added total spend column since we were thin on data but had price and volume. By adding this feature, it can capture patterns and relationships between spending behavior and the target variable. 
- Using .apply(), condensed the characters of lengthy product descriptions to reduce dimensionality
- Ran IQR (interquartile range) to check for outliers with each column heading
- Led us to find 2 outliers with Price and Product Volume, further analysis using count the number of negative values found there were actually 0 negative values for each, these were left alone
- Applied label encoding to categorical variables, category name, product description and best seller to make it compatible with the other data

## Model Development
Initially chose Linear Regression based on the simplicity of our dataset. It provides straightforward interpretations between the features and the target variable. While predicting stars and best seller, R-squared was under 1%, mean squared error and root mean squared error were 1.1, all indicating poor predictive performance. Even after the iterative improvements, the model still had very low scores. With these results, we abandoned Linear Regression for Random Forest. This model captures nonlinear relationships between features and the target variable, identifies the most influential features and discards irrelevant ones.  And, when it discovers outliers or noisy observations it’s less likely to have significant impact to the overall predictions. 

## Random Forest Model
Due to a limited time, kept same features and target variable since we still wanted to predict stars and best seller. 
Hyperparameters n_estimator and random_state, were the only ones adjusted but those showed insignificant changes in the accuracy score. 
For predicting stars, received an accuracy score of 0.728 and for best seller 0.993. For both target variables, it correctly predicted the model.  But for comparison, a baseline model is needed or find the industry standards.   

For next steps, it would of benefit to create subsets for bootstrap samples to reduce overfitting and provide an estimate, of model performance by training on diverse subsets. Add in other hyperparameters such as tree depth and minimum samples per leaf to help optimize performance. And, try different evaluation metrics such as, F1 score and area under the ROC curve which takes in to account class imbalance and identify false negatives and positives. 

## Results and Analysis
- The initial Linear Regression model produced inadequate predictions.
- Random Forest showed promise with high accuracy scores, but with potential overfitting.
- Best Seller predictions showed high accuracy, whereas Stars predictions were moderate.

## Conclusion
The project concludes with a high-performing Random Forest model. However, caution is 
advised due to potential overfitting, as indicated by the unusually high accuracy scores 
for the Best Seller predictions.

