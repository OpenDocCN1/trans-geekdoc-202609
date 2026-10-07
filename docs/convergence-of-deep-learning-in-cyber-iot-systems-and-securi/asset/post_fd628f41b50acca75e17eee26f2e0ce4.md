
## 218 CONVERGENCE OF DL In Cyber-IoT Systems AND SECURITY

![](img/081dc7f102a3793cb08980a6e19b8f17_241_0.png)

Figure 10.1 Detailed flowchart of the methodology used.

Flowchart for the algorithm is given in Figure 10.1. Root Verb Extraction and associated algorithms are available in the published paper [5]. Details of service used for POS tagging has been acknowledged at last. Training and test sets are prepared independently. Cross validation of 10 folds is used with shuffling for avoiding any biasness.

## 10.6 Results and Discussion

### 10.6.1 Result Summary for TDIL Dataset

A total number of 340 questions are fired to the system. 326 questions are classified correctly among eighty-six classes. So, the accuracy of the question classification is 95.88%.

Among these correctly classified 326 questions, for 322 questions the answer A returned by the system contains exact answer EA. So, the coarse-grain accuracy is 98.77% for answer prediction.

Among these correctly classified 326 questions, for 304 questions the answer returned by the system is the exact answer EA. So, the fine-grain accuracy is 93.25% for answer prediction.

### 10.6.2 Result Summary for SQuAD Dataset

A total number of 952 questions are fired to the translated SQuAD. Among 952 questions, 916 questions are classified correctly among 86 classes. So, the accuracy of the question classification is 96.21%.

Among these correctly classified 916 questions, for 900 questions the answer A returned by the system contains exact answer EA. So, the coarse-grain accuracy is 98.25% for answer prediction.

Among these correctly classified 916 questions, for 850 questions the answer A returned by the system is the exact answer EA. So, the fine-grain accuracy is 92.79% for answer prediction.

Examples of retrieved answers are given in the next section (Table 10.1).

## 220 CONVERGENCE OF DL IN CYBER-IoT SYSTEMS AND SECURITY

### 10.6.3 Examples of Retrieved Answers

**Table 10.1** Example questions and their retrieved answers.

| Questions | Predicted class(es) | Answer retrieved |
|---|---|--|
| Q1. আনন্দমঠ কর লেখা? ('Ananda Math Kar Lekha?' or 'Who is the author of the Anandamath?') | Education, Mass media | 1. বঙ্কিমচন্দ্র |
| Q2. কবে বঙ্কিমচন্দ্রকে হাওড়ায় বদ করা হয়? ('Kobe Bankimandra Howrate Badli Kora Hoy?' or 'When Bankimandra was transferred to Howrah?') | Essay | 1. ১৮৮৩ শ্লিষ্ট |
| Q3. সগররাজ পত্রের কে ছিলেন? ('Sagar RajarpoutkeChhilen?' or 'Who was the grandson of king Sagar?') | Class not determined | No Answer Retrieved |
| Q4. স্যার রিচার্ড হ্যাডলিন কোন দেশের খেলোয়া? ('Sir Richard Hadley Desher Kloar?' or 'Richard Hadley played for which country?') | Games and Sports | 1. নিউজিেলিঞ্জের |
| Q5. রক্তশূন্যতা নিবারনের সেরা উপায় কি? ('Rokpalta Nibaroner resto Up Ki?' or 'What is the best way to avoid anemia?') | Home Science | 1. দৈনিক আহারে রক্ত রোগের উপাদান |
| Q6. “বাজল তোমার আলোর বেগের.”—লালেরের সুরকার কে? (“Bajlo Tomlar Alor Benu.”— or 'Who is the composer of the song “Bajlo tomar Alor Benu.”') | Music | 1. পঞ্জুম কুমার্লার 2. সুপ্রীতি ঘোষ |

### 10.6.4 Calculation of TP, TN, FP, FN, Accuracy, Precision, Recall, and F1 score

TP = True Positive = The system predicts that the answer of the question is present in the repository and actually the repository has the answer (the answer is returned as part of output)

TN = True Negative = The system predicts that the answer of the question is not present in the repository and actually the repository does not contain the answer

FP = False Positive = The system predicts that the answer of the question is present in the repository but actually the repository does not contain the answer

FN = False Negative = The system predicts that the answer of the question is not present in the repository and actually the repository contains the answer

- TP for TDIL dataset is TP_TDIL=322
- TN for TDIL dataset is TN_TDIL=9
- FP for TDIL dataset is FP_TDIL=3
- FN for TDIL dataset is FN_TDIL=6

So, accuracy for TDIL dataset is Accuracy_TDIL = (TP+TN)/(TP+TN+FP+FN) = 97.35

So, precision for TDIL dataset is Precision_TDIL=TP/(TP+FP) = 99.07

So, recall for TDIL dataset is Recall_TDIL=TP/(TP+FN) = 98.17

So, F1 score for TDIL dataset is F1 score= 2*(Recall*Precision)/ (Recall + Precision) = 1941.4/197.24 = 98.61

TP for translated SQuAD dataset is TP_SQuAD=900
TN for translated SQuAD dataset is TN_SQuAD=25
FP for translated SQuAD dataset is FP_SQuAD=14
FN for translated SQuAD dataset is FN_SQuAD=13

So, accuracy for translated SQuAD dataset is Accuracy_SQuAD = (TP+TN)/(TP+TN+FP+FN) = 97.16

So, precision for translated SQuAD dataset is Precision_SQuAD = TP/(TP+FP) = 98.46

So, recall for translated SQuAD dataset is Recall_SQuAD=TP/(TP+FN) = 98.57

## 222 CONVERGENCE OF DL IN CYBER-IoT SYSTEMS AND SECURITY

So, F1 score for translated SQuAD dataset is F1 score_SQuAD = 2*(Recall*(Precision))/(Recall + Precision) = 19410.4/197.03 = 98.51

### 10.6.5 Comparison of Result with other Methods and Dataset

Performance of the question classification techniques of different research groups is presented in Table 10.2.
Table 10.3 represents the F1 score calculation of QA system working in SQuAD dataset.

**Table 10.2** Comparison of accuracy for question classification with previous work.

| Author | Language | Dataset | QC percentage |
|---|---|---|---|
| Banerjee and his group [2] | Bengali | Own created dataset [2] | 87.79% |
| Sarkander and his group [8] | Bengali | SUST database | 90.5% |
| Monisha et al. [1] | Bengali | SUST database | 90.6% |
| M A Islam and his group [6] | Bengali | University database | 95.6% |
| A Das and D Saha | Bengali | TDIL | 95.88% |
| A Das and D Saha | Bengali | Translated SQuAD | 96.21% |

**Table 10.3** Comparison of F1 score with previous work.

| Author | Language | Dataset | F1 score |
|---|---|---|---|
| Z Lan et al. [12] (Albert system) | English | SQuAD | 92.215 |||Zhang et al. [13] | English | SQuAD | 93.11 |
| A Das and D Saha | Bengali | TDIL | 98.61 |
| A Das and D Saha | Bengali | Translated SQuAD | 98.51 |

## 10.7 Analysis of Error

From the confusion matrix, it is derived that classification is prevailing the worst-case complexity. Out of 322 questions which were classified rectify the system was able to draw the correct answer or the sentence containing correct answer at some point of iterations.

Difference between fine-grain and coarse-grain accuracy for answer retrieval is due largely on the fact that the answer is contained in one sentence or multiple sentences. If direct answer is available in one sentence system was able to return the exact answer. Otherwise the system returned the sentences containing the answer.

## 10.8 Few Close Observations

- a) Word2Vec helps in improving the performance a lot.
- b) With Word2Vec the system learns and becomes able to give the correct answer of a question which was previously answered incorrectly.
- c) Classification is taking a longer time for the first time as it includes all kind of preprocessing and all. Once the model is built, reclassification is taking much less time. So, system returns the answer much quickly for repeated question; though neither the question nor the answer is saved in the system.
- d) The system performs ideally for factoid question. For the questions which demands descriptive answer the system performance degrades.
- e) For the questions in code-mixed language or having foreign words, the performance degrades graded. The reason is that neither Bengali Wikipedia trained Word2Vec nor Bengali WordNet contains the foreign word or code-mixed word.
