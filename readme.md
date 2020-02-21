# MovieLens Recommender System

Svenborgia has gone under dictator rulership and are now cut off from all international website content except for python packages. We are a group of three savvy data scientists that have managed to whip up a solution for movie recommendations in four days. 

Our overall goal is to provide users with the best recommendations possible. Our system utilizes both collaborative and content filtering based recommendations. To power this recommender we utilized the smaller MovieLens dataset (from www.grouplens.org). The important columns available in this dataset are userId, movieId, genre, title, tags (explains attributes of the movie), and reviews. Each user has a unique userId which is attached to all the movies they watched and the reviews and tags they gave it. 

The collaborative based filtering compares similarities between users. It utilizes Apache Sparks ALS model as recommender system. To recommend a movie to a given user, this system uses the reviews a user has and based on that and what other users have recommended the same movies and other movies, it creates a prediction rating for all other movies, then the most relevant movies based on content and ratings is provided.

Our content based filtering uses Surprise’s (a Python module) SVD (Single Value Decomposition) and TFIDF word vectorizer. The system groups movies based on similar keywords using both genre and tags. It then recommends movies that are closest and most similar to a given movie.

How our recommender works.

It takes in a User ID. If the user is new, it will output the top rated and most popular movies
If the user is a current user, it will output a Top 5 recommendation based on their viewing and rating history
It also can prompt the user to add ratings to movies, and will respond with movies based upon the rating (using collaborative filter)
The user can also explore movies similar to a specific movie (using content filter)

Our current implementation of the collaborative filtering system had a root mean square error (RMSE) rate of just under 1.0. Meaning that on average, for any rating predicted for any user, the prediction is on average off by ~1.0. Meaning that the system might rate a movie a 5, when the user actually thought it was a 4. This definitely leaves some room for improvement. While not fully utilized in our finished model, when we used the full MovieLens dataset this error rate was reduced to 0.87. We also explored using the Surprise package for our collaborative filtering, and obtained an RMSE of ~0.85 on the small MovieLens dataset. We were also able to implement a Mean Average Precision @ K (MAP@K) evaluation on the Surprise model, and, surprisingly, received an average precision of 86%. Meaning that, on average, the actual recommendations provided to a user were considered relevant 86% of the time. Even still, it regularly recommended the same movie as the #1 pick for users (Shawshank Redemption). We were not able to implement this with our ALS system.

To improve our recommender in the future we would like to have a better UI and better evaluation metrics. For the UI, we would like to include images. These can be obtained through web scraping from IMBD’s website. Also from IMBD, we would like to use a larger dataset. Also we would like to implement some sort of filter by year. If a user chooses a new movie, only recent movies will show up while if they choose an old movie, other classics will appear. To utilize better evaluation metrics, we want to change the way our content based filter works. One option is to try KNN, so that we would get a score based on each recommendation which we could use to evaluate. Another hurdle we encountered in using evaluation metrics is our lack of data needed for the metrics, so doing some sort of data collection would be useful.

File Paths
/data: Data library
 - Will need to download dataset from https://grouplens.org/datasets/movielens/latest/
/notebooks/report: Final Jupyter Notebook
/notebooks/exploratory: Exploratory Notebook

