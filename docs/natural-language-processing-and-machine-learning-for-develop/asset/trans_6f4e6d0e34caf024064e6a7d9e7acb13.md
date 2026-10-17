
import numpy as np
from sklearn.datasets import fetch_20newsgroups
from sklearn.feature_extraction.text import CountVectorizer
from sklearn.feature_extraction.text import TfidfTransformer
# from sklearn.neighbors import KNeighborsClassifier
# from sklearn.pipeline import Pipeline
# [https://scikit-learn.org/0.19/datasets/twenty_newsgroups.html](https://scikit-learn.org/0.19/datasets/twenty_newsgroups.html)
my_cats = ['rec.sport.hockey', 'comp.sys.mac.hardware']
# load training/testing data from sklearn:
train_data = fetch_20newsgroups(
    subset='train',
    categories=my_cats,
    shuffle=True,
    random_state=42
)
print("target_names:")
print(train_data.target_names)
print("------------------------\\n")
print("\\n".join(train_data.data[0].split("\\n")[:3]))
print("------------------------\\n")
print("First element of train_data target:")
print(train_data.target_names[train_data.target[0]])
# Initial training data points and their categories:
for t in train_data.target[:5]:
    print("target_name:", train_data.target_names[t])
    print("------------------------\\n")
    
###########################################
# 1) create a dictionary of features
# 2) transform documents to feature vectors
# 3) convert text documents to a matrix of #    token counts (CountVectorizer)
###########################################
count_vect = CountVectorizer()
X_train_counts = count_vect.fit_transform(train_data.data)

# count matrix => normalized tf-idf representation:
tfidf_transformer = TfidfTransformer()
X_train_tfidf = tfidf_transformer.fit_transform(X_train_counts)

**# an instance of the sklearn MultinomialNB class:** **from sklearn.naive_bayes import MultinomialNB** **nbayes = MultinomialNB()**

print("train_data.target:")
print(train_data.target)

# train_data.target has label data for each category in train data
clf = nbayes.fit(X_train_tfidf, train_data.target)

# predict the correct classes for these documents:
docs_new = [
    'My Macbook does not support Swift 5.',
    'I never played hockey',
    'Bobby Orr was the best NHL player'
]

# feature vector of our input:
X_new_counts = count_vect.transform(docs_new)

# invoke transform (feature vector is standardized):
X_new_tfidf = tfidf_transformer.transform(X_new_counts)

# predict the numeric categories for the documents:
predicted = clf.predict(X_new_tfidf)

#for doc, category in zip(docs_new, predicted):
#    print('%r: %s' % (doc, train_data.target_names[category]))

# Pipeline creates a single classifier:
text_clf = Pipeline([
    ('vect', CountVectorizer()),
    ('tfidf', TfidfTransformer()),
    ('clf', **nbayes**),
])

# Fit the train data to the pipeline
text_clf.fit(train_data.data, train_data.target)

# Test data
test_data = fetch_20newsgroups(
    subset='test',
    categories=my_cats,
    shuffle=True,
    random_state=42
)
docs_test = test_data.data
predicted = text_clf.predict(docs_test)

from sklearn.metrics import confusion_matrix
cm = confusion_matrix(test_data.target, predicted)
print("confusion matrix:")
print(cm)

true_neg, false_pos = cm[0]
false_neg, true_pos = cm[1]

all_values = true_pos + true_neg + false_pos + false_neg
accuracy = round((true_pos + true_neg) / all_values, 3)
precision = round((true_pos) / (true_pos + false_pos), 3)
recall = round((true_pos) / (true_pos + false_neg), 3)
f1 = round(2 * (precision * recall) / (precision + recall), 3)

print("--------------------------\\n")
print('Accuracy:  {}'.format(accuracy))
print('Precision: {}'.format(precision))
print('Recall:    {}'.format(recall))
print('F1 Score:  {}'.format(f1))

[Listing 10.11](#ch10.xhtml#list10.11) is also similar to [Listing 10.7](#ch10.xhtml#list10.7): the three main differences are shown in bold in the code. Launch the code in [Listing 10.11](#ch10.xhtml#list10.11) and you will see the following output:

confusion matrix: target_names: \['comp.sys.mac.hardware', 'rec.sport.hockey'\] \------------------------   From: nhmas@gauss.med.harvard.edu (Mark Shneyder 432-4219) Subject: Re: Playoff telecasts in Atlanta Organization: HMS \------------------------   First element of train_data target: rec.sport.hockey target_name: rec.sport.hockey target_name: comp.sys.mac.hardware target_name: rec.sport.hockey target_name: rec.sport.hockey target_name: rec.sport.hockey \------------------------   train_data.target: \[1 0 1 ... 1 1 0\] confusion matrix: \[\[378   7\]  \[  1 398\]\] \--------------------------   Accuracy:  0.99 Precision: 0.983 Recall:    0.997 F1 Score:  0.99 

The accuracy is 99%, which is the best accuracy of all the classification algorithms that we have seen: kNN, decision trees, random forests, and SVC.

This concludes the portion of the chapter that performs text classification with machine learning classifiers. The next section shows you how to perform text classification with the kMeans algorithm, which is an unsupervised clustering algorithm.

## **Text Classification with the kMeans Algorithm**

This section contains a brief description of the kMeans clustering algorithm, followed by a code sample that uses kMeans to perform text classification.

The intuition for the kMeans algorithm involves first selecting a set of points (called “centroids”), and second for each point in the dataset, determine its closest centroid. A more detailed description of the kMeans algorithm is shown here:

1.  Specify a value for k (typically an odd number).

2.  Initialize a set of randomly selected points as the centroids.

3.  Assign each datapoint to the closest centroid.

4.  Recompute the centroid for each cluster.

5.  Perform steps 3 and 4 again for each n-tuple.

6.  Repeat until the centroids no longer change.

Here are some details to keep in mind regarding the kMeans algorithm:

1.  The initial centroids can be any points (including points in the dataset).

2.  The number of centroids is a hyperparameter.

3.  This algorithm involves in-memory calculations.

4.  All datapoints must fit into memory.

The meanShift algorithm is another clustering algorithm that does not require you to specify the number of clusters, but it’s not scalable for very large datasets (which is also true of kMeans itself).

One technique for finding the optimal number of clusters involves the minimization of the within-cluster sum of squares (WSS). The value of WSS for a given cluster equals the sum of the distances between each datapoint in the cluster and the cluster centroid. In general, lower WSS values occur when observations are closer to their respective centroids, which in turn indicates a better fit.

In the extreme case in which each datapoint is its own cluster, the value of WSS is zero and hence it’s minimized. At the other extreme, if we have a single cluster, then the value of WSS is maximized. Hence, it’s necessary to find the right balance the value of WSS and the number of clusters.

The concept of “prediction strength” is way to evaluate clustering algorithms and to find the optimal number of clusters, which also involves WSS and the “elbow” technique, as discussed here:

*[https://towardsdatascience.com/prediction-strength-a-simple-yet-relatively-unknown-way-to-evaluate-clustering-2e5eaf56643](https://towardsdatascience.com/prediction-strength-a-simple-yet-relatively-unknown-way-to-evaluate-clustering-2e5eaf56643)*

Now that you have a rudimentary understanding of the kMeans clustering algorithm, let’s look at a code sample.

[Listing 10.12](#ch10.xhtml#list10.12) displays the contents of kmeans_nlp_classify.py that performs text classification with the kMeans clustering algorithm.

***LISTING 10.12: kmeans_nlp_classify.py***

