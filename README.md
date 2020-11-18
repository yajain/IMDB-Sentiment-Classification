# IMDB-Sentiment-Classification
This takes in a review of a movie ad input and predicts if the review is positive or negative.
Uses XGBoost on SageMaker 1.72.0 for the classification and the data is stored on S3 buckets.
The dataset can be found here - [IMDB Datset](http://ai.stanford.edu/~amaas/data/sentiment/).

# Dataset and Preprocessing
Dataset is basically a 50,000 reviews from imdb. Training set of 15,000, validation set of 10,000 and testing set of 25,000.
Uses NLTK and Beautiful Soup to preprocess data - removing HTML tags, converting to lower case, removing stopwords and stemming each words using Porter Stemmer.
Stores the data in three csv files - train.csv, test.csv, validation.csv after preprocessing.
Stores data from the three files into the default S3 bucket using upload_data

# Algorithm
Creates a Docker container from AWS which has XGBoost.

Hyperparameters of XGBoost - 
max_depth=5
eta=0.2, gamma=4
min_child_weight=6
subsample=0.8
silent=0
objective='binary:logistic'
early_stopping_rounds=10
num_round=500

Instance type for training - ml.m4.xlarge

Testing Accuracy - 86%

# Dependancies
SageMaker 1.72.0, Python3.x, AWS, SciKit Learn, NumPy, NLTK, Beautiful Soup
