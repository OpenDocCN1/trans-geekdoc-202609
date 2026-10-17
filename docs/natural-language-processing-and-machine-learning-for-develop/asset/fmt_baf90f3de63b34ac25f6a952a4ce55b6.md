
\=> sentence: I love Chicago deep dish pizza. \=> polarity: { 'neg': 0.0, 'neu': 0.488, 'pos': 0.512, 'compound': 0.6369}   \=> dataframe:      neg    neu  ...  compound            sentence 0  0.000  0.716  ...    0.2466                     Our plan was not without merit 1  0.000  0.615  ...    0.6124  I like the pizza toppings but I do not like th... 2  0.205  0.795  ...   -0.4767  The only thing worse than being talked about, ... 3  0.000  0.775  ...    0.4404  Everything is funny, as long as it's happening... 4  0.163  0.392  ...    0.6486    When ignorance is bliss, 'tis folly to be wise. 5  0.190  0.652  ...   -0.1531  Good judgement is the result of experience and...   \[6 rows x 5 columns\]   \=> dataframe:      neg  ...  positive\_sentiment 0  0.000  ...               False 1  0.000  ...                True 2  0.205  ...               False 3  0.000  ...               False 4  0.163  ...                True 5  0.190  ...               False   \[6 rows x 6 columns\] 

## `Sentiment Analysis with Flair`

`Flair` is an open source Python‑based library that performs various NLP‑tasks, such as NER and POS tagging, and its home page is here:

*[https://github.com/flairNLP/flair](https://github.com/flairNLP/flair)*

In addition to sentiment analysis, `Flair` provides the following functionality:

*   a biomedical NER library

*   a text embedding library

*   a PyTorch NLP framework

The final example of sentiment analysis is [Listing 9.8](#ch09.xhtml#list9.8) that displays the contents of the Python script `flair_sentiment.py` that uses the Flair library to perform sentiment analysis. Make sure that you invoke pip3 install flair.

## `NOTE`

*You might need to use Python 3.7 instead of Python 3.9.x in order to install* flair

***Listing 9.8: flair_sentiment.py***

```
# pip3 install flair 
from flair.models import TextClassifier 
from flair.data import Sentence 

classifier = TextClassifier.load('en-sentiment') 
sent = "I love Chicago deep dish pizza." 
ssent = Sentence(sent) 
classifier.predict(ssent) 
print('Sentence:  ', sent) 
print('Sentiment: ', ssent.labels) 
print() 

sent = "I love Chicago deep dish pizza!" 
ssent = Sentence(sent) 
classifier.predict(ssent) 
print('Sentence:  ', sent) 
print('Sentiment: ', ssent.labels) 
print() 

sent = "I love Chicago deep dish pizza!!!" 
ssent = Sentence(sent) 
classifier.predict(ssent) 
print('Sentence:  ', sent) 
print('Sentiment: ', ssent.labels) 
```

[Listing 9.8](#ch09.xhtml#list9.8) starts with two import statements and then initializes several variables, starting with the variable `classifier` (which is a model) as an instance of the `TextClassifier` class.

The next three code blocks in the same style as the code in [Listing 9.4](#ch09.xhtml#list9.4) whereby the variable `sent` is initialized as three text strings containing zero, one, and three exclamation points, respectively, after which the sentiment of each sentence is calculated via the `predict()` method of the `classifier` variable and then displayed. Now launch the code in [Listing 9.8](#ch09.xhtml#list9.8) and you will see the following output:

```
Sentence:   I love Chicago deep dish pizza. Sentiment:  [POSITIVE (0.999)]  Sentence:   I love Chicago deep dish pizza! Sentiment:  [POSITIVE (0.9996)]  Sentence:   I love Chicago deep dish pizza!!! Sentiment:  [POSITIVE (0.9997)] 
```

## `Detecting Spam`

Spam classification has been an on-going challenge ever since the introduction of email (or soon thereafter). Spam filters often use a Naïve Bayes classifier (discussed briefly in Chapter [6](#ch06.xhtml)). However, the nature of spam evolves over time, which means that spam classifiers must also evolve in order to handle new types of spam.

A spam classifier involves the following set of steps that are common to machine learning tasks:

Step 1: a labeled training dataset

Step 2: determining a set of features

Step 3: splitting the dataset into train/validation/test

Step 4: training the classifier

Step 5: performs some predictions on new data

Step 1 involves a good mixture of legitimate email message as well as spam email messages. Step 2 involves the typical tasks that are described in Chapter [3](#ch03.xhtml) (such as removing stop words, stemming, and calculating word frequencies). Step 3 requires a decent sized dataset. If your dataset is small, you can split its content into train and test and omit the validation (not the best solution).

Step 4 is a standard step, and you can use k-fold cross validation, which involves dividing the dataset into subsets (such as ten “folds”) and then repeating the training on nine of the ten folds, using the omitted fold as the test data. Calculate the average error after completing the cross fold validation. This technique is very handy for small datasets.

The final step involves making predictions and determining the accuracy of those predictions.

## `Logistic Regression and Sentiment Analysis`

Recall that classification problems involve predicting discrete outcomes, whereas regression problems involve predicting a value of a continuous variable. As you learned in a previous chapter logistic regression is actually a classification algorithm (not a regression algorithm). Logistic regression works well when the features and the target have a relatively simple relationship.

The Sklearn `LogisticRegression` class has these arguments: `penalty`, `dual`, `tol`, `C`, `fit_intercept`, `intercept_scaling`, `class_weight`, `random_state`, `solver`, `max_iter`, `verbose`, `warm_start`, `n_jobs`, and `l1_ratio`.

[Listing 9.9](#ch09.xhtml#list9.9) displays the contents of `log_reg_spam.py` that illustrates how to perform sentiment analysis with NLTK.

***LISTING 9.9: log_reg_spam.py***

```
import numpy as np 
import pandas as pd 
from sklearn.feature_extraction.text import TfidfVectorizer  #for sklearn version 0.24.0: 
from sklearn.linear_model import LogisticRegression 
from sklearn.model_selection import train_test_split, cross_val_score  # you can download the SMSSpamCollection dataset here: 
# [https://archive.ics.uci.edu/ml/machine-learning-databases/00228](https://archive.ics.uci.edu/ml/machine-learning-databases/00228) 
# NB: header "type\\ttext" was manually added to SMSSpamCollection 
df = pd.read_csv('SMSSpamCollection', delimiter='\\t') 
print("First five rows (before):") 
print(df.head(5)) 
print("-------------------------") 

# map ham/spam to 0/1 values: 
df['type'] = df['type'].map( {'ham':0 , 'spam':1} ) 
print("First five rows (after):") 
print(df.head(5)) 
print("-------------------------") 

# X contains text and y contains labels: 
X = df.iloc[:, 1].values 
y = df.iloc[:, 0].values 

# perform train/test split on the data (75/25): 
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size = 0.25, random_state = 0) 
#print("X_train:",X_train) 
#print("-------------------------") 

vectorizer = TfidfVectorizer() 
X_train = vectorizer.fit_transform(X_train) 
X_test  = vectorizer.transform(X_test) 

# train an instance of the LogisticRegression class: 
classifier = LogisticRegression() 
classifier.fit(X_train, y_train) 

# make predictions for the y_test data: 
y_pred = classifier.predict(y_test) 
print("predictions:",y_pred) 
print("-------------------------") 

# create the confusion matrix: 
from sklearn.metrics import confusion_matrix 
cm = confusion_matrix(y_test, y_pred) 
print("confusion matrix:") 
print(cm) 

true_neg, false_pos = cm[0] 
false_neg, true_pos = cm[1] 
all_values = true_pos + true_neg + false_pos + false_neg 

accuracy  = round((true_pos + true_neg) / all_values, 3) 
precision = round((true_pos) / (true_pos + false_pos),3) 
recall    = round((true_pos) / (true_pos + false_neg),3) 
f1        = round(2 * (precision*recall) / (precision+recall),3) 

print("--------------------------\\n") 
print('Accuracy:  {}'.format(accuracy)) 
print('Precision: {}'.format(precision)) 
print('Recall:    {}'.format(recall)) 
print('F1 Score:  {}'.format(f1)) 
```
