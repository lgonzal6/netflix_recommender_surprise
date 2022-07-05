# Netflix Recommnder Systerm with Surprise

## The purpose of this project

In this short project, we explore a shortened version of the data provided on Kaggle Netflix recommender competition. We will build a simple recommnder system using the Surprise library, and test its results. 

## About the Data

The data can be downloaded from Kaggle [here](https://www.kaggle.com/datasets/rishitjavia/netflix-movie-rating-dataset)

Movie file contains the following columns: Movie_ID, User_ID, Rating <br />
Rating: 1-5

## Process 

In this project we explored Netflix's dataset that was use for its Kaggle recommender system competition. The dataset that I began working with was just a small portion of the actual dataset. But even then, I had to greatly reduce the dimentionality of my dataset, first by taking a sample (30%). I then further reduced the dimentionality by filtering out users that had rated less than 5% of movies and movies that had been rated by less than 5% of users. 

While such filtering may have been unfair, in real practice, companies do have to make choices for new customers (cold start problem). In this scenario, I am assuming that those customers that we filtered out will have to get recommendations based on another algorithm and through information obtained from a questionaire.

We tested the reduced dataset on three different models: SVD, BaselineOnly, and KNNWithMeans. We obtained the best rmse scores from the SVD model which relies on Probabilistic Matrix Factorization. So we decided to move on with that model. 

We then try to find the best hyper-parameters for SVD using gridsearch, thereby reducing rmse from 0.91 to 0.88. 

After tuning our SVD model, we explored the errors, and we saw that on average, ratings were missed by 0.70 ratings points. We futher explored the distribution of errors and saw that a vast majority of ratings were mispredicted by 1 rating point or less. 

## Conclusions

This simple SVD model provided very good predictions, the model does not need to be precise to generally make very good recommendations. If the model predicts a rating or 4 or more, if is very likely the user will enjoy the movie. If the model predicts a rating of 3 or less, it is quite likely the user will not enjoy this movie.  I do recognize that we filtered certain users and movies that would have led to a much greater distribution of errors, but in industry, there will always be that issue and in those cases, user can be recommended generally popular titles and/or be given a survey to help kick-start predictions.