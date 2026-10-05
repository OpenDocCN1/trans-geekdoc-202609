
# Soft Computing and Machine Learning with Python

- 33. R. S. Michalski, T. J. (1983). Learning from Observation: Conceptual Clustering. TIOGA Publishing Co.
- 34. Rajesh P. N. Rao, B. A. (2002). Probabilistic Models of the Brain. MIT Press.
- 35. Rashevsky, N. (1948). Mathematical Biophysics: Physico-Mathematical Foundations of Biology. Chicago: Univ. of Chicago Press.
- 36. Richard O. Duda, P. E. (2000). Pattern Classification (2nd Edition ed.).
- 37. Richard S. Sutton, A. G. (1998). Reinforcement Learning. MIT Press.
- 38. Ripley, B. (1996). Pattern Recognition and Neural Networks. Cambridge University Press.
- 39. Rosenblatt, F. (1958). The perceptron: a probabilistic model for information storage and organization in the brain. Psychological Review, 65 (6), 386-408.
- 40. Russell, S. J. (2003). Artificial Intelligence: A Modern Approach (2nd Edition ed.). Upper River, NJ, NJ, USA: Prentice Hall.
- 41. Ryszard S. Michalski, J. G. (1955). Machine Learning: An Artificial Intelligence Approach (Volume I). Morgan Kaufmann
- 42. Ryszard S. Michalski, J. G. (1955). Machine Learning: An Artificial Intelligence Approach.
- 43. Selfridge, O. G. (1959). Pandemonium: a paradigm for learning. The mechanisation of thought processes. H.M.S.O., London. London.
- 44. Sleeman, D. H. (1983). Inferring Student Models for Intelligent CAI. Machine Learning. Tioga Press, s: ACM Press.
- 45. Timothy Jason Shepard, P. J. (1998). Decision Fusion Using a Multi-Linear Classifier. In Proceedings of the International Conference on Multisensor-Information Fusion.
- 46. Tom, M. (1997). Machine Learning. Machine Learning, Tom Mitchell, 1997: McGraw Hill.
- 47. Trevor Hastie, R. T. (2001). The Elements of Statistical Learning. New York, NY, USA: Springer Science and Business Media.
- 48. Widrow, B. W. (2007). Adaptive Inverse Control: a Signal Processing Approach. Wiley-IEEE Press.
- 49. Y. Chali, S. R. (2009). Complex Question Answering: Unsupervised Learning Approaches and Experiments. Journal of Artificial Intelligent Research, 1–47.
- 50. Yu, L. L. (2004, October). Efficient feature Selection via Analysis of Relevance and Redundancy. JMLR, 1205-1224.
- 51. Zhang, S. Z. (2002). Data Preparation for Data Mining. Applied Artificial Intelligence. 17, 375-381.

# CHAPTER 3
# DATA MINING WITH SKEWED DATA

Manoel Fernando Alonso Gadi¹, Alair Pereira do Lago², and Jorn Meinenen³

¹Milton Keynes United Kingdom
²Depart. de Ciencia de Computacao, Inst. de Matematica e Estatistica Universidade de Sao Paulo Brazil
³Decision Engineering Centre, Cranfield University Cranfield, Bedfordshire MK43 0AL United Kingdom

In this chapter, we explore difficulties one often encounters when applying machine learning techniques to real-world data, which frequently show skewness properties. A typical example from industry where skewed data is intrinsic problem is fraud detection in finance data. In the following we provide examples, where appropriate, to facilitate the understanding of data mining of skewed data. The topics explored include but not limited to: data preparation, data cleansing, missing values, characteristics construction, variable selection, data skewness, objective functions, bottom line expected prediction, limited resource situation, parametric optimisation, model robustness and model stability.

Citation: Manoel Fernando Alonso Gadi, Alair Pereira do Lago and Jorn Mehnen (February 2010). “Data Mining with Skewed Data”, New Advances in Machine Learning, Yang Zhang, IntechOpen, DOI: 10.5772/9382.

Copyright: © 2010 by authors and Intech. This paper is an open access article distributed under a Creative Commons Attribution 3.0 License

# INTRODUCTION

In many contexts like in a new e-commerce website, fraud experts start investigation procedures only after a user makes a claim. Rather than working reactively, it would be better for the fraud expert to act proactively before a fraud takes place. In this e-commerce example, we are interested in classifying sellers into local customers or fraudsters. If a seller is involved in a fraudulent transaction, his/her license to sell can be revoked by the e-business. Such a decision requires a degree of certainty, which comes with experience. In general, it is only after a fraud detection expert has dealt with enough complaints and enough data that he/she acquired a global understanding of the fraud problem. Quite often, he/she is exposed to a high number of cases in a short period.

# DATA PREPARATION

## Characteristics Extraction

One of the most important tasks on data preparation is the conception of characteristics. Unfortunately, this depends very much on the application (See also the discussions in 4 and 5). For fraud modelling for instance, one starts from determine significant indicators. The design of characteristics to be used in a model is called characteristics extraction or feature extraction.

In this evaluation, one is interested in measuring how well these characteristics:
- covers (is present in) the true fraud cases;
- and how clearly they discriminate fraud from non-fraud.

In order to cover as many fraud cases as possible, one may verify how many of them are covered by characteristics set. The discrimination power of any of these characteristics can be evaluated by their odds ratio. If the probability of the event (new characteristics) in each of two classes (fraud and non-fraud in our case) are $p_f$ (first class) and $p_n$ (second class), then the odds ratio

$OR = \frac{p_f/(1-p_f)}{p_n/(1-p_n)} = \frac{p_f(1-p_n)}{p_n(1-p_f)}$

An odds ratio equal to 1 describes the characteristics as equally probable in both classes (fraud and non-fraud). The more this ratio is greater/less than 1, the more likely this characteristic is in the first/second class than in the other one.

# Data Cleansing

In many manuals on best practice in model development, a chapter on data consistency checks, or data cleansing, is present. The main reason for this is to avoid wasting the effort applied in the model development stage, because of data inconsistency invalidating the dataset in use.

Here we understand data consistency checks as being a set of expert rules to which expert rules can be based on expert knowledge or common sense. For example, a common error when filling the date-of-birth section in a credit card application form is to put the current year instead of the year the person was actually born. In many countries under sixteen years old can not have a credit card. Therefore, an easy way of checking this inconsistency is to simply calculate the applicant's age and if it falls within a valid range. With more information available, more complex checks can be applied, such as, e.g. matching name with gender or street name with post code.
