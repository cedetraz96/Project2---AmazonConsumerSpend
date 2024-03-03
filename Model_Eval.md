
# Started with Linear Regression model
# To see what scores wre predicted, we ran the model with the dataset as is
# Predicting Stars and Best Sellers
# First test was X = Best Seller and Y = Stars, this resulted in a score/r2 of 0.00081, mse 1.807, rmse 1.3478
# Second, X = Product Volume and Y = Stars, score/r2 0.00397, mse 1.8, rmse 1.3416
# Third, X = Reviews Y=Stars, score/r2 0.001387, mse 1.8046, rmse 1.3434
# Fourth, X = Price Y= Stars, score/r2 0.00629, mse 1.7957, rsme 1.34
# Tried get dummies, but received a 'Memory Error' message that there was not enough memory available to create dummy variables.
# Changed to label encoder for the Cateogry Name, Product Description and Best Seller to convert the objects to floats
# Next it was recomemnded to condense the Product Description column which was done using .apply()
# Another action was scrutinizing the EDA again, this time we ran the number of nonzero values for each column heading
# and found that List Price and Reviews each had 1M zero values out of 1.4M.  These 2 column headings were dropped from the dataset
# instead of replacing the values, since the amount was over 70% to be replaced, we of assessed it would severally distort the predictions. 
# The dataset features were looking thin, to try and improve model performance, we added a 'Total Spend' column since we had the price and product volume
# With these changes, we tested again but, the predictions were still showing low scores or performing poorly.  
# Results were, Best Seller predictions ranged from 0.01844 - 0.0626, the score/r2 4.37, mse 0.01, rsme 0.1, unsure if there is an error in the calculation or interpretation of the metric and what we needed from Best Sellers was a 0 or 1 for the predictor. 
# For Stars predictions ranged from 3.8 - 4.3, which was promising, but score/r2 1.2, mse 1.79, rsme 1.34.  Overfitting or again, s an error in the calculation or interpretation of the metric 
# Asking Generative AI about these results from the Linear Regression, it stated that based on the datset, the Linear Regression model may be too simple and it recommended Random Forest.  
# Pivot to Random Forest Classifier
# Added define threshold for categorizing star rating since we were receiving an error message. Doing this to posisble help control the vlassification decision making process. 
# Used n_estimator=128 and random_state=78
# Received an accuracy score of 0.728
# Next we predicted Best Seller, since these were True/False, but then converted to 0 and 1s, 
# Removed define threshold. 
# Received an accuracy score of 0.993, seems a little too good to be true considering the Stars score is 0.728, define as overfitting
# Trying a different number for the n_estimators = 75 and random_state=42 for both the Stars and Best Seller predictions
# Stars accuracy score 0.7279 and Best Sellers accuracy score 0.9939 this shows an insignificant change 