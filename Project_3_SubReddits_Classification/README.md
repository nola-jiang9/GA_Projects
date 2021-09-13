# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png)

# Project 2 - Ames Housing Price Prediction



### Problem Statement

As part of Data Science team in Ames Property Consultancy Company, I aim to use Linear Regression model to best predict residential house sales price at Ames based on fixed features and to identify the important house predictors on residential house sales price.
The target stakeholders of this new project are House Buyers, House Owner, Devleopers and Housing agent, different business suggestions will be made for stakeholders on the model predictors.

In this project, I've attempted these regression models-Linear Regression, LASSO, Ridge and Elastic Net, enhanced by feature engineering, feature selection, regularization and GridSearch. The success of the model will be measured using R-square on unseen data and the RMSE score given by Kaggle.

### Contents:

1. Data Cleaning and EDA
2. Preprocessing and Feature Engineering
3. Model and Evaluation

### Data Cleaning and EDA

1. All Data Errors have been corrected
2. All Categorical null cells were replaced with 'na' 
3. Integer or Ratio null cells were replace with 0
4. All ordinal variable were encoded using integer 

### Data Dictionary:
Analyzed & Model have been done for Ames housing data, which includes 81 features describing a wide range of characteristics of 1,460 homes in Ames, Iowa sold between 2006 and 2010. Models were required to be trained on houses sold prior to 2010 and evaluated on houses sold in 2010.

The original data dictionary may be used. It is found here: http://jse.amstat.org/v19n3/decock/DataDocumentation.txt

There were 3 featured engineered variables:

|Feature|Type|Dataset|Description|
|---|---|---|---|
|**Total SF**|*float*|df_train/df_test|Total living area, include both above ground and basement.| 
|**Total Baths**|*float*|df_train/df_test|Total number of bathrooms, include both above ground and basement bathrooms.|
|**Total Porch SF**|*float*|df_train/df_test|Total Porch Area, include 3 season porch, enclosed porch and open porch area.|
|**TotRms AbvGrd_new**|*float*|df_train/df_test|Total number of rooms above the ground, include both above ground floor bedrooms and kitchen.|
|**Age of Built**|*int*|df_train/df_test|Age of building, using year sold minus year built.|
|**has 2nd Flr**|*int*|df_train/df_test|Age of building, using year sold minus year built.|
|**has Bsmt**|*int*|df_train/df_test|0,1 to indicate whether there's basement.|
|**has Fireplace**|*int*|df_train/df_test|0,1 to indicate whether there's fireplace.|
|**has Garage**|*int*|df_train/df_test|0,1 to indicate whether there's garage.|
|**has Pool**|*int*|df_train/df_test|0,1 to indicate whether there's pool.|
|**has Porch**|*int*|df_train/df_test|0,1 to indicate whether there's porch.|

### EDA

- These are the variable that has strong to mid positive correlation to Sale Price: 

1. Overall Qual (0.8034):There seems to be strong positive correlation between overall quality material and finish of the house. The better the quality the higher the sale price.The sales price for best rated house would sold on average about 9 times more than the lowest rated house, the sales price for average rated house would sold on average about 3 times more than the lowest rated house.

3. Gr Liv Area (0.7194): There is a strong positive correlation between sale price and above grade living area square feet. The bigger the living area, the higher the sale price. There seems to be 6 outliers that does not follow the trend, it warrants further investigation. The first two outliers are extremely large houses bigger than 4000 sq feet but the sale price is very low. THe next 4 outliers are large houses around 3000 sq feet but the sale price are below the trend. 

3. Garage Area (0.6550): There's strong postive correlation between sales price and Garage Area, the bigger the Garage Area, the higher price the house would be sold. Majority houses with the Garage for 1-3 cars, houses with 3 cars' Garage have the highest Sales price, the median sale price is 297K, Q1 at 250K and Q3 at 369K. The spread is big as well.

4. Garage Cars (0.6482): Garage that can contain 3 cars has the highest sale price. The median sale price is 297K, Q1 at 250K and Q3 at 369K. The spread is big as well.

5. Age of built: There's strong positive correlation between between sales price and age of built, the yonger the house is, the higher price the house woud be sold.

### Model Selection

- Linear Regression: r2 score = -1.91757034 RMSE = 3585853900135635.0, the train score is quite good while the test score is really bad, and r2 score is negative, this probably due to the issue of overfitting and redundant features. 
- Lasso: r2 score = 0.912 RMSE = 24303(I selected Lasso as best preferred model)
- Lasso GridSearch CV: r2 score = 0.911 RMSE = 24481
- Ridge: r2 score = 0.904 RMSE = 25427 (I have picked ridge as the baseline model)
- Ridge GridSearch CV: r2 score = 0.904 RMSE = 25427 
- Elastic Net: r2 score = 0.912 RMSE = 24318

The high r2 score means that the model is able to explain over 90% of sale price variation.

## Conclusion and Recommendations

The recommendation will be based on Lasso model and inferential statistics. The recommendations will be relevant to the following stakeholders: home buyers, housing agent, developers and home sellers based on the top 5 coefficients, the simplest and the most important, the best to stakeholders to understand. The model confirms 4 broad categories: living space, quality of house, location and age of building are important predictors of a price of housing in Ames, Iowa for my business recommendations:

**The 1st Category is Living Space**

Based on Lasso model, the following coefficients related to living space are significant:   

- Total SF = Total area both above ground and below ground square feet 
  - is postively high correlated with Sales Price
  - A one unit change in total area, the sale price will increase by 46.7 dollar, holding others constant.

#### Implications for stakeholders

- Home Buyers
    - Home buyers can use living space to estimate the actual price of the house. Normally, sellers or agents will post a higher price on property portals to fetch the highest selling price. Home buyers can have a rough estimate of the actual price by assessing the total living area. As such, home buyers can give an appropriate offer to the seller so as to enhance the opportunity of securing the property. 
    - Generally for home buyers on a tight budget should avoid looking for big houses. 
- Home sellers( including house owner, devleopers, housing agent)
    -  when marketing their property, they should leverage on living area to achieve a better bargain. Living area should include basement area and garage area as they have an impact on selling price. Meaning, the bigger the area, the higher the sale price. Therefore, small houses should not be asking for a high sale price otherwise no buyer would buy. 
    - Sellers should take note or take care on the completeness of basement which it might be neglected. As an incompleted Basement area will cause your buyer have more space to bargin on the sales price.
    - Developers, when there is a limit on how big the house can be built above ground with completed basement.

**The 2nd Category is House Quality**

Based on Lasso model, the following coefficients related to house quality are significant:     

- Overall Qual = Rates of the overall material and finish of the house 
  - is postively correlated with Sales Price
  - A one unit change in total area, the sale price will increase by 9878.6 dollar, holding others constant.
  
#### Implications for stakeholders
- Home Buyers
    - Before buying a property, buyers should assess the overall material finish of the house. Houses that have execellent material finish tends to have a higher sale price as the two variables are positively correlated. Therefore, buyers need to give a higher offer to house that has a better material finish (holding other variables constant) so as to increase the probability of the offer being accepted. 
- Home sellers
    - Sellers could highlight the material quality of the house during marketing. For developers, in order to sell the house at a premium, the developer can use quality materials and ensure good worksmanship.
    - Sellers could renovate their house or at the least renovate the kitchen or exteior to boost sale price. 


**The 3rd Category is Location**

Based on lasso model, Northridge Heights & Stone Brook were found to be significant. 

- If the property is neighbored with Northridge Heights, the sale price will increase by 31676 dollar, holding other variables constant.  
- If the property is neighbored with Stone Brook , the sale price will increase by 46116 dollar, holding other variables constant.  
    
* Houses at Northridge Heights neighbourhood tend to have a higher sale price. Based on outside research the NH population is highly educated, 74% of the population has an associate degree or higher. Secondly, NH also has a very high median income 105,583 usd which is much higher than the national average of 33,706 usd. Besides that, NH houses also tends to have high rental yield, its rental yield is comparable to large cities such as Indianapolis. NH also enforce strict smoking ban in workplace, bars and restaurants which make the environment more livable. Lastly, the crime rate at NH is generally low compare to national average. These could the reasons for NH houses having a higher sale price. 

* Houses located at Stone Brooks neighbourhood is very convenient and is the closest to Iowa State University, the largest university in Iowa state. It is also very close to downtown and is just about a 10 minute drive away. The Northridge Heights and Stone Brooks are situated close together and is slightly further away to then University but is equidistant to downtown as compared to Stone Brook neighbourhood. 

* Moreover both these 2 neighbourhoods are very close to elementary, middle and high schools and have amenities really close by.  

#### Implications for stakeholders
- Home Buyers
    - Home buyers needs to prepare to pay higher price for houses in Northridge Heights or Stone Brooks Neiborhood, in exchange for a comfortable & convenient living environment. 
- Home sellers( including house owner, devleopers, housing agent)
    - Sellers can leverage on NH's good living environment to maximise sale price. Sellers can highlight high rental yield, low crime rate and convenience of the neighborhood. 
    - Developers can consider bidding for land at NH, higher sale price could translate to higher profit (assuming cost is constant)
    
**The 3rd Category is Age of House**

Based on lasso model, the following coefficients related to age of building are significant: 

- Year Built 
    - A one unit increase in year built i.e the house is younger, the sale price would increase by 294 dollar, holding other variables constant.
 
#### Implications for stakeholders
- Home Buyers
    - Buyers need to prepare to pay higher price for new houses. Perhaps, new houses has lesser defects, does not require repairs. Buyers also can renovate the house to his/her liking. 
- Home sellers( including house owner, devleopers, housing agent) 
    - It is good news for developers, the positive correlation between age of of building and sale price means that Ames is a city worth investing in for developers. The high sale price means there is demand for new buildings. 
    - Developers and agents could highlight the young age of the building in their marketing effort. It could also highlight the new amenities that come along with the new building.

* Reference: 
    - https://www.weichert.com/search/community/neighborhood.aspx?hood=60290 
    - https://en.wikipedia.org/wiki/Iowa_State_University
    
## Model Limitation & Future Work

**Model Limitations**
Our model only has the data for Ames city, Iowa, the importance predictors might not translate very well to other cities. Different cities the size of above ground floor & total basement area in square feet might not hold same measuring standards. 
Also the rating of the house quality & condition is subjective, how to standardize these measurements and rating system it could be a future work to improve the data consistancy. 

**Future Work** 
In the future, demographic data could be included so data scientist can examine who is willing to pay higher price, popular location, buyers are willing to pay for what kind of features. This woud provide an overall picture to data scientist and stakeholders.
Other than the age of the house, I am also interested on when the house been posted for sale. As a common understanding, the longer the sales advertisement been posted, the more agent fee or cost would be incurred. How to save the cost for stakeholders to get a house to be sold or purchase would be another key concern.
