
Kesu Malviya et al (2021) developed certain standard models such as SVM and Linear Model. The Transformers model with Reddit data was achieved a high accuracy for determining depression in social media users. Transformer model is nothing but a deep learning technique that does the mechanism of self-attention which allows the input to communicate with each other and identify where there should be more attention. The dataset used in this model have given a balanced and smooth implementation so obtained the higher accuracy of 98%.

Sudha et al (2020) developed a depression detection system, that detects depression from the social media user, through machine learning technique. In this work, the depression was detected by using Naïve Bayes, Decision Tree, Random Forest algorithms and K-Nearest Neighbors. Further, continuous analysing of previous readings of the user to detect the changes in the depression level. And also, the user is immediately warned about their depression level and they are urged to seek the help of the professionals. Data was obtained from the patients or users on the regular basis in the form of text. Finally, accuracy of the model was calculated through evaluation metrics.

Akshi et al (2019) proposed an Anxious Depression (AD) prediction system for social media tweets. The feature set of the model was described by using a 5-attributes vector-like word, timing, frequency, sentiment, and contrast based on the user posting pattern. This lexicon is constructed to identify the existence of anxiety indicators. Time and frequency of tweets are studied for lack of symmetry and opinion polarity analytics was done to find out inconsistencies in behavioral posts. The model was trained using three classifiers like Random Forest, multinomial Naive Bayes, Gradient Boosting and take major voting using an ensemble voting classifier. The classification accuracy of 85.09% was achieved in this model for 100 users’ tweets from social media.

Zhang et al (2019) developed a system for constructing a sentiment lexicon of each topic. It was an important basement for analysing sentiment in social networks. Though, in social media need a sentiment lexicon and it was constructed based on filtering text model, Sentiment relationship graph, CRM Model, Spectral clustering model. By using this system, it was solved the sentiment words of topics and increase the performance and accuracy of the sentiment lexicon.

Giuntini et al (2021) proposed TROAD (Tracing the Roadmap of Depressive Users) framework for identifying consecutive patterns and long-time mental state depressed user in social network sites. This algorithm monitors the frequent activity of the user’s post on the Reddit dataset and it maintains the user’s silence for generating patterns. It takes psychological and contextual information from user’s comment. It was hard in governing negative emotions common among users with depression and readability was poor due to consecutive patterns.

Hatoon AlSagri et al (2020) proposed a system for detecting depressed Twitter Tweets based on user’s tweets and network behavior by applying Machine learning algorithms. Classifiers are trained and tested based on users’ activities features from the network and check whether the person is depressed or not. The classifiers used for this system was Naive Bayes, Linear SVM, Decision Tree. Evaluation metrics like accuracy, F1-score was found for evaluating the system.

Anu Priya et al (2020) offered a system for forecasting depression, stress level and anxiety by using machine learning algorithms. Data collection was done through hired and unhired people throughout diverse cultures and communities through DASS 21(Depression, Anxiety, Stress Scale questionnaire). In this work, F1-score was found for identifying the high-quality accuracy framework among the five algorithms like Naive Bayes, K-NN classifier, Decision Tree classifier, Random Forest classifier and Support Vector Machine. The accuracy of Naive Bayes became observed to be the highest, even though Random Forest recognized as the high-quality model. Due to this problem, this model produced imbalanced classes so the selection of high-quality model was made on the premise of the f1 score and solve the imbalanced partitioning.

Suyash Dabhane et al (2020) proposed work on detection of depression using ML techniques have been functioned out. Here Ensemble learning approach and various machine learning methods were used to detect depression. Machine Learning algorithms along with the ensemble method is helped to build an efficient and high accurate model for detecting depression on social media.

G. Geetha et al (2020) developed a work to help patients suffering from depression by earlier identification of the signs and symptoms of depression which was more useful to them. This Method has taken the writing pattern of textual contents and linguistic clues of tweets for identification of depression users. Naive Bayes, Support Vector Machine, Logistic Regression and Random Forest classifiers were used for classifying textual and linguistic tweets. The accuracy of Bayes theorem as 88.5%, Random Forest as 95.1%, Support Vector Machine as 96.1% and Logistic Regression was 96.2%. The result has been concluded that Logistic Regression have given the better performance among the classifiers.

## MAIN FOCUS OF THE CHAPTER

The idea of this work is to predict the depression from social media users’ tweets by using the depressive and non-depressive lexicons and machine learning algorithms. This work uses the various machine learning classifier algorithms like SVM, Naïve Bayes, ANN and compare the performance of these algorithms using Accuracy, Precision, Recall and F1-Score.

## PROPOSED METHODOLOGY

The proposed work involves different Machine Learning approaches to classify and predict the depressive features (Depressed and Non-Depressed) from the dataset. The dataset consists of comments of users from social media. The proposed system made up of five steps:

- 1. Data Pre-Processing
- 2. Feature Extraction
- 3. Data Splitting
- 4. Classification
- 5. Performance Evaluation

### 1. Dataset Description

The dataset considered for this work is Kaggle which carries 50997 records and which are Twitter comments of the user in social media. Initially, the dataset doesn’t have class labels so converting it into supervised data is the part of this work after structuring the comments are labeled as depressive, non-depressive and neutral.

Figure 1 presents the flow of predicting depressive features using two aspects training and testing. It encompasses Machine Learning Classifiers like Naive Bayes, Non-linear Support vector Machine and Artificial Neural Network. It includes sub methods such as text pre-processing, feature extraction and labelling. Finally classified labels are evaluated through performance evaluation.

### Figure 1. The overall architecture of proposed system

![](img/20813928ec98c7f6fbdbab0d52bde2f1_273_0.png)

### 2. Data Pre-Processing

Text preprocessing is a way to remove the unwanted information from the text data before send into the model. The unwanted information from the raw data in various representation like stop words, punctuations, emotions, etc. Pre-processing is common for both training and testing of the model. This step contains four processes which are explained below:

- i) Remove Stop Words

Stop words are words, they don’t have any semantic information for the whole online comments. It includes pronouns, auxiliary verbs, determinant, interjections, etc. The elimination of stop words and elimination of special symbols support the sequence of sentiment classification framework for achieving better performance and accuracy.

- ii) Tokenization

Tokenization is used for separating each sentence into tokens. Each tokens are considered as words in the sentence.

- iii) Lemmatization

In this process, words are lemmatized to root or lemmas. It looks through the provided dictionary to extract the base form of the word. Along with word reduction, it also considers the complete language vocabulary for doing morphological analysis of the word.

- iv) It also removes the URLs, Numbers, HTML Tags, Special Characters, and Hashtags From the User Comments

This data pre-processing is done by using python language with Natural Language Toolkit (NLTK) and it takes forty seven lines of code including the function as word_tokenize(), WordNetLemmatizer() and stopwords.words().

### 3. Feature Extraction and Labelling

In this work Count-Vectorizer method is used to extract the feature from the user data. It is used to transform the texts into vectors according to frequency of each word present in the entire documents. Count-Vectorizer converts the text documents to token counts and construct the sparse matrix. This incorporation produces a sparse representation of the count. The collection of depressive words within the index of 90 and above 90 it has neutral words, totally the collected lexicon has 130 words (Genghao et al., n.d.; Akshi Kumar et al., n.d.).

Count-vectorizer forms the sparse matrix or feature vector based on the frequency count of the user comments. The initial un-labeled dataset is labeled by extracting the depressive words of the particular user comment based on the results of the feature vector. If the depressive words are found in the user comment it is labeled as Depressed or Neutral based on the index otherwise it is labeled as non-depressed. This step takes one hundred and thirty lines of codes including the functions as CountVectorizer(), fit(), get_feature_names(), transform().

The collected words are considered as the feature for depressive users. Count-vectorizer forms the sparse matrix or feature vector based on the frequency count of the user comments. The initial un-labeled dataset is labeled by extracting the depressive words of the particular user comment based on the results of the feature vector. If the depressive words are found in the user comment it is labeled as Depressed or Neutral based on the index otherwise it is labeled as non-depressed.

Feature Extraction Algorithms includes two main steps BOW (Bag-of-Words) and Label Encoding. The steps of each algorithm are listed below in Algorithm 1 and Algorithm 2:

### Algorithm 1 Bag of words()

```
// Input
: tweet:Each tweet of user
// Output
: bow_feature: Feature Vector of each tweet
{
Initialize feature_vectors bow_feature = [0,0,...,0]
for words in tweet do
if words in dictionary then
```
