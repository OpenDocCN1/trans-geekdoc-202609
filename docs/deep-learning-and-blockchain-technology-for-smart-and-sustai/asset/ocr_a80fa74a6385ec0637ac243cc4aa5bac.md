+   1. Synonym of each word in an email body is found.
+   2. If the synonym set is empty for a word, then it is removed.
+   3. If a word has a synonym, then compare it with the synonym of other words.
+   4. If multiple words have similar meaning, then merge into a single word in the body.
+   5. Reduced feature set is obtained as an output.

# ## 2.3.4 Applying BOW Model

Machine learning algorithms can operate only on numerical values. Hence, the reduced textual features are then converted into numeric values using the Bag of Words model. This model counts the number of occurrences of words in the email. To reduce features again, the words with the highest count have been considered for further processing. Words with a minimum count are discarded since they have no impact on classification process. In this proposed model, 0.25 has been considered as minimum threshold value for the count of the words. Words with count greater than 0.25 have been taken for classification process. Words with frequency less than or equal to 0.25 are discarded. After obtaining the sparse matrix for the email body dataset, it is combined with spam_term_weight from the subject field. The classification models have been built for the training and test datasets using all classifiers.

# ## 2.3.5 Email Classification Using ML Algorithms

The Classification module is the most crucial one for our work. To classify the emails as spam or ham, four classifiers have been implemented: SVM [21,22], Multinomial Naive Bayes, Gaussian Naive Bayes, and Bernoulli Naive Bayes. Eighty percent of this dataset is for training, while 20% is for testing.

For the training dataset, classification models utilising Bernoulli Naive Bayes, Multinomial Naive Bayes, SVM, and Gaussian Naive Bayes have been developed. Initially, a model for the training dataset is constructed using an SVM classifier. This classifier effectively manages large dataset volumes. For linear regression and classification, the supervised machine