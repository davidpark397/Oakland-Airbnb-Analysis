# Oakland-Airbnb-Analysis
## Overview
This repository contains the versions of data, figures generated, and Python notebook that comprise an analysis of 3000+ Airbnb listings in the city of Oakland. In my experience, I've been very confused as to what determines the price of an Airbnb. When I needed to get an Airbnb in Chicago during an internship, for example, very similar listings (according to my specifications) in the neighborhood that I wanted to stay in displayed large variations in price. The analysis featured here represents an attempt at better understanding the drivers of the price of an airbnb listing as a product of its characteristics. We first clean the data, perform an extensive EDA, and then use regularized regression models to predict price and perform a basic feature importance analysis. 

## Data
The data used in this analysis consists of Airbnb listings characteristics for the city of Oakland, CA from http://insideairbnb.com/get-the-data.html compiled on July 8, 2019.

## How to Run
Create a virtual environment and install the packages listed in `requirements.txt` using:
```
pip install -r requirements.txt
```

## Final Takeaways:
From the Python notebook:
#### General Descriptive Stats
* There are 3211 Airbnb listings in the city of Oakland (in the dataset)
* The average price of these listings is \\$130.07
* There are 2288 unique hosts that have listings in the city of Oakland
#### Neighborhood Information
* The neighborhoods in Oakland that contain the most listings are Bushrod (138), Prescott (135), and Longfellow (119)
* The neighborhoods with more than 60 listings that have highest average price are Claremont (\\$388.78), Upper Rockridge (\\$225.00), and Trestle Glen (\\$192.06)
    * It's difficult to characterize the 3 "most expensive" neighbhorhoods as the number of listings per neighborhood is realtively small (around 58 on average), making mean neighborhood listing prices sensitive to the presence of outliers
#### Listing Characteristics
* Listings tend to be clustered around Bart stations
* Listing prices vary to a great extent across different property type and room type combinations (this makes intuitive sense)
    * For example, shared Rooms in apartments are \\$47.68 on average, whereas entire houses are \\$226.73 on average.
* The listings with the most reviews are within the \\$40 - \\$200 price range.
* The most common amenities offered by listings are (in order) wifi, "essentials" (which include toilet paper, soap, towels, pillows, and sheets), smoke detectors, and heating.
* A commonly used term in listings' descriptions is "San Francisco" suggesting that proximity to San Francisco is a draw to Oakland Airbnb listings.
#### Price Prediction
* The feature in the dataset that is the most correlated with listings price is the # of accommodates
* The most important features in determining listings price according to Lasso Regression are the # of accommodates, whether the listing offers an entire property or not, and the # of bedrooms and bathrooms
    * Whether or not the host is a superhost is also an important feature according to the Lasso model
* The most important features in determining listings price according to our XGBoost regressor are the # of amenities, the # of accommodates, and the # of the reviews
    * The host response rate and the review scores rating are also important features according to this model
