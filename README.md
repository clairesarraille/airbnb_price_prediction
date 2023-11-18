# Introduction:
- Welcome to my Airbnb price prediction study! This project's goal is to predict a realistic price for new Airbnb hosts to use to estimate the value of their first listing.

- Here's a guide to my GitHub Repo.
  - The first two notebooks cover data intake, data cleaning and data munging. The third notebook models price using Ridge and Lasso Regression.

# Business Case:
Currently, "The majority (of hosts) go with their own research, knowhow and gut," according to an Aibnb representative in Winter 2023. Experience and domain knowledge for type of property, location, and setting are of paramount importance for setting realistic prices.
The problem is that first-time hosts looking to set the price of their first-ever listing don't have reviews or experience from pior properties. To put it simply, first-time hosts lack the wisdome of experience to draw upon, and new listings lack data!

# Use Cases:
1. Sustainable Price-setting
- By a sustainable price, I mean one that is realistic and will attract customers given the listing's attributes.
- I ask this question: What price will consistently attract customers tiven the attributes of a new listing? Our answer comes from modeling existing listing data, which in essence "Crowd Sources" the collective wisdom of all Airbnb hosts.
2. New Listings - Do they have enough data?
- I ask a second question to guide this research: Do the variables that exist for new listings belonging to new hosts have enough "signal" for a predictive model? The attributes of a new listing lacks signal from review data that could be modeled as a time-series analysis based on changes in the listing. I want to get insight around this question: Does the limited aspect of new listing data hinder the ability of machine learning algorithms to accurately predict price?