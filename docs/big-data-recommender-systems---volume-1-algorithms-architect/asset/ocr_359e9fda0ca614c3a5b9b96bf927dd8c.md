# Theoretical foundations for recommender systems 15

# Discussion

CF process works through the utility matrix as in Table 2.1. The focus is here to predict the ratings for the unrated items based on the available data in the matrix, and producing recommendations later on. The following process is followed [6]:

+   Each say 'T_ij' represents a rating given by user 'i' to item 'j' in the matrix. The rating is numeric, and it can also be 0, which means the item 'i' 'j' is not yet rated by the user 'i'.

+   The missing ratings are predicted by first computing the similarity between items and users. So the most similar 'N' users to the user 'i' are found and similarly most 'N' items to the item 'j' are found.

+   Using the similarities calculated in Step 2, the output is generated. The output consists of the prediction of the value 'T_ij' and a list of N recommended items for the user.

CF could be done through two major techniques:

+   Memory based

In memory-based techniques, the entire or a sample of data from the utility matrix is used. In this approach, unknown ratings are predicted and similarities among users and items are calculated using the rating information in the utility matrix, and a list of 'N' items to be recommended to a particular user is generated. The memory-based approach is classified into two types [6]:

+   User based: In the user-based approach, similarity between users is computed and the rating of user 'i' for an item 'j' is predicted based on what average rating has been given to this item by the similar 'N' users.

+   Item based: In item-based approach similarity between items is computed and the rating of user 'i' for an item 'j' is predicted based on what average rating the user 'i' has given to the 'N' similar items.

Similarity Measures: There are different similarity measures that could be used to compute the similarity between users and items. So commonly used are the [6]:

+   cosine similarity

+   correlation-based similarity

+   Pearson correlation

+   cosine vector similarity

+   adjust cosine similarity

+   Spearman correlation

+   Gaussian kernel.

+   Model based by constructing statistical models for predicting the ratings. Not all of the data and information is used in this approach. Some of the model-based approaches for estimating the probability of ratings are the following [6]:

+   cluster-based models

+   Bayesian networks