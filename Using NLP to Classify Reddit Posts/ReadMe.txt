# Project 3: Using Modelling to Classify Reddit Submissions between /r/Conspiracy & /r/History

Problem Statement: 
My grandfather loves history and loves to read about it. He recently started using the internet more and I noticed that he's been saying some pretty out there things! I had a look at his computer at it seems like he's been getting things he reads on /r/conspiracy mixed up with things that he's read on /r/history. To help him tell the difference, I built several classification models to help him understand what topics tend to show up in which subreddits.

## Table of Contents

1. Repository Components
2. Data Dictionary
2. How to Read the Notebooks
3. Conclusions

### Repository components: 

1)A folder containing the notebooks for Data Acquistion, EDA & Data Cleaning, and Modelling

2) Data sets including the raw Reddit scrapes broken out by scrape and subreddit

3) A .pdf containing a PowerPoint generated slideshow presentation of insights gathered from the data, geared towards explaing my thought process behind the modelling. It is 7 slides to be delivered in junction with an oral presentation with a 5-6 minute timeframe. 

4) This README as well as the original README which has been moved to the Resources folder

### Data Dictionary

All data used is submissions scraped from Reddit using the PushShift API. 


### How to Read the Notebooks

The code folder of this repository contains three (3) notebooks, each covering a different step of the modeling process: Exploratory Data Anlysis & Data Cleaning, Feature Engineering and Selection, and finally the Linear Regression models.

1. Data Acquisition

The Reddit submissions were acquired using the Pushshift API in order to scrape submissions from both subreddits from the month of January. They were then exported as csvs for cleaning and modelling.

2. EDA & Data Cleaning

After importing and combining my data into two datasets, one history, one conspiracy, I dropped all posts by the AutoModerator, deleted/removed posts, and replaced all non-alphanumeric characters with white space.

3. Modelling

I combined the two data sets and adding a column for "is history" so that we can classify posts as 0= is history, 1 = is not history.

My best model used a CountVectorizer and then a Logistic Regression to achieve a perfect accuracy score on the training data 95% on the testing data. However I also experimented with Naive Bayes, Bagging, Random Forest, Bagging Random Forest, and SVC, all using TDIDF to vectorize the posts.

## Conclusions

| Model Type                          | Train Score | Test Score | ROC AUC Score |
|-------------------------------------|-------------|------------|---------------|
| CountVectorizer Naive Bayes         | .9821       | .93224     | .9325         |
| CountVectorizer Logistic Regression | 1.0         | .9525      | .952          |
| TFIDF Logistic Regression           | .9940       | .9339      | .9337         |
| TFIDF Bagging                       | .9918       | .92284     | .9337         |
| TFIDF  Random Forest                | .9599       | .8857      | .8821         |
| TFIDF Bagging Random Forest         | .9873       | .9332      | .931          |
| TFIDF SVM                           | .9146       | .8264      | .8188         |

From the above table we can see that the CountVectorized Logistic Regression scored the best across the training and test data, followed closely by the TFIDF Bagging and Bagging Random Forest models. It makes sense that these 2 were 2nd and 3rd best since they are designed to make sure that one feature does not have undue influence on th predictions, which is think is helpful in this case because so many of the /r/conspiracy posts have to do with the CoronaVirus outbreak which tips the model.