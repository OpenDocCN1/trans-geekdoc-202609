
## Spam bot and Cyberbullying Detection in OSN using DL

![](img/66ecdb8eb8654ae1c99705e55a45a836_362_0.png)

**FIGURE 18.8** Literature Reviewed.

Researchers have used outdated detection methods using various techniques. Our systematic review was purely based on recent papers from 2018 to 2022.

Several review papers have not provided clarifications on how spam bots and cyberbullying are detected using various DL algorithm techniques. This systematic review briefly explains all recently used DL algorithms for detecting spam bots and cyberbullying in OSN.

Since 2022, few studies have been conducted on the detection of spam bots and cyberbullying in OSNs using DL. Many studies have been directed toward detecting spam bots and cyberbullying through the use of ML.

In 2019, some research papers related to DL techniques were published. This systematic review aimed to gather all research papers related to DL techniques to provide ideas for future inventions, as depicted in Figure 18.8.

In the systematic review, a detailed description was provided for OSNs, botnets, spam and its types, cyberbullying and its types, social media bots, various DL techniques, spam bot and cyberbullying detection methods, and the basic stages for detecting spam bots and cyberbullying in OSNs using DL. This systematic review is then organized into the following sections:

- Section 18.2 consists of the review methodology.
- Section 18.3 includes the basic performance metrics.
- Section 18.4 contains the literature survey of spam bot and cyberbullying detection in OSNs using DL, while section 18.5 includes the search gap analysis and outcome of the literature survey.
- Section 18.6 presents the conclusion of this review.

### 18.2 PROPOSED METHODOLOGY

The methodology to explain a systematic review, as shown in Figure 18.9, is divided into three stages: planning, identifying, and reporting stages.

During the first stage, or the planning stage, a researcher should emphasize the need to conduct a systematic review and formulate research queries that will be answered by their work by showing the accuracy of the model.

During the second stage, or the identification stage, the researcher should specify the search strategy employed, the journals or research papers consulted, and the analysis of various models used. In the final stage, or the reporting stage, the researcher should present the full concept of the research domain, including the overall mechanism and the results obtained.

The remainder of this chapter includes the previously mentioned methodology. Initially, questions related to spam bots and cyberbullying are identified. The exploration strategies and the papers reviewed are then presented.

Figure 18.9 depicts the discussion of the overall spam bot and cyberbullying detection methods, including the objectives of detecting spam bots and cyberbullying, comparisons with other methods, the models and datasets used, and the parameters evaluated in previous studies.

![](img/66ecdb8eb8654ae1c99705e55a45a836_363_0.png)

**FIGURE 18.9** Review Methodology.

#### 18.2.1 RESEARCH QUERIES

The primary objective of this systematic review is to answer the following queries:

- Q1. What are the models proposed to detect spam bots and cyberbullying in OSNs?
- Q2. What are the metrics calculated to identify the effectiveness of the proposed models?
- Q3. What are the datasets used to train the model?
- Q4. What are the performance metrics analyzed?
- Q5. What are the stages used in DL for spam bot and cyberbullying detection?

#### 18.2.2 Search Strategy

Based on the research queries and other targets, the search process is divided into three stages: word-based, crawling-based, and inclusion-/exclusion-based searching (Figure 18.10).

Word-based searching is a strategy for collecting data using words related to the domain. This involves exploring an inbuilt source, such as Google Scholar, to retrieve information. Crawling-based searching is a strategy for exploring previous literature in the same domain.

Inclusion-/exclusion-based searching is conducted to determine whether the papers reviewed are relevant to a particular domain.

![](img/66ecdb8eb8654ae1c99705e55a45a836_364_0.png)

**FIGURE 18.10** Searching Strategies.

##### 18.2.2.1 Word Search

Based on the technique and model used, the word search was conducted.

- SBD and cyberbullying
- Deep learning
- CNN model
- RNN model

##### 18.2.2.2 Resources Referred

The following information-gathering centers were found using Google Scholar and other search engines:

- IEEE
- Springer
- Elsevier
- Research Gate
- Science Direct

#### 18.2.3 STUDY CHOICE

A total of 1500 published studies were taken using the mentioned search strategy. Of these, 730 papers were confirmed and selected for further validation, as depicted in Figure 18.11. Additional filtration of these published studies was necessary because several of these publications were outside the scope of the current study. For this purpose, the following inclusion and exclusion rules were applied:

1. Inclusion rules
   - Include surveys conducted from 2018 to 2022.
   - Include surveys in the domain of spam bot and cyberbullying detection in OSNs.
   - Include surveys written only in the English language.
2. Exclusion rules
   - Exclude surveys without proposed methodologies.
   - Exclude surveys and review papers.
   - Exclude surveys with unclear information about the publication.

![](img/66ecdb8eb8654ae1c99705e55a45a836_365_0.png)

**FIGURE 18.11** Study Choice.

#### 18.2.4 QUALITY EVALUATION TOOLS

The quality of the survey papers was evaluated using the following quality evaluation tools:

- Was the flow of writing in the literature presented well?
- Did the publication identify the contribution of the research domain?
- Was there sufficient information about spam bot and cyberbullying detection provided in the literature?
- Did the publication briefly describe terminologies, such as abbreviations used?
- Were all OSNs defined?
- Were the results of the proposed models revealed?
- Did the proposed models attain optimal solutions for various performance evaluations?

### 18.3 PERFORMANCE METRICS FOR SPAM BOT AND CYBERBULLYING DETECTION

The most commonly used performance metrics for the methods proposed by different researchers to detect spam bots and cyberbullying in OSNs using a DL approach are accuracy and average accuracy, precision and average precision, recall and average recall, F-measure and average F-measure, G-measure, specificity, and average specificity.

#### 18.3.1 Accuracy and Average Accuracy

The degree to which the number of predicted genuine and fake tweets in a dataset is correct is referred to as accuracy. If the accuracy level is 100%, then the proposed method will be of value. Equations 18.1 and 18.2 were used to calculate accuracy and average accuracy, respectively:

$$A = \frac{S_p + S_n}{S} \tag{18.1}$$

$$AA = \frac{1}{n} \cdot \sum_{k=1}^{n} A_k \tag{18.2}$$

where $S$ is the total population. The $S$ denoted here represents

$$S_p + S_n + R_p + R_n$$

#### 18.3.2 Precision and Average Precision

Precision is the measurement of the number of accurately classified genuine bots among all the information in the testing set. Equations 18.3 and 18.4 were used to calculate precision and average precision, respectively:

$$P = \frac{S_p}{S_p + R_p} \tag{18.3}$$

$$AP = \frac{1}{n} \sum_{k=1}^{n} P_k \tag{18.4}$$

#### 18.3.3 Recall and Average Recall

Recall is the measurement of the number of accurately identified genuine bots among all genuine information in the testing set. Equations 18.5 and 18.6 were used to evaluate recall and average recall, respectively:

$$R = \frac{S_p}{S_p + R_n} \tag{18.5}$$

$$AR = \frac{1}{n} \sum_{k=1}^{n} R_k \tag{18.6}$$

#### 18.3.4 F-Measure

F-measure is the balanced mean of both the recall and precision metrics. Equations 18.7 and 18.8 were used to calculate F-measure and average F-measure, respectively:

$$F = 2 \times \frac{P \times R}{P + R} \tag{18.7}$$

$$AF = \frac{1}{n} \sum_{k=1}^{n} F_k \tag{18.8}$$

#### 18.3.5 G-Measure

G-measure is the square root of precision and recall. Equation 18.9 was used to calculate G-measure:

$$g = \sqrt{P \times R} \tag{18.9}$$

#### 18.3.6 Specificity and Average Specificity

Specificity was used to calculate the capacity of the classifier to accurately identify true-negative results. Equations 18.10 and 18.11 were used to evaluate specificity and average specificity, respectively:

$$Sp = \frac{S_n}{S_n + R_p} \tag{18.10}$$

$$ASp = \frac{1}{n} \sum_{k=1}^{n} Sp_k \tag{18.11}$$
