# 8.3 COUNTERFACTUAL EXPLANATIONS

![](bbox=[0.198, 0.126, 0.833, 0.386])

From the two resulting groups, one with parents and one with children, we only want the best using two sorting algorithms. The nondominated sorting algorithm sorts the candidates according to their objective values. If candidates are equally good, the crowd distance sorting algorithm sorts the candidates according to their diversity.

Given the ranking of the two sorting algorithms, we select the most promising and/or diverse half of the candidates. We use this set for the next generation and start again with the selection, recombination and mutation process. By repeating the steps over and over we happily approach a diverse set of promising candidates with low objective values. From this we can choose those with which we are most satisfied, or we can give a summary of all counterfactuals by highlighting which and how features have been changed.

# 8.3.2 Example

The following example is based on the credit dataset example in Dandl et al. (2020). The German Credit Risk dataset can be found on the machine learning challenges platform kaggle.com¹⁵.

The authors trained a support vector machine (with radial basis kernel) to predict the probability that a customer has a good credit risk. The corresponding dataset has 522 complete observations and nine features containing credit and customer information.

The goal is to find counterfactual explanations for a customer with the following values:

> ¹⁵https://www.kaggle.com/uciml/german-credit