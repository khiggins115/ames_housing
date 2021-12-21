# Project 2 - Ames Housing Data and Kaggle Challenge

---

## Problem Statement

Given a dataset containing descriptive property/structural information about residential sales in Ames, Iowa, build a model that is able to accurately predict housing prices.

## Executive Summary

The project began with initial exploratory analysis and data cleaning to identify the best method to fill missing values. As part of the data cleaning process, some categorical variables were converted to numeric if their descriptions in Kaggle's info indicated directionality (ex. any 'Quality' variable that is low-high can be converted 1-10). the cleaned data were visualized in a number of ways to identify potential variables of interest for the modeling process. A new notebook dedicated solely to reading in the cleaned data and modeling it includes 4 models, each its own attempt to balance prediction accuracy with overall interpretability of the model's results. 

## Contents

### ***01_CODE***

> #### ***01_DataCleaning.ipynb***
> - Read in Data
> - Inspect Data
> - Data Cleaning
> - Feature Engineering
> - Export Cleaned Data

> #### ***02_EDA.ipynb***
> - Exploratory Analysis and Visualization
>    - heatmaps, distribution/histplots, scatterplots, boxplots exploring variable relationships

> #### ***03_Models.ipynb***
> - ***Model #1:*** Simple Univariate Linear Regression
> - ***Model #2:*** Multivariate (3) Regression Model(s): Comparison of Linear, Ridge, Lasso - Hypertuned parameters
> - ***Model #3:*** "Blackbox" Model: Pipeline with StandardScaler, SelectKBest, Lasso, GridSearchCV (nearly all features included)


### ***02_DATA***
> - [Training Data](../datasets/train.csv)  
> - [Testing Data](./datasets/test.csv)  
> - [Cleaned Training Data](./datasets/ames_train_clean.csv)  
> - [Cleaned Testing Data](./datasets/ames_test_clean.csv) 

### ***03_PRESENTATION***
> - PDF and PPT files used in presentation
> - image files used in presentation


## Data Dictionary. 

The data for this project can be found [here](http://jse.amstat.org/v19n3/decock/DataDocumentation.txt)

Data descriptions are also found on the Kaggle Project 2 [competition page](https://www.kaggle.com/c/dsir-907-project-2/data)


## Conclusion

Model selection matters, but each could serve a different purpose. If interpretability matters to you, then the final model (whose predictions had the lowest RMSE) might not be the most useful. The first model, a single variable ('Gr Liv Area') Linear Regression, explained approximately 51% of the variance in `SalePrice`, and had an RMSE above 80,000. Further iterations managed to increase R2 significantly while reducing RMSE to about 2/3 of its original value with our final model. 

Scoring metrics aside, Model 3 only represented a slight increase in accuracy over Model 2/2.5 despite including 150 features (compared to Model 2' 30 features - 28 of which were the OneHotEncoded Neighborhood variables). Given that Model 3's interpretability was significantly lower than the other models, I feel that Model 2/2.5 was our "best" performing model of the lot. I also feel confident that with further time and exploration and some feature engineering a highly simplified, interpretable model could at minimum manage to generate equally meaningful insights and predict `SalePrice` values with similarly low RMSE to the models shown here. 

Based on our EDA and modeling, it is clear that features related to the location (Neighborhood) and external appearance/quality are pertinent. Model 3 showed certain roofing materials chosen as model coefficients with outsized positive values compared to the rest of the chosen features, while certain types of buildings, neighborhoods (Edwards and Gilbert) and other house features (Mansard roofing, banked land contour, among others) wound up with outsized negative coefs relative to the other 150 chosen coefs. 

Further analysis might consider a log transformation of y before running the models, as well as investigating issues of multicolinearity that were not thoroughly explored in this project. The use case should always be considered, and if interpretability is important then taking time to identify a select few features to include in a simpler regression model is ideal. If generating predictions with a low RMSE is paramount, then it is worth throwing as many features as possible into a pipeline and scaling before choosing an ideal regression model. 

#### Sources
- https://stackoverflow.com/questions/66109829/pandas-df-isna-sum-not-showing-all-column-names
- https://medium.com/@chrisshaw982/seaborn-correlation-heatmaps-customized-10246f4f7f4b
- https://moonbooks.org/Articles/How-to-plot-horizontal-lines-with-matplotlib-/#dashed-lines
- https://stackoverflow.com/questions/33952142/prevent-pandas-from-interpreting-na-as-nan-in-a-string
- https://scikit-learn.org/stable/modules/generated/sklearn.feature_selection.SelectKBest.html
- https://stackoverflow.com/questions/39839112/the-easiest-way-for-getting-feature-names-after-running-selectkbest-in-scikit-le
