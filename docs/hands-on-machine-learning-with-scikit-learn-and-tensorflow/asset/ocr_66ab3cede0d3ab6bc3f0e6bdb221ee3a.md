ted copies (one per direction) and add them to the training set. Finally, train your best model on this expanded training set and measure its accuracy on the test set. You should observe that your model performs even better now! This technique of artificially growing the training set is called data augmentation or training set expansion.

+   3. Tackle the Titanic dataset. A great place to start is on Kaggle.

+   4. Build a spam classifier (a more challenging exercise):

+   - Download examples of spam and ham from Apache SpamAssassin's public datasets.

+   - Unzip the datasets and familiarize yourself with the data format.

+   - Split the datasets into a training set and a test set.

+   - Write a data preparation pipeline to convert each email into a feature vector. Your preparation pipeline should transform an email into a (sparse) vector indicating the presence or absence of each possible word. For example, if all emails only contain four words, "Hello," "how," "are," "you," then the email "Hello you Hello you" would be converted into a vector [1, 0, 0, 1] (meaning "Hello" is present, "how" is absent, "are" is absent, "you" is present), or [3, 0, 0, 2] if you prefer to count the number of occurrences of each word.

+   - You may add hyperparameters to your preparation pipeline to control whether or not to strip off email headers, convert to lowercase, remove punctuation, replace all URLs with "URL," replace all numbers with "NUMBER," or even perform stemming (i.e., trim off word endings; there are Python libraries available to do this).

+   - Then try several classifiers and see if you can build a great spam classifier, with high recall and high precision.

Solutions to these exercises are available in the online Jupyter notebooks at https://github.com/ageron/handson-ml2.