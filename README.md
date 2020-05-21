# Recommendation-Engine
Describes both User-based and Item-based recommendation systems

1) Introduction:

A recommender system is a system based of machine learning algorithms that provide the most relevant information to users by discovering patterns in their dataset. The algorithm rates the items and shows the user the items that they would rate highly. For example, Amazon and Netflix for instance, use the same for recommending movies to their users.

TYPES OF RECOMMENDATION SYSTEMS:
  
  i. Collaborative filtering: Collaborative Filtering is a technique used to filter out items that a user might like on the basis of     reactions by similar users. In other words, the behavior of a group of users is used to make recommendations to other users. It          works by searching a large group of people and finding a smaller set of users with tastes similar to a particular user. It looks at      the items they like and combines them to create a ranked list of suggestions.Furthermore, there are two types of collaborative techniques:
     
- Memory-based method:Memory-based techniques use user rating data to compute the similarity between users or items. They are      simple to implement and the resulting recommendations are often easy to explain.They are divided into two:
        
a) User-based collaborative filtering:In this model, products are recommended to a user based on the fact that the products have been liked by users similar to that user.
        
b) Item-based collaborative filtering:These systems identify similar items based on users’ previous ratings. It does the same by taking note of how many users that bought item X, also bought item Y. If the correlation is high enough, they can be assumed         to be similar to one another. Item Y will from there on be recommended to users who bought item X and vice versa.
    
- Model-based methods: Model-based methods are based on matrix factorization and are better at dealing with sparsity. They are       developed using data mining, machine learning algorithms to predict users’ rating of unrated items. In this approach techniques          such as dimensionality reduction are used to improve the accuracy. Examples of such model-based methods include decision trees,         rule-based models, Bayesian methods and latent factor models.   
  
  ii. Content based filtering:Content based systems use meta data such as genre, producer, actor, musician to recommend items say movies       or music. They are based on the idea that if you liked a certain item you are most likely to like something that is similar to it.
  
2) Dataset used: Used movielens dataset for this project. https://grouplens.org/datasets/movielens/latest/

3) Approach

I. ITEM-BASED COLLABORATIVE FILTERING:The final algorithm we have implemented is a hybrid of collaborative filtering and content-based prediction. We create a pivot table created from ratings, movieId and userId. We also create a metadata for each movie consisting of the genre and the tags associated with each movie. Now we use the help of Natural Language Processing and cosine similarity to generate similarity score of movies from this metadata. We also generate a similarity score from the aforementioned pivot table with the help of cosine similarity. We sort the movies according to hybrid score calculated as the weighted average of the two individual scores calculated and return the top recommendations. Pre-processing of the data before feeding to the algorithm is very important. We have dropped fields like time-stamp which can be used to have very high accuracy of prediction but would increase the complexity of the model and would lead to high processing cost.

II. USER-BASED COLLABORATIVE FILTERING: The user-based collaborative filtering is generally based on “K - Nearest Neighbor” algorithm for recommendations, which looks at the users’ rating patterns and finds the nearest neighbors, i.e. users with ratings similar to yours. The algorithm then proceeds to give you recommendations based on the ratings of these neighbors. In a fixed size neighborhood, the algorithm finds the most similar users and use them for a basis of recommendation. However, in a threshold based neighborhood, all users that fall within the threshold, i.e. are similar enough are used to provide recommendations. The neighborhood-based algorithm calculates the similarity between two users or items, and produces a prediction for the user by taking the weighted average of all the ratings. Similarity computation between items or users can be done using Cosine-based similarity criterion. Now we make a list of all movies seen by the similar users and remove the movies already watched by the user for whom we’re making predictions. Now we score the movie according to the user’s likings.This predicted score is equal to the sum of the ratings that each user gave to that item subtracting the average rating of that user multiplied with some weight which is of how much this user is similar or supposed to contribute to the predictions of other user. This is weight between user u and v. The score ranges between 0 to 1 where 0 is low and 1 is high. Now sort these in descending order and return the top 10 movies.
