[<img src="/Users/claire/git/flatiron/capstone/airbnb_price_prediction/readme_images/Airbnb Price Prediction Project.jpg">]([https://link-to-your-URL/](https://github.com/clairesarraille/airbnb_price_prediction/blob/main/readme_images/Airbnb%20Price%20Prediction%20Project.jpg))




# Introduction:
- Welcome to my Airbnb price prediction study! This project's goal is to predict a realistic price for new Airbnb hosts to use to estimate the value of their first listing.

# Repo Guide:
- Here's a guide to my GitHub Repo so that you can explore and more importantly, *re-produce* my findings:
  - `notebook_01_data_cleaning.ipynb` covers data intake and file merging. `notebook_02_data_cleaning.ipynb` contains data cleaning and data munging work. `notebook_02_data_cleaning.ipynb` contains the data pre-processing, pipeline creating and model building code.
  - You'll also find development work in `Dev_Notebooks`
  - All raw data is contained in the zipped file `listing_raw_data.zip`
  - The cleaned dataset that is intended to be loaded into Google Colab from the file's raw link is `airbnb_data.csv`

# Repo Map:
```
├── CAPSTONE_PRESENTATION .pdf
├── Dev_Notebooks
├── LICENSE
├── README.md
├── airbnb_data.csv
├── listing_raw_data.zip
├── notebook_01_data_cleaning.ipynb
├── notebook_02_data_cleaning.ipynb
└── notebook_03_modeling.ipynb

```

# Business Case:
Currently, "The majority (of hosts) go with their own research, knowhow and gut," according to an Aibnbirbnb representative in Winter 2023. Experience and domain knowledge for type of property, location, and setting are of paramount importance for setting realistic prices.
The problem is that first-time hosts looking to set the price of their first-ever listing don't have reviews or experience from pior properties. To put it simply, first-time hosts lack the wisdome of experience to draw upon, and new listings lack the on-going feedback that review data provides. 

# Use Cases:
1. Sustainable Price-setting
- By a sustainable price, I mean one that is realistic and will attract customers given the listing's attributes.
- I ask this question: What price will consistently attract customers tiven the attributes of a new listing? Our answer comes from modeling existing listing data, which in essence "Crowd Sources" the collective wisdom of all Airbnb hosts.
2. New Listings - Do they have enough data?
- I ask a second question to guide this research: Do the variables that exist for new listings belonging to new hosts have enough "signal" for a predictive model? The attributes of a new listing lacks signal from review data that could be modeled as a time-series analysis based on changes in the listing. I want to get insight around this question: Does the limited aspect of new listing data hinder the ability of machine learning algorithms to accurately predict price?


# Data Understanding:
This study uses [listing data](http://insideairbnb.com/get-the-data/) scraped from Airbnb's website in September 2023, compiled by the organization [*Inside Airbnb*](http://insideairbnb.com/about/). "Inside Airbnb is a mission-driven project that provides data and advocacy about Airbnb's impact on residential communities." As a side note, they also produce fascinating studies such as [A Year Later: Airbnb as a Racial Gentrification Tool](http://insideairbnb.com/research/a-year-later-airbnb-as-a-racial-gentrification-tool).

## Extent of Data:
- Listings from 32 cities from 20 states in the U.S. There are over 270,000 listings. My final set of cleaned and pre-processed attributes include amenities, location, beds, bathrooms, property type, room type, and the polarity/subjectivity of the description of the host, property, and neighborhood. My final count of listings that I use for modeling after duplicates and outlier removal is 274,234.

# Sources:
- Alharbi, Zahyah. (2023). [A Sustainable Price Prediction Model for Airbnb Listings Using Machine Learning and Sentiment Analysis.](https://www.researchgate.net/publication/373625586_A_Sustainable_Price_Prediction_Model_for_Airbnb_Listings_Using_Machine_Learning_and_Sentiment_Analysis) Sustainability. 15. 13159. 10.3390/su151713159.
- Brownlee, Jason. (2016). Master Machine Learning Algorithms. Edition, v1.15.

# Modeling Process
Because my dataset had high multicollinearity that couldn't be completely eliminated, and because this is a regression problem as the target variable is continuous, I used Ridge and Lasso Regression rather than simple linear regression. Multicollinearity occurs when there is a strong correlation between two or more identified predictor variables in a multiple regression model. The existence of this phenomenon may seriously impair the analysis's overall quality and severely restrict the model evaluation's conclusions. I knew I wanted to begin this analysis by addressing the issue of multicollinearity, because one of the assumptions of linear modeling is that all predictors are independent of each other (meaning there is no multicollinearity). Ridge and Lasso regression models were used because they make use of regularization strategies to mitigate multicollinearity's negative impact on the model's quality and validity of conclusions. The generalization of models with incredibly complex relationships is supported by regularization strategies such as Ridge and Lasso Regression. One feature of a highly complex model may be multicollinearity. Overfitting is avoided by regularizing the model predictors with a penalty.

# Results:
### Discussion:
- I was able to reduce the distance between my predicted results and the real price (RMSE) with each successive model. I was also able to increase how much variability in my target value is explained by my data (R2). However, my results are still sub-par. My final R-Squared value of .38 means that 62% of the variation in price is explained by data that is NOT in my dataset. Only 32% of the variability in price is explained by my available data.
- I won't discount the success of seeing that Ridge Regression performed a bit better than Lasso Regression - R2 was improved by about 3%, and error was reduced by about 1%. My final model, tuned via GridSearchCV, improved from Lasso Regression by 8% for R2 value and there was a 4% reduction in the RMSE value.

## Results from each Model Iteration:
- Lasso Regression:
  - RMSE: 268
  - R-Squared: 0.35
- Ridge Regression:
  - RMSE: 265
  - R-Squared: 0.36
- Final Model, Ridge Regression with hyperparameters tuned:
  - Optimized Hyperparameters via GridSearchCV:
    - alpha=10
    - solver=svd
  - RMSE: 258
  - R-Squared: 0.38


# Conclusion:
1. My model’s performance was drastically lower compared to studies I consulted.
   - The study's superior model performance indicates that there is something wrong with my feature selection (missing review data) -- which would have to change my business problem.
2. There weren’t great gains in model performance were achieved: Lasso->Ridge->Tuned Ridge


# Recommendations and Next Steps:
1. Tweak Approach to Problem:
   - Which features are most important for highest priced listings?
   - Subset by attributes listers can’t change like location and property type.
   - Different models for each city or region.
2. More Data:
   - Review Data
   - Additional Amenities
3. Use Spatial Auto-correlation for lat/long values