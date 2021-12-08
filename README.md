# Project 2 - Ames Housing Data and Kaggle Challenge

---

## Problem Statement

Given a dataset containing descriptive property/structural information about residential sales in Ames, Iowa, build a model that is able to accurately predict housing prices.

## Executive Summary

The project began with initial exploratory analysis and data cleaning to identify the best method to fill missing values. As part of the data cleaning process, some categorical variables were converted to numeric if their descriptions in Kaggle's info indicated directionality (ex. any 'Quality' variable that is low-high can be converted 1-10). the cleaned data were visualized in a number of ways to identify potential variables of interest for the modeling process. A new notebook dedicated solely to reading in the cleaned data and modeling it includes 4 models, each its own attempt to balance prediction accuracy with overall interpretability of the model's results. 

## Contents

**01_EDA**
- Read & Data
- Data Inspection
- Data Cleaning
- Feature Engineering
- Export Cleaned Data
- Exploratory Analysis & Visualization

**02_Models**
- Read & Inspect Cleaned Data
- *Model 1:* Simple One Variable Linear Regression
- *Model #2:* Logistic Regression with 3 Variables
- *Model #2.5:* Ridge Regression with 3 Variables, add GridSearchCV
- *Model #3:* Pipeline with StandardScaler, SelectKBest, Lasso, GridSearchCV (nearly all features included)

**Folders**
- datasets (provided data, and cleaned data)
- presentation (pdf of presentation slides and images from viz)
- scratch (initial submission to Kaggle)

## Data Dictionary. 

The data for this project can be found at http://jse.amstat.org/v19n3/decock/DataDocumentation.txt

Data descriptions are also found on the Kaggle project 2 competition page https://www.kaggle.com/c/dsir-907-project-2/data

## Data

- [Training Data](./datasets/train.csv)  
- [Testing Data](./datasets/test.csv)  
- [Cleaned Training Data](./datasets/ames_train_clean.csv)  
- [Cleaned Testing Data](./datasets/ames_test_clean.csv) 

## Conclusion

Model selection matters, but each could serve a different purpose. If interpretability matters to you, then the final model (that had the most accurate predictions) might not be the most useful. Based on the 64% accuracy of the single variable ('Overall Qual') Linear Regression, and the fact that model 3 only represented a slight increase in accuracy over model 2.5 despite including 150 features (compared to Model 2.5's 3 features), I feel confident that with further time and exploration a highly simplified, interpretable model could at minimum manage to generate equally accurate predictions to the models shown here. 

Based on our EDA and modeling, it is clear that features related to the location (Neighborhood) and external appearance/quality are pertinent. Model 3 showed certain roofing materials chosen as model coefficients with outsized positive values compared to the rest of the chosen features, while certain types of zoning wound up with outsized negative coefs relative to the other chosen coefs. 

Further analysis might consider a log transformation of y before running the models, and as well as investigating issues of multicolinearity that were not thoroughly explored in this project. The use case should always be considered, and if interpretability is important then taking time to identify a select few features to include in a simpler regression model is ideal. If accuracy is all that matters, then it is worth throwing as many features as possible into a pipeline and scaling before choosing an ideal regression model. 

### Sources
- #https://stackoverflow.com/questions/66109829/pandas-df-isna-sum-not-showing-all-column-names
- # https://medium.com/@chrisshaw982/seaborn-correlation-heatmaps-customized-10246f4f7f4b
- # https://moonbooks.org/Articles/How-to-plot-horizontal-lines-with-matplotlib-/#dashed-lines
- https://stackoverflow.com/questions/33952142/prevent-pandas-from-interpreting-na-as-nan-in-a-string
- #https://scikit-learn.org/stable/modules/generated/sklearn.feature_selection.SelectKBest.html
- https://stackoverflow.com/questions/39839112/the-easiest-way-for-getting-feature-names-after-running-selectkbest-in-scikit-le



