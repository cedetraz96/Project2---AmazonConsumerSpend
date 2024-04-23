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
Initially chose Linear Regression based on the simplicity of our dataset. It provides straightforward interpretations between the features and the target variable. While predicting stars and best seller, R-squared was 1.1, mean squared error and root mean squared error were 1.79 and 
1.34, respectively, all indicating poor predictive performance. Even after the iterative improvements, the model still had very low scores. I did use the accuracy score and it was also 0.011. With these results, we abandoned Linear Regression.  Asking Gen AI, it recommended Random Forest. Maybe we needed a model to capture nonlinear relationships between features and the target variable, or identify the most influential features and discard irrelevant ones or when it detects outliers or noisy observations it’s less likely to have significant impact to the overall predictions. Or all of the above.  

## Random Forest Model
Due to time, we had time for one iteration with Random Forest. We kept the same features still wanting to predict stars and best seller. The ‘feature importance’ graph shows the first iteration for predicting stars.   

For predicting stars, we received an accuracy score of 0.728 and for best seller 0.993.  It seems to have correctly predicted the model for stars and best seller. But for comparison, we need a baseline model or find the industry standards.   

Hyperparameters n_estimator and random_state, were the only adjustments made and those showed insignificant changes in the accuracy score. 

For next steps, it would benefit us to 
-	create subsets for bootstrap samples to reduce overfitting and provide an estimate, of model performance by training on diverse subsets. 
-	Add in other hyperparameters such as tree depth and minimum samples per leaf to help optimize performance.  
-	Lastly, try different evaluation metrics such as, F1 score and area under the ROC curve which takes in to account class imbalance and identify false negatives and positives. 

## Results and Analysis
- The initial Linear Regression model produced inadequate predictions.
- Random Forest showed promise with high accuracy scores, but with potential overfitting.
- Best Seller predictions showed high accuracy, whereas Stars predictions were moderate.
- Some iterative improvements: 
- Added ‘define threshold’ for the stars column after receiving error messages.  This converted the continuous scores into discrete class predictions to help clarify decision boundaries.  This was removed for best seller since that was converted to binary values of 0s and 1s.  
- Applied label encoder for columns with categorical text to convert into numerical format to make it compatible with the other data.  
- .apply() for Product Description to pare down the characters to reduce dimensionality to mitigate overfitting. 
- Checked for nonzero values and found 2 more columns to drop, each had more than 70% - 0 values
- Due to the error message and time constraints, we decided against adding dummy variables believing it would not provide an accurate prediction and increase the dimensionality. Of course, it would be beneficial to use this and see what predictions are made as a comparison.  
- Lastly, added a Total Spend column since we were thin on data but had price and volume.By adding this feature, it can capture patterns and relationships between spending behavior and the target variable. 

## Conclusion
The project concludes with a high-performing Random Forest model. However, caution is 
advised due to potential overfitting, as indicated by the unusually high accuracy scores 
for the Best Seller predictions.

# sms_spam_detector
