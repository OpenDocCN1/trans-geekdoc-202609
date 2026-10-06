# # Unsupervised Machine Learning

![](bbox=[0.93, 0.16, 0.85, 0.38])

**Figure 15-3. Unsupervised machine learning flow.** The first step trains the model and outputs the labels, such as groups. The optional second step allows the model to label new data

# ## Semi-supervised Learning

Semi-supervised machine learning is a combination of supervised and unsupervised because we provide both labeled and unlabeled data. Sometimes labeled data is expensive or very hard to come by, especially in the large quantities often necessary in machine learning. If unsupervised learning simply won’t be enough for the problem being solved, there’s a way to augment the existing data to get more “labeled” data that can be used in a supervised learning model. This can work well, but doesn’t always. It’s definitely a “your mileage may vary” approach that depends on your domain and data.

There are some general limitations to using this approach. One key is that the unlabeled data needs to be similar to what's in the labeled data in terms of content. If we were trying to identify genres of songs and we had a set with labeled rock, pop, and reggae songs, adding in unlabeled