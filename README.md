
# Increasing Vaccine Adoption in Your City
<p align="center">
  <img src="images/flubanner.jfif" alt="">
</p>

#### Team Members
Dietrich Nigh, Parker DeShazo

#### Summary of Repository Contents:
* National 2009 H1N1 Flu Survey data acquired from  [Driven Data](https://www.drivendata.org/competitions/66/flu-shot-learning/page/211/)
* Exploratory Notebooks from each member of this group
* A copy of our [final presentation(FinalPresentation.pdf)] in PDF format
* A copy of our [final notebook](FinalNotebook.ipynb) containing detailed analysis and accompanying code

## Business Understanding of Problem



#### Limitations of Our Data

* No data on rents
* Data set did not include any information on unimproved lots
* Models are not predictive
* No data on development price

## Bottom Line

Through the proper setting and thoughtful allocation of lot real estate, profits can be maximized when developing in the Seattle Metro.

## Data Preparation

At the outset, the data was not in a usable state and preliminary cleaning needed to be performed.
Some of the data was unusable due to missing values. These categories were:
* 
Additional data manipulation was done via a ColumnTransformer within our pipeline.
* Categorical and Numeric data was imputed 
* Categorical data was oridinally encoded to be usealbe
* Numeric data was standard scaled
Data was then seperated into train and test sets to prevent data leakage.

## Simple Model

![](images/)



## Exploratory Modelling

![](images/)


#### Model Tuning


## Final Model
After removing factors due to their insignificance or due to multicollinearity, our final model included the following predictors:
* opinion_seas_risk              2.104511
* doctor_recc_seasonal           1.894827
* opinion_seas_vacc_effective    1.853458
* age_group                      1.326044
* health_worker                  0.723932
* opinion_seas_sick_from_vacc    1.509126

![Final Regression Model](images/final_multiple_reg.png)

Despite removing 26 predictors, our final model only lost approximately 0.5% of its predictive power from the largest logistical regression model. The limited number of predictors affords this model more value for municipalities with limited resources. 


#### Implications (Coefficients)

* 
* 
* 
* 
* 

