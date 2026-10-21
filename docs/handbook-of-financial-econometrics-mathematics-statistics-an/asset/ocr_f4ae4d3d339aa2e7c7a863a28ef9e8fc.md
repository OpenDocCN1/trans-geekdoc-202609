The response variable is

+   - $Y$: Default payment next month (1 = default; 0 = not default).

We use the following 23 variables as explanatory variables:

+   - $X_1$: Amount of the given credit (NT dollar),
+   - $X_2$: Gender (1 = male, 2 = female),
+   - $X_3$: Education (1 = graduate school; 2= university; 3 = high school; 4 = others),
+   - $X_4$: Marital status (1 = married; 2 = single; 3 = others),
+   - $X_5$: Age (year),
+   - $X_6$–$X_{11}$: History of past monthly payment traced back from September, 2005 to April, 2005 (–1 = pay duly; 1 = payment delay for one month; 2 = payment delay for two months; …; 8 = payment delay for eight months; 9 = payment delay for nine months and above),
+   - $X_{12}$–$X_{17}$: Amount of past monthly bill statement (NT dollar) traced back from September, 2005 to April, 2005.
+   - $X_{18}$–$X_{23}$: Amount of past payment (NT dollar) traced back from September, 2005 to April, 2005.

This data set is interesting because it contains two “sorts” of attributes. The first sort is about categorical attributes like education, marital status, and age. These attributes have a very small range of possible values, and if there was a high correlation between these categorical attributes then the classification algorithms would be able to easily identify them and produce high accuracies. The second sort of attribute is the past payment information. These attributes are just integers without clear differentiation of categories and have much larger possible ranges of how much money was paid. Especially, if there was not strong correlation between education, marital status, age, etc. and defaulting on payments, it could be more difficult to algorithmically predict the outcome from past payment details, except for the extremes where someone never pays their bills or always pays their bills.

Figure 101.1 plots the heatmap to show pairwise correlations between attributes. It is shown that most correlations are about zeros, but high correlations exist in features of past monthly payments ($X_6$, …, $X_{11}$) and past monthly bill statements ($X_{12}$, …, $X_{17}$).

# 101.3 Machine Learning

Let $X = (X_1, …, X_p)'$ denote the $p$-dimensional input vector, and let $Y = (Y_1, …, Y_d)'$ denote the $d$-dimensional output vector. In its simplest form,