# Project 2: Using Linear Regression Modelling to Predict House Prices in Ames, Iowa

Problem Statement: 
I am planning to move to Ames, Iowa to work at the US Department of Agricultural facility. In preparation for my move, I would like to examine the features of the house itself (both qualitative and quantitative) as well as location that drive the price of housing in the city. In order to predict the sale price of a house, I built several linear regression models that predicted the price of a house based on the features I provided.

Finally, I submitted my models to a Kaggle competition to see how they scored against other Linear Regression Models.

## Table of Contents

1. Repository Components
2. Data Dictionary
3. How to Read the Notebooks
4. Conclusions

### Repository components: 

1)A folder containing the notebooks for EDA & Data Cleaning, Feature Selection, and Modelling/Kaggle Submissions

2) Data sets including the housing set from Kaggle to train models on, the test data set, and separately cleaned and saved csvs of the same

3) A .pdf containing a PowerPoint generated slideshow presentation of insights gathered from the data, geared towards explaing my thought process behind the modelling.vIt is 7 slides to be delivered in junction with an oral presentation with a 5-6 minute timeframe. 

4) This READMEProject1.md file and 5) the original README.md file, renamed to instructions.md, containing detailed instructions for the full scope of this project, with resources and rubric attached.

### Data Dictionary

A complete data dictionary was provided by Kaggle and can be found here: https://www.kaggle.com/c/house-prices-advanced-regression-techniques/data

### How to Read the Notebooks

The code folder of this repository contains three (3) notebooks, each covering a different step of the modeling process: Exploratory Data Anlysis & Data Cleaning, Feature Engineering and Selection, and finally the Linear Regression models.

1. EDA & Data Cleaning

After reading in an examining the data, I began by splitting the features into numerical features and categorical features. Numerical features including things such as house/plot size, number of bedrooms, and number of bathroom. The categorical features included qualitative ratings for the quality and condition of the house as well as whether or not the house had things such as central A/C, how the house was zoned, and what neighborhood it was in. I also plotted histograms and scatter plots of the numeric features and well as quality-related categorical features as related to sales price to start getting an idea of what features would be important to include in the model later on.

The first step I took cleaning the data was removing the outliers of homes that had more than 4,000 square feet of above ground living area. Next, I renamed all of the columns to lower case letters for formatting reasons.

Most importantly, I checked all of the columns for missing NaN values. For relevant categorical columns I replaced NaN with "none" and numerical columns had NaN replaced with "0."

Since I am interested in house price depending on where it is located - I made dummy columns for all of the "neighborhood" information so that it could be included in my models.

Lastly, I noticed one of the columns I wanted to use had a numeral in the column name so I changed it to prevent errors before exporting both the train and test data as separate "clean" csvs.

2. Feature Engineering

Looking at the heatmap of correlations between the various features and sale price that I created as part of the EDA process. I selected a combination of features that had strong correlations with sales price. I decided the best approach would be to look at a combination of numerical (square footage & dummy neighborhood) and categorical (features related to the house condition and quality) that I thought would be important predictors of the final price.

3. Modelling

Since we were provided with the test set, I wanted to be careful not to overfit my model to get a good R^2 score on the testing data only to drop off on the final score.

My best model which took the log of the sale price and used the features: overall quality, overall condition, above ground living area, year built, and first floor square footage in addition to the dummy columns I created for the neighborhoods. I also tested both Ridge and Lasso model predictions, but since they had slightly lower R^2 scores I decided not to use them.

## Conclusions

As discussed previously, I did not want to overfit my model to the training data. While I probably could have made it more accurate by including more features, this would have resulted in an over rather than under fit. Given shifting trends in architecture and style which dictate a home's features a model fit too tightly to this "snapshot" of homes might quickly it may become outdated.

I was also disappointed that the data did not include any information about how close to cultural features like ISU and the USDA facility a home is. Proximity to important cultural landmarks is a driving force in demand for housing, so I imagine that there would also be a strong linear relationship with how close a home is to a cultural center and the price. The data also did not include zip code (a better location metrics than arbitrarily designated neighborhoods) or demographic information which are also important factors to consider when planning my move.

While I look forward to moving to Ames, more data needs to be collected in order to form a better picture of the city housing market and predict the prices of future homes.
