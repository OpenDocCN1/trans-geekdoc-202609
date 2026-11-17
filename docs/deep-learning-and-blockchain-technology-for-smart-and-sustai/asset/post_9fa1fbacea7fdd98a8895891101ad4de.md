
reviewed, and email monitoring settings—beginning with phishing mail—have been scrutinised. Both static and dynamic analytics are utilised to identify phishing pages and domain name impersonation. Credential sharing on phishing websites has been investigated.

In [15], the author locates and sorts the logos of “zero-hour” phishing sites using computer vision methods for object detection. For this goal, scale-invariant visual representations of target trademark logos have been created using the features of the HOG. Throughout the classification procedure, an SVM classifier equipped with max-margin loss has been used to handle less training images and false positives. An additional resource for researchers is a publicly accessible dataset of 3,060 training and 1979 unique phishing and legitimate web page/email samples, together with bounding box annotations.

In [16], a multi-stage strategy is used to detect phishing email threats using NLP and machine learning. The suggested multi-stage methodology includes enhanced learning approaches for resampling and cross-validation, tokenization, feature extraction and selection, feature engineering in NLP, and hyperparameter setting. Two methods have been provided for implementing the suggested methodology: one that combines PCA and LSA (Latent Semantic Analysis) with mutual information and Chi-Square statistics. Both approaches tackle “the curse of dimensionality” in terms of sparseness and the amount of environmental data that must be gathered.

In 2021, the authors [17] proposed Rule-Based and Semantic-Based analyses for improving classification accuracy of machine learning algorithms. In this proposed work, subject and content features of email have been considered for classifying emails into spam or ham. After applying this proposed methodology, the classification accuracies are improved.

## 2.3 Proposed Methodology

The proposed work consists of five modules namely Dataset collection, Preprocessing, Applying RBSA and SBFS, Applying BOW model, and Email classification using ML algorithms. In this work, the publicly available Enron email dataset has been used for comparing the efficiency of ML algorithms with RBSA and SBFS and ML algorithms without RBSA and SBFS. Subject and Text features of the emails have been extracted from the email dataset. Based on various rules framed on RBSA algorithm, the words of subject are analysed. The existence of spam words is also found in order to compute the weight of email. The Bag of Words model has been applied on body of email to find the frequency of words in body text. This BOW model produces sparse matrix as output, and it is augmented with the output of RBSA and SBFS algorithms. The machine learning algorithms such as SVM, Multinomial Naive Bayes, Gaussian Naive Bayes, and Bernoulli Naive Bayes have been applied for classifying emails into spam or ham. The performance of the proposed methodology has been compared with traditional method without using RBSA and SBFS.

### 2.3.1 Dataset Collection

The Enron email dataset [18] is used in this suggested work. There are 5,643 emails in total in dataset D. Since we only focus on subject and body features of email, unnecessary columns have been deleted from the dataset. In a data frame, the columns Label, Subjects, Text, and Weight are kept for later processing.

### 2.3.2 Preprocessing

In text processing and natural language processing [19,20], preprocessing is a crucial step. Preprocessing is used in email contents in order to minimise the amount of features. Text typically includes extraneous words, URLs, HTML elements, meaningless words, several words with the same meaning, special characters, and digits. These are eliminated from the provided input text to increase machine learning algorithms’ accuracy. Ham is encoded as 0, but spam is 1. The class labels can be made normal by using these encodings. Text labels should be changed to numeric labels since they are not comparable.

The Subject and Text columns are then subjected to tokenization. Word tokenization is used to represent the content in the Subject and Text columns. Words like “in,” “the,” “this,” “that,” “is,” etc. are stop words. Prior to using machine learning techniques, these terms should be disregarded because they are more common and do not help with the classification process. Eliminating stop words increases classification accuracy because ML algorithms process fewer tokens.

### 2.3.3 Applying RBSA and SBFS on Subject

Finding spam phrases in the subject area of emails is the primary goal of RBSA. The most popular phrases used in spam are gathered from online resources. This method that is suggested follows a few rules. Several spam emails are cited in the formulation of these guidelines. Based on these guidelines, the weight is calculated for every email in the sample. The RBSA method that has been presented aids in the effective identification of spam emails.

**Algorithm:** Rule-Based Subject Analysis
**Input:** Words of subject
**Output:** Spam_term_weight

- 1. Words are compared with collection of spam words.
- 2. If a word is spam word then it checks for various conditions
  - 2.1 If word has ‘?’ Or Capitalized Or Alphanumeric Or length > Max then increase number of spam terms of the email
- 3. Spam_term_weight=spam_term/No. of emails
- 4. Finally, computed spam term is assigned to spam_term_weight for each email

After analysing subject feature of emails, the body features are analysed for feature reduction. This is achieved by combining the words with similar meaning in each email. The SBFS algorithm finds the synonym of each word and combines the words with the same synonym. The main objective of this module is reducing the number of features, which improves the classification accuracy.

**Algorithm:** SBFS
**Input:** Words in the body of emails
**Output:** Reduced feature set

- 1. Synonym of each word in an email body is found.
- 2. If the synonym set is empty for a word, then it is removed.
- 3. If a word has a synonym, then compare it with the synonym of other words.
- 4. If multiple words have similar meaning, then merge into a single word in the body.
- 5. Reduced feature set is obtained as an output.

### 2.3.4 Applying BOW Model

Machine learning algorithms can operate only on numerical values. Hence, the reduced textual features are then converted into numeric values using the Bag of Words model. This model counts the number of occurrences of words in the email. To reduce features again, the words with the highest count have been considered for further processing. Words with a minimum count are discarded since they have no impact on classification process. In this proposed model, 0.25 has been considered as minimum threshold value for the count of the words. Words with count greater than 0.25 have been taken for classification process. Words with frequency less than or equal to 0.25 are discarded. After obtaining the sparse matrix for the email body dataset, it is combined with spam_term_weight from the subject field. The classification models have been built for the training and test datasets using all classifiers.

### 2.3.5 Email Classification Using ML Algorithms

The Classification module is the most crucial one for our work. To classify the emails as spam or ham, four classifiers have been implemented: SVM [21,22], Multinomial Naive Bayes, Gaussian Naive Bayes, and Bernoulli Naive Bayes. Eighty percent of this dataset is for training, while 20% is for testing.

For the training dataset, classification models utilising Bernoulli Naive Bayes, Multinomial Naive Bayes, SVM, and Gaussian Naive Bayes have been developed. Initially, a model for the training dataset is constructed using an SVM classifier. This classifier effectively manages large dataset volumes. For linear regression and classification, the supervised machine learning algorithm SVM is appropriate. This approach performs admirably in both high- and low-dimensional spaces. Drawing a line or plane is necessary to divide the data points. This technique works well for prediction, text categorization, and pattern recognition. We employ it in our proposed strategy to classify the supplied set of emails into two classes: spam and ham, because of its rapid functioning nature. Drawing a proper hyperplane that yields a maximal margin allows for this separation.

The multinomial model Naïve Bayes classifier is constructed for the training dataset, which classifies emails as either spam or ham. The MNB classifier is capable of efficiently classifying text. The word counts or word frequencies are the input required for this MNB classifier.

The Gaussian Naïve Bayes model is then constructed for the training dataset. The provided email set is once more divided into spam and ham categories. The continuous values for each class are dispersed using a Gaussian distribution. Take note that continuous data is used by this classifier. Once more, test data are categorised as spam or ham using the pre-built Gaussian Naïve Bayes model.

The Bernoulli Naïve Bayes algorithm is the next classifier, which functions similarly to multinomial Naïve Bayes. The predictors are used as Boolean variables by the Bernoulli method, which is the only difference. Put differently, the parameter values are either yes or no, and we go on to the class variable prediction.

The training dataset is used to build the classifier model using the Bernoulli Naïve Bayes algorithm. To classify emails in the test dataset, the same model is also used. There is also a comparison between the four classifiers’ accuracy levels. SVMs are shown to provide the best degree of accuracy.

## 2.4 Results and Discussions

### 2.4.1 Machine Learning Algorithms with RBSA and SBFS Algorithms

Eighty percentage of the training dataset has been considered for building classification models using all the four classifiers. Once the model is built
