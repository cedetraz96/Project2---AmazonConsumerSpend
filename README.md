# Amazon Product Stars & Best Seller Prediction

## Project Overview
We developed a predictive model using Amazon consumer spending data from 
Kaggle to forecast product star ratings and best seller status. The dataset 
comprises 1.4M products and was meticulously cleaned and prepared for modeling.

## Data Preparation
- Merged products and categories files.
- Cleaned null values, duplicates, and NaN values.
- Dropped irrelevant columns like imageURLs, productURLs, and IDs.
- Reordered and renamed columns for clarity.
- Condensed lengthy product descriptions.
- Identified and removed columns with a significant number of zero values to improve model accuracy.

## Feature Engineering
- Introduced 'Total Spend' as a new feature.
- Conducted outlier detection and addressed issues without altering the dataset integrity.
- Applied label encoding to categorical variables.

## Model Development
We experimented with a Linear Regression model, tweaking features and encoding
methods to optimize predictions. Despite the efforts, the model underperformed, 
leading us to switch to a Random Forest approach.

## Random Forest Model
- Implemented as a series of decision trees.
- Encoded categorical variables and defined features.
- Split the data into training and testing sets.
- Configured with `n_estimators=128` and `random_state=78` for reproducibility.
- Achieved an accuracy score of 0.728 for stars prediction and 0.993 for best seller prediction, which indicated potential overfitting.

## Results and Analysis
- The initial Linear Regression model produced inadequate predictions.
- Random Forest showed promise with high accuracy scores, but with potential overfitting.
- Best Seller predictions showed high accuracy, whereas Stars predictions were moderate.

## Conclusion
The project concludes with a high-performing Random Forest model. However, caution is 
advised due to potential overfitting, as indicated by the unusually high accuracy scores 
for the Best Seller predictions.

