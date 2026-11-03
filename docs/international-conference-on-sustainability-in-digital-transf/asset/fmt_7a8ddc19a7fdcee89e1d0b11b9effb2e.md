
By seeming to be a reliable party in an electronic connection, “phishers” seek to steal sensitive information such as login credentials and credit card numbers. Cybercriminals use this method to get access to sensitive user data. The thieves will replicate legitimate websites in order to trick users. If a user enters sensitive information (such as a password, bank information, or account credentials) into one of these fraudulent websites \[[1](#ch28.xhtml#ref28_1), [2](#ch28.xhtml#ref28_2) and [3](#ch28.xhtml#ref28_3)\], they risk becoming a victim of identity theft. After gaining access to your account, a criminal may make unauthorised purchases, wire funds, or do other fraudulent actions \[[4](#ch28.xhtml#ref28_4), [5](#ch28.xhtml#ref28_5)\]. Since phishing toolkits like Rock Phish and Super Phisher make it simple for attackers to set up fake websites, the number of these sites has also increased \[[6](#ch28.xhtml#ref28_6), [7](#ch28.xhtml#ref28_7)\]. These malicious sites might copy the source code of legitimate ones \[[8](#ch28.xhtml#ref28_8)\]. Therefore, a reliable anti-phishing solution is required to identify phishing websites and manage this security risk. Users are still vulnerable to new phishing assaults, despite the fact that researchers have created a number of anti-phishing detections, such as employing heuristic \[[9](#ch28.xhtml#ref28_9)\], blacklist \[[10](#ch28.xhtml#ref28_10)\], and content-based method \[[11](#ch28.xhtml#ref28_11)\]. This occurs because attackers are dynamic in their behaviour, constantly switching up their method of operation to elude detection \[[12](#ch28.xhtml#ref28_12), [13](#ch28.xhtml#ref28_13)\]. This encourages us to explore new methods of detecting phishing assaults by using machine learning classifiers. Artificial intelligence (`AI`) subfield known as “machine learning” employs a data-mining strategy to unearth previously hidden or previously recognised characteristics within a given dataset \[[14](#ch28.xhtml#ref28_14)\]. After that, a classification algorithm is used to the retrieved characteristics to determine if the assaults are phishing or not. In this research, we present a technique for detecting phishing attempts and checking for malicious code on webpages. The suggested research makes use of a heuristic-based strategy and website features.

The given paper is organized into following sections. Section 2 provides a literature review of studies regarding types of phishing attacks. Section 3 discusses methodology of the proposed approach. It involves defining classifiers like `RF` and `NB`. Section 4 presents results and analysis followed by conclusion and references.

## Literature Review

Today, phishing assaults may take many forms. There are three main forms of phishing attacks: social engineering, malware, and content injection. For the purpose of tricking the unwary into visiting a malicious website, the term “deceptive phishing” \[[15](#ch28.xhtml#ref28_15)\] is used to describe the practice of sending mass emails to multiple recipients with the hopes that at least one of them will fall for a scam and click on a link to a fake site or re-enter their account information. The term “malware-based phishing” describes assaults that are designed to install and run dangerous software on victims’ computers \[[16](#ch28.xhtml#ref28_16), [17](#ch28.xhtml#ref28_17)\]. The most common method of spreading malware is via downloadable attachments sent over email. Key loggers and screen grabbers, two types of spyware that record keystrokes and relay the data to the phisher are often used in phishing assaults. The victim’s PC may be taken over in subsequent attacks \[[18](#ch28.xhtml#ref28_18)\]. Content injection is a phishing tactic in which a malicious actor modifies legitimate website content. This is done to trick the user into visiting a website that is not the actual one so that sensitive information may be submitted \[[19](#ch28.xhtml#ref28_19)\]. Blacklist-based methods, content-based methods, and heuristic-based methods are all employed to combat phishing assaults \[[20](#ch28.xhtml#ref28_20)\].

## Proposed Methodology

### A. Dataset Collection from Websites or Repositories

Dataset collection is the initial step of implementation. During the dataset phase, it is crucial to ensure the reliability of the obtained results. Phishing and legitimate operations may be better understood and explained with the use of this dataset. After the dataset has been analyzed, the findings may be utilized to make predictions about potential phishing attacks. The Phishing website dataset is the source of the dataset on Kaggle \[[21](#ch28.xhtml#ref28_21)\]. Thirty distinct characteristics of phishing websites have been compiled. The gathered dataset contains the categorical variables “`Legitimate`,” “`Suspicious`,” and “`Phishy`,” which have been converted to numeric values by substituting the values “1,” “0,” and “-1,” respectively \[[21](#ch28.xhtml#ref28_21)\].

### B. Defining Phishing Website Features

The features of phishing website are collected and are subjected to noise removal. It means the final phishing features are reduced by removing redundant and repetitive features.

### C. Extracting Features and Attributes

In order to improve the prediction model’s accuracy, feature selection techniques were utilized to isolate and eliminate superfluous details. In order to classify the phishing website, its characteristics were first learned. In this research, the feature selection method is used to identify the most relevant attributes for efficient phishing website detection. As a result, the original list of 30 phishing elements was whittled down to only 10. This is done so that a distinguishable difference may be seen between legitimate and fraudulent websites.

### D. Classifiers- `RF` and `NB`

The random forest (`RF`) is a supervised machine learning approach. It may be used for regression analysis as well as classification \[[22](#ch28.xhtml#ref28_22)\]. The system is comprised of several decision trees. The technique operates by using a stochastic process to choose attributes at random, afterwards generating numerous decision trees and thereafter computing the average outcome.

The Naïve bayes (`NB`) algorithm, as described in reference \[[23](#ch28.xhtml#ref28_23)\], is designed to be used on the premise that the characteristics within each class are independent of each other. However, empirical evidence suggests that `NB` may still perform well even when this assumption is violated.

### E. Testing and Training of Model

To predict how well a model would function in the real world, researchers utilize `n`-fold cross-validation or rotation estimation. The process entails randomly dividing a sample dataset `D` into `s` distinct and non-overlapping parts. In every iteration, the model is trained using the whole dataset and then evaluated on the remaining folds. In the present study, the value of `n` was set to 10 in our suggested technique.

### F. Evaluation Based on Metrics

The appraisal of predictive data mining algorithms may be assessed using many metrics. When evaluating the predictability of various predictive data mining methods, it is necessary to evaluate certain values that assess the model’s goodness of fit and error measures. The metrics utilized during the research are as follows.

(1) `Precision = TP/(TP + FP)`

(2) `Recall = TP / (TP + FN)`

(3) `F-measure = (2 * precision * recall) / (precision + recall)`

(4) `True Positive rate (TPR) = TP / positive`

(5) `False Positive rate (FPR) = FP / negative`

[Figure 28.1](#ch28.xhtml#fig28_1) presents the flow of methodology adopted in the study.

![Figure 28.1 Workflow of the proposed approach](images/fig28_1_B.jpg)

[Figure 28.1 Workflow of the proposed approach](#ch28.xhtml#R_fig28_1)

## Result and Implementation
