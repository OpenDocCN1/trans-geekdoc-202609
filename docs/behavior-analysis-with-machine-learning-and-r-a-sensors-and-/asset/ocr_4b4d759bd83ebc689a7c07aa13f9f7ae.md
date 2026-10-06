# CHAPTER 7. ENCODING BEHAVIORAL DATA

id as the label. The id of each centroid can be an integer number. Intuitively, similar feature vectors will end up in the same group. For example, there could be a group of objects that look like chairs another for objects that look like cars and so on. Usually, it may happen elements in the same groups will not look similar for the human eye, but they are similar in the feature space. the objects' shape the groups may not make sense at all for the human eye. If the objective is to classify the complex scene, then we do not necessarily need to understand the individual objects nor they need to have a corresponding mapping into a real-world object.

Once the feature vectors are labeled, we can now build the word-count table but instead of 'meaningful' words, the entries be ids with their corresponding clusters. As you might have guessed, limitation is that we do not know how many clusters (labels) there should be for a given problem. One approach is to try for different values of k and use the one that optimizes your performance metric of interest.

But, what this BoW thing has to do with behavior? Well, we can use this method to decompose complex behaviors into simpler ones and encode them as BoW as we will see in the next section for complex activities analysis.

# Advantages

+   - Able to represent complex things by decomposing them into simpler parts.
- The resulting BoW can be very efficient and effective for classification tasks.
- Can be used in several domains including text, computer vision, sensor data, etc.
- The BoW can be constructed in an unsupervised manner.

# Limitations

+   - Temporal and spatial information is not preserved.
- It may require some effort to define how to generate the words.
- There are cases where one needs to find the optimal number of words.

# 7.6.1 BoW for Complex Activities.

```
bagwords/bow_functions.R bagwords/bow_run.R
```