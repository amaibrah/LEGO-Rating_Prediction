# LEGO-Rating_Prediction

The dataset used in this project was found through Kaggle and includes data originally scraped from LEGO's website. The data focuses on online purchases made in different countries with the currency already being in USD. Every purchase has a rating associated with it. In this case, I focused on the overall rating of the Lego set purchased. The dataset originally had 14 different features, but this was cut down to 7.

*The ultimate goal of this project is to build a model that is able to predict LEGO set ratings based on other emtrics such as LEGO set size, minumum age per set, etc.*

## Data cleaning and preparation
#### Features and datatypes:  
* min_age, float 
* list_price, float
* num_reviews, float
* piece_count, float
* review_dfficulty, integer
* star_rating, float
* country_num, integer

#### Null values:
* There were multiple null values with review_difficulty having the highest number of them. Since this was a metric I wanted to focus on, I dropped the rows with the nulls.
* There were still nulls within the dataset, but they were within features I did not want to explore. Those columns were dropped.

#### Additional cleaning:
* convert age column from string to float. Age originally had a range of ages suitable for each Lego set. Took the lowest age within the range.

#### Additional data prep:
* Split star_rating column into 2 groups:
    * Ratings 5 and up are "good"
    * Ratings below 5 are "bad"
* Define predictor and target variable:
    * Predictor = min_age, list_price, num_reviews, piece_count, review_dfficulty, country_num
    * Target variable = star_rating

## Build Models
#### Build multiple models:
* GridSearchCV was used to look for best hyperparameters for specific models
* Apply best hyperparameters to Classification models and fit to training data
* Predict using test set

#### Check performance of model on test data:
* Check confusion matrix for classification models
* Compare model performance through precision and recall since data was imbalanced
* Determine best performing model based on metrics
