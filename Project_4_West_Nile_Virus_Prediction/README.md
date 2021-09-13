# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png)  Project 4: West Nile Virus Prediction
---
Mubina | Wei Hua | Liubin  

## Problem Statement
Our client is the Centers for Disease Control and Prevention (CDC) who are working with Chicago government to reduce the patients whom are affected by the incurable West Nile Virus. Our team are given a chance to work with Department of Public Health to set up a surveillance control system.

As a data scientist from a consultancy firm, our task is to build a model and make predictions to determine the period and location of the sprays. We will also be conduting a cost-benefit analysis which include the annual cost projections for various levels of pesticide and quantity of the pesticide spraying to achieve the maximum benefit.

Our primary stakeholders will be the client (CDC) and the secondary stakeholders will be the government of Chicago. The given dataset consist of the following data:

- Main dataset where public health workers in Chicago set up mosquito traps across the city to test for the presence of West Nile virus. 
- Spray data which records the details of their spraying such as location and date in order to reduce the number of mosquitoes in the area. 
- Weather Data which records the condition of the city. It is believed that hot and dry conditions are more favourable for West Nile virus as compared to cold and wet. 
- Map from openstreet map 

The model will then be evaluated by ROC AUC score and recall score. The objective of the model is to get a high  ROC AUC score and recall score.

## Executive Summary
The following is the general workflow for this project:
1. [Data cleaning](##Data-cleaning)
2. [Exploratory Data Analysis](##Exploratory-Data-Analysis)
3. [Pre-processing and feature engineering](##Pre-processing-and-feature-engineering)
4. [Modelling and evaluation](##Modelling-and-evaluation)
5. [Conclusion](##Conclusion)
6. [Cost benefit analysis](##Cost-benefit-analysis)
7. [Recommendation](##Recommendation)

## Modelling and evaluation
|Models|Recall|ROC AUC|True Positives|False Positive|True Negatives|False Negatives|
|---|---|---|---|---|---|---|
|Logistic Regression|0.725|0.848|66|274|1330|25|
|KNN classifier|0.736|0.720|67|622|982|24|
|Random Forest classifier|0.747|0.844|68|313|1291|23|
## Conclusion
Random Forest classifier is the best model because:
1. Least cross validation score difference of 12% even though the model is still overfitting.
2. Highest recall score with the least False Negatives. False negative is important as we have to identify potential locations before it leads to a big outbreak of virus.
3.  Achieve similar ROC AUC score for logistic regression and random forest classifier.

In conclusion, random forest classifier has ROC AUC score of 84% and recall score of 75%. With the classification model, it can be used to reduce false negative which means less positive case are identify as negative.

The top features identified are mainly location, period of the year and weather conditions.

- Location-longitude and latitude
- Days since max wnv present, day of the year and August
- Wetbulb temperature, sealevel and dewpoint

The benefit of the model will be:
1. Primary Stakeholder - To optimise the spray for prevention
2. Secondary Stakeholder - To prevent virus infection in the community

## Cost benefit analysis
In summary, it is more economical to spray the whole city with pesticides in order to prevent any potential west nile virus outbreak.
Benefits from mosquito spraying would include increased quality of life from fewer people falling sick and fatalities, increased workplace productivity by reducing the number of people falling sick, as well as savings in hospital expenses from treating WNV patients. Of these, only the latter two are calculated as shown in the table above.

With the help of the model, we found that WNV is more prevalent under certain conditions. Location - longtitude and latitude was the top predictor, followed by day of year, days since maximum WNV, 21-days rolling mean of wet bulb temperature, August, and 14-days rolling mean of dewpoint. This means that WNV is most likely to occur in the North of Chicago especially in August and this is where and when spray efforts should be prioritised to maximise the benefit of the pesticide spray.

Our team also suggest that educating the public on prevention of breeding mosquitoes is better than cure. We can implement it as part of the children education and put up more poster for awareness. The best way to prevent mosquitoes breeding is to avoid stagnant water.

## Recommendation
As for the prediction model, we hoped to improve the model by :
1. To collect more data to have a more balance dataset
2. To reduce noise by reducing unimportant features
3. To better understand the impact of environment to the number of mosquitoes by having lesser missing data
4. To collect more recent data for better predictions

## Appendix
### Train Dataset

|Feature|Type|Dataset|Description|
|:---|:---|:---:|:---|
|date|datetime|train|date that the wnv test is performed|
|address|object|train|approximate address of the location of trap (send to geocoder)|
|species|object|train|species of mosquitoes|
|block|int|train|block number of address|
|street|object|train|street name|
|trap|object|train|id of the trap|
|addressnumberandstreet|object|train|approximate address retuned from geocoder|
|latitude|float|train|latitude returned from geocoder|
|longitude|float|train|longitude returned from geocoder|
|addressaccuracy|int|train|accuracy returned from geocoder|
|nummosquitos|int|train|number of mosquitoes caught in trap|
|wnvpresent|int|train|whether west nile virus was present in this mosquitoes (1 - present, 0 - not present)|

### Spray Dataset

|Feature|Type|Dataset|Description|
|:---|:---|:---:|:---|
|date|datetime|spray|date of pesticides spraying|
|time|object|spray|time of pesticides spraying|
|latitude|float|spray|north-south distance measurement (location) of spray|
|longitude|float|spray|east-west distance measurement (location) of spray|

### Weather Dataset

|Feature|Type|Dataset|Description|
|:---|:---|:---:|:---|
|station|int|weather|different weather stations|
|date|datetime|weather|date of weather forecast|
|tmax|int|weather|maximum temperature (Fahrenheit)|
|tmin|int|weather|minimum temperature (Fahrenheit)|
|tavg|object|weather|average temperature (Fahrenheit)|
|depart|object|weather|temperature departure from normal (Fahrenheit)|
|dewpoint|int|weather|average temperature of dew point (Farenheit)|
|wetbulb|object|weather|average temperature of wet bulb (Farenheit)|
|heating|object|weather|heating - seasons begins in july (Based 65 Farenheit)|
|cooling|object|weather|cooling - seasons begins in january (Based 65 Farenheit)|
|sunrise|object|weather|time fo sunrise|
|sunset|object|weather|time fo sunset|
|codesum|object|weather|weather types|
|depth|object|weather|depth of snow - from ground (inches)|
|water1|object|weather|water equivalent (inches)|
|snowfall|object|weather|snowfall (Based on inches & tenths)|
|preciptotal|object|weather|water equivalent due to rainfall & melted snow (Based on inches & hundreths)|
|stnpressure|object|weather|average station pressure (Based on inches)|
|sealevel|object|weather|average sea level pressure (Based on inches)|
|resultspeed|float|weather|resultant wind speed (Based on miles per hour)|
|resultdir|int|weather|resultant direction (Based on whole degrees)|
|avgspeed|int|weather|average speed(Based on miles per hour)|

### Project planning
This is the [link](https://docs.google.com/spreadsheets/d/1Mf_rOQT043UL6CQwaP-Wx0SBXX_oEWUg55d2J6JJuT0/edit#gid=0) to our project planning. 
