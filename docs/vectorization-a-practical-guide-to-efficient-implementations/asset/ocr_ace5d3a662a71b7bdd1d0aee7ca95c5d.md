feature can take. We use x_size=0 to indicate the feature is a continuous feature.

+   - k_latent: This is the latent dimension size of the embeddings. For the FM model, the latent dimensions should be always identical among the features.

+   - n_label: This tells the method if the feature is a list or a single-value feature. We assume that a categorical feature can be either a single-value feature or a list feature, but all continuous features are single-value features.

+   - name: This provides a name for the embedding. Used for Keras model summary to keep track of the flow of the data.

+   - keepdims: If True, then the method returns (batch_size, 1, emb_size) embeddings. This can be useful for later concatenation operations when building the model.

+   • fm_1d (Lines 125–140): This is the method that implements the linear part of Equation 6.1. It iterates through the features and creates the linear or the bias terms of the features, using the embedding of size 1. Then, the bias terms are all summed together.

+   • fm_2d (Lines 142–176): This is the method that implements the second-order part of Equation 6.1. It first iterates through the features to create embeddings with the size of K and uses the reformulated optimization criterion to compute the sum of pair-wise second-order interactions between the features.

+   • deep_mlp (Lines 178–197): This method implements the dense feedforward layer given the feature embeddings obtained from fm_2d as inputs. The model first concatenates the embeddings of the features and uses it to predict a single score that will later be combined together with the scores from fm_1d and fm_2d.

+   • build_model (Lines 199–231): This method creates the model. It first creates the Input layers for each of the features (Lines 201–207). It then proceeds to call the three terms (fm_1d, fm_2d, deep_mlp) to compute predicted scores for the current batch of examples (Lines 209–210). The scores are combined into an array via Concatenate, and the array is sent to another feedforward layer to obtain the final score (Lines 212–223). Finally, the method builds the Keras.Model object and returns it (Lines 226–231).

# 6.5.4 Training DeepFM on MovieLens 1M Dataset

In this section, we train the DeepFM model using the MovieLens [Harper and Konstan, 2016] 1M dataset, which can be downloaded from https://grouplens.org/datasets/movielens/1m.

Let's first prepare the data for our model