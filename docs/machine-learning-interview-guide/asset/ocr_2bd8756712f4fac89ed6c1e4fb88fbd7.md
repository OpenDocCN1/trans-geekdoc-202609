probable value is said to have the document belonging to it. Still, Naïve Bayes is helpful for text classification in general, and in particular useful for NLP tasks.

# Question 2: How does Naïve Bayes handle text classification tasks in NLP?

In text classification, Naïve Bayes applies in the NLP by analyzing the likelihood of features/words appearing in the documents in order to determine the class/category of the document. It generally models the likelihood of a document in each class from the occurrence of the words in documents.

# An overview of how it works:

+   - Feature extraction: Naïve Bayes transforms text data into vectors based on the specific words, disregarding the sentences’ grammar and word positions.
+   - Training: It learns the probability of occurrence of each word that is in documents of category, and estimates the prior probability of each of the categories from the training corpus.
+   - Prediction: Naïve Bayes uses Bayes theorem to calculate likelihood of a document belonging to that class and the features of that class and the likelihood of it not belonging to that class; then, the approach selects the class with the highest likelihood.
+   - Classification: As it identifies the document to a certain class with maximum probability, the technique is very effective in simple text classification problems in NLP.

It can be seen that, even when making certain assumptions, the Naïve Bayes classifier can be effective in text classification problems, especially when there is a large