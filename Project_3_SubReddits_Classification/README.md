# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png)

# Project 3 - SubReddits Classification

### Problem Statement

In a most recent survey, Walmart was ranked **LAST** for supermarkets in the 2021 American Customer Satisfaction Index Retail and Consumer Shipping Report, We as a Data Science Team in Walmart are been appointed by Top Management on tasks to understand what users(Customers & Walmart employees) think of Walmart and our competitors, to understand where positive feedback will continue to be reinforced and adopted while negative feedback can be addressed and prevented, with the leverage of Data Science approach, We will suggest on what actions We could take and eventually improve the social media image of Walmart as well as improve Customer Satisfaction.

As Social media presence is vital in our day and age, Reddit is an American social news aggregation, web content rating, and discussion website featuring user-posted stories. As of February 2021, Reddit was ranked the 18th most visited website in the world and 7th most visited website in the U.S.

As a start, we will be looking into the posts on Walmart's subreddit page, alongside a chosen competitor, **Costco** (who was ranked at top 2 in above suvey mentioned)

**Primary Objective**: 
To enhance our understanding of Walmart's social media image on reddit so as to introduce strategy for improvement.

**Secondary Objective**: 
To identify what subreddit users think of both supermarkets, where positive feedback will continue to be reinforced and adopted while negative feedback can be addressed and prevented.

The __Primary stakeholder is:__ Walmart Corporate, and the __Secondary Stakeholder is:__ Walmart Consumers.

### Executive Summary:

The success of this project will be evaluated based on a classification model having a higher prediction accuracy and AUC Score than the baseline score of 50%.

The classification model through Natural language processing will aid us in "understanding" the contents of the subreddits.
Posts from Walmart and Costco subreddits are scraped, analyzed, cleaned, processed and ran through several classification models (e.g. Logistic Regression, KNearestNeighbor, Multinomial Naive Bayes, Random Tree Classifier).
The final production model that we chose was __Logistic Regression with TfidfVectorizer__, at a classification prediction rate of __93.3%__.
We choose TfidfVectorizer as it penalize common words and give rare words more influence, this is relevant to our problem statement, Walmart posts and Costco posts tends to use different terms and Logistic Regression on interpretation of coefficients allows us to make useful recommendations for our problem statement.

More Negative sendiments on Walmart's subreddit posts are double compared to Costco.
- For the sentiments of subreddit post of walmart, 19% are neutral, 34% negative & 47% positive.
- For the sentiments of subreddit post of costco, 22% are neutral, 23% negative & 54% positive.

We would conclude that Walmart's social media image on reddit is not ideal given the numerous posts by Walmart's employees complaining about their workplace environment and conditions. Also supported by the sentiment analysis in which we seek to classify text as having positive or negative emotion.

Costco's social media image on the other hand fared well. Costco seems to be able to offer products and services that customers are interested in and had gone on reddit to discuss and give praises about it.

### Recommendations:

* To the __Primary stakeholder: Walmart Corporate-Empoyees__ (Because happy employees make happy customers, leading to positive improvements to Walmart’s brand image)

    - Provide more benefits programmes：
        - Have better employee benefits to attract and retain employees
    - Suggest for Management Uplift：
        - Consider improving overall management strategy to develop a better company culture
    - Improve HR Policies：
        - Uplift Annual leave and PTO policies
        - Capitalise on Whistle Blowing policy to protect employees, for example, Human Resource Team can reinforce the fact that associates are able to report a concern online without their identities being exposed, especially if they have Team Leads and/or Store Managers who are not carrying out the necessary duties
        - To start being pro-active in addressing and taking in feedback of their employees
    - Improve SOP: 
        - Clear guidelines and protocols on how everything should be carried out in Walmart should be communicated clearly by employers to employees

* To the __Secondary Stakeholder: Walmart Consumers__(Because happy customers keep us going everyday)

    - Promotions：
        - To have better cash rebate scheme and offer better deals, more sales to attract customers
    - House Brands：
        - To develop a House Brand similar to Costco's Kirkland Signature to increase brand loyalty
    - Improve HR Policies：
        - Uplift Annual leave and PTO policies. Capitalise on Whistle Blowing policy to protect employees, for example, Human Resource Team can reinforce the fact that associates are able to report a concern online without their identities being exposed, especially if they have Team Leads and/or Store Managers who are not carrying out the necessary duties
    - Inhouse Foodcout/Food Stations: 
        - Setup a "happy" shopping with "eating" enviroment, potentially develop "hot food" stations or food courts that consumers can enjoy the full experience of shopping in Walmart

### Data Dictionary:
|Feature|Type|Dataset|Description|
|---|---|---|---|
|id           |str      |r/walmart/r/costco|id of each subreddit post
|created_utc  |datetime |r/walmart/r/costco|date and time subreddit post was created
|subreddit    |str      |r/walmart/r/costco|name of subreddit that the subreddit post belongs to
|text         |str      |r/walmart/r/costco|combined title & body text of each subreddit post
|selftext     |str      |r/walmart/r/costco|body text of each subreddit post
|title        |str      |r/walmart/r/costco|title of each subreddit post
|num_comments |int      |r/walmart/r/costco|number of comments of a subreddit post
|score        |int      |r/walmart/r/costco|number of upvotes of a subreddit post
|upvote_ratio |float    |r/walmart/r/costco|ratio of upvotes of a subreddit post
    
## Future Work

- In the future, a larger dataset could be gathered. Currently, only around 1490 unique posts were gathered for Costco and 1497 posts for Walmart. A larger dataset would be better for us to make inference of the population. 
- More models could be applied, for example models such as artificial neural network could be explored in the future. The advanced models which might provide better predicitions. 
- We are now is comparing Costco Posts, We could compare more subreddit posts of supermarkets in USA to Walmart (Eg. Trader Joe's, Aldi etc.) 
- Our model is limited to just look into the title & selftext of each subreddit post, we can also look into the comments and upvotes in each post.
