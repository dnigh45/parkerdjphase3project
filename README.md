# Insights for Site Development in Seattle
<p align="center">
  <img src="images/seattleskyline.jpg" alt="">
</p>

#### Team Members
Dietrich Nigh, Rachael McCue, Jake Swecker

#### Summary of Repository Contents:
* Data set containing King County housing information provided by Flatiron School
* Exploratory Notebooks from each member of this group
* A copy of our final presentation in PDF format
* A copy of our final notebook containing detailed analysis and accompanying code

## Business Understanding of Problem

The stakeholder of interest is a site developer in the Seattle metropolitan area. 

In the context of this project, the developer was looking to develop a vacant lot anywhere in Seattle proper. The developer is neither interested in renovating a home nor are they interested in purchasing the lowest-cost lot. Instead, their focus is on maximizing profits through the proper home characteristics. This means looking at features surrounding the home as well as the configuration of the lot, i.e. the layout of the home, garage, and patio. With all this in mind, our model seeks to provide them with the characteristics to focus on when choosing and then developing the lot to attain maximal profits.

#### Analyzed Factors

bedrooms, bathrooms, sqft_living, sqft_lot, floors, waterfront, greenbelt, nuisance, sqft_above, sqft_basement, sqft_garage, sqft_patio, yr_built, basement, patio, garage

#### Unaddressed Factors

lat, long, zipcode (beyond belonging to the Seattle Metro), address, yr_renovated, heat_source, view, grade, condition

#### Limitations of Our Data

* No data on rents
* Data set did not include any information on unimproved lots
* Models are not predictive
* No data on development price

## Bottom Line

Through the proper setting and thoughtful allocation of lot real estate, profits can be maximized when developing in the Seattle Metro.

## Data Cleaning

At the outset, the data was not in a usable state and preliminary cleaning needed to be performed.
* Categorical data was processed into dummy data for exploration.
* ppsq_living and ppsq_lot were engineered.
* The data was filtered using zipcode to Seattle proper.
* Tiny homes were removed (< 400 living sq.ft. )
* Basement, patio, and garage presence were engineered
* Unaddressed factors were dropped from the dataset
* Outliers of price and sqft_lot were dropped
* Homes built before 2013 were removed

## Simple Model

![Simple Regression Model](images/simple_reg.png)

Our simple model focused on sqft_above. With an R-Squared of 0.41, our model had room for improvement. 

## Initial Complex Model

![First Multiple Regression Model](images/first_multiple_reg.png)

The first attempt at improving our simple model took the kitchen sink approach. We used 16 predictors, all of the analyzed factors listed above, to construct the regression. This gave much more explanatory power of the variance in price. The kitchen sink approach gave us an adjusted R-squared of 0.55, over a 30% improvement.  Despite this predictive power, this model was far too complex to be useful to our stakeholders and had an unacceptably high condition number of 4.63x10<sup>16</sup>.

#### Filtering Process

Several further iterations of our model were made to simplify what would otherwise be an unruly model.

Using statistical significance as a means of excising factors, we began removing variables from the model. After this filtering, our model contained 6 predictors. However, a check for multicollinearity was run befroe accepting this as our final product. We discovered that sqft_above and sqft_lot were highly correlated.

![Coveriance of Model Factors](images/covar.png)

As such, we decided to remove sqft_lot from the model. Square footage of the lot, while important to home price, will not be a mutable characteristic for our developer. This makes the predictor less relevant to our stakeholders. Additionally, its removal reduces the explanatory power of our model less than the removal of sqft_above.

## Final Model
After removing factors due to their insignificance or due to multicollinearity, our final model included the following predictors:
* sqft_above
* basement presence
* sqft_garage
* sqft_patio
* nuisance presence

![Final Regression Model](images/final_multiple_reg.png)

Despite removing 11 predictors, our final model only lost approximately 2% of its predictive power with an adjusted R-squared value of 0.53. The limited number of predictors affords this model more value for stakeholders. 


#### Implications (Coefficients)

* For every sqft increased above ground, price increases by $468.59
* If a basement is added, price increases by $201427.49
* For every sqft increased in a garage, price decreases by $267.58
* For every sqft increased on a patio, price increases by $274.12
* If a nuisance is present, price decreases by $48570.84

What do these numbers mean?

Predictably, the presence of a nuisance near the developed home will result in a tangible decrease in the price. While not something that can be changed, the development company should be cognizant of any potential annoyances, like excessive traffic noise from a nearby highway, prior to selecting a lot. 

Our stakeholders will be pleased to hear that garages are not valued in the Seattle market. With garage square footage decreasing the value of the home, this expensive bit of construction can be done without.  Garages, additionally, take up lot space. That square footage would be better allocated to a patio. Not only is it cheaper to build, but patio space is a lucrative addition to the home. This may be due to the high premium that private, developed outdoor space commands in urban environments. 

The most lucrative characteristics, however, were the presence of a basement and additional square footage above ground. Adding additional space above ground should be concentrated on. While patio space is valuable, above-ground living space leads to even greater increases in sale price. Independent of spacial concerns, like square footage, a basement should make its way into the final blueprints. The presence of a garage led to a massive increase in predicted price.

While profits are the primary concern, our model will allow developers to focus on the factors that are most tied to price. They will then be able to independently assess what makes the most sense when considering costs.