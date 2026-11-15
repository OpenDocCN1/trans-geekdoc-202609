

## LLR (\(\lambda=0\))

## RLR (\(\lambda=0\))

## LLR-ridge (\(\lambda=10\))

## SVM (C=1, \(\gamma=1\))

![](img/f3b106d7e76ae3afcec8895afa28732c_390_0.png)

Figure 11.10 LLR, RLR and SVM on the circular data set with mixed outliers.

We see in Figure 11.10 that the LLR (\(\lambda_2 = 0\)) decision boundary is not satisfactory but is somewhat acceptable with LLR-ridge (\(\lambda_2 = 10\)). In contrast, both RLR (\(\lambda_2 = 0\)) and SVM ( C = 1.0, \(\gamma = 1.0\)) carefully capture as many black dots in the center region as possible. This shows that RLR and SVM are superior to LLR-ridge even with optimal regularization. Although not shown, we find that LLR-LASSO regularization (\(\lambda_1 = 20.0\)) will remove \(x_1\) and \(x_2\) and also produce a similar result to LLR-ridge, but neither can compete with the RLR and SVM decision boundaries.

If we now return to Figure 11.10 with the mixed set of outliers, we note that SVM produces an unnecessarily tight boundary as compared to RLR due in part to the new outliers in the central region. SVMs are, in general, not robust to outliers. RLR is superior with the larger boundary and it can provide probabilities, while SVM does not. However, SVM is robust in that it relies on only a few support vectors. The best option for the loan problem is then RLR and we can use the predicted probabilities to make a more informed decision on each loan. But SVM with the RBF kernel does not require extra features to be defined. RLR and LLR both have this limitation but it will be resolved in the next chapter using neural networks.

## 11.6 Example: Titanic Data Set

Now that the concepts and value of rank-based logistic regression have been established, it is an appropriate time to use a larger data set with higher dimensions where outliers are not easily observed but their presence is almost certain. The Titanic data set is well-known in data science circles⁴. It will be used to show that RLR is often superior to both LLR and SVM. It contains information about the passengers who survived, and those who did not, on the ill-fated maiden voyage of the Titanic in April of 1912 that struck an iceberg 400 miles off the coast of Canada. Our goal is to use a training set to learn about a random subset of passengers and their survival rates, and use logistic regression to predict the survivors for a given test set.

We first illustrate basic elements of data science and exploratory data analysis. Then the data set is processed to create the needed X and y for both training and testing purposes. Next, the three approaches to binary classification are compared and contrasted. We note up front that the Titanic data set is expected to have many outliers by its very nature, and this leads us to believe that rank-based methods would be well-suited for this application. The goal of this section is to determine if this conjecture is true.

### 11.6.1 Exploratory Data Analysis

In this section, we carry out rudimentary elements of exploratory data analysis. To begin the analysis, we show the first 10 rows of the Titanic data set in Table 11.6. The first column is the passenger ID for the data set and is only used for bookkeeping. The second column is the binary response indicating whether the passenger survived (1) or not (0). This is used to form the y-vector. The rest of the columns are used to derive the X matrix, with one row for each passenger. The definitions associated with these data columns are given in Table 11.7. The original data set contains much more information but this reduced form is sufficient for our purposes here.

The data set is a mixture of strings, categorical data, and real and integer numbers. This is usually the nature of most data sets. They are a mix of all types of data in different formats. Although the data is already in the form of a data frame for our example, the process of getting the data into this form can be a major undertaking in itself. We ignore that aspect here and assume someone else has done that work. Our task at hand is to convert all of this data into numbers so that it can be used for logistic regression.

4 The Titanic data set is available on the Kaggle site at www.kaggle.com in the Competitions section.

| ID | Survived | Pclass | Name | Sex | Age | SibSp | Parch | Ticket | Fare | Cabin | Embarked |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 1 | 0 | 3 | Braund, Mr. Owen Harris | male | 22.0 | 1 | 0 | A/5 21171 | 7.2500 | NaN | S |
| 2 | 1 | 1 | Cumings, Mrs. John Bradley (Florence Briggs Th...) | female | 38.0 | 1 | 0 | PC 17599 | 71.2833 | C85 | C |
| 3 | 1 | 3 | Heikkinen, Miss. Laina | female | 26.0 | 0 | 1 | 3101282 | 7.9250 | NaN | S |
| 4 | 1 | 1 | Futrelle, Mrs. Jacques Heath (Lily May Peel) | female | 35.0 | 1 | 0 | 113803 | 53.1000 | C123 | S |
| 5 | 0 | 3 | Allen, Mr. William Henry | male | 35.0 | 0 | 0 | 373450 | 8.0500 | NaN | S |
| 6 | 0 | 3 | Moran, Mr. James | male | NaN | 0 | 0 | 330877 | 8.4583 | NaN | Q |
| 7 | 0 | 1 | McCarthy, Mr. Timothy J | male | 54.0 | 0 | 0 | 17463 | 51.8625 | E46 | S |
| 8 | 0 | 3 | Palsson, Master. Gosta Leonard | male | 2.0 | 3 | 1 | 349909 | 21.0750 | NaN | S |
| 9 | 1 | 3 | Johnson, Mrs. Oscar W (Elisabeth Vilhelmina Berg) | female | 27.0 | 0 | 2 | 347742 | 11.1333 | NaN | S |
| 10 | 1 | 2 | Nasser, Mrs. Nicholas (Adele Achem) | female | 14.0 | 1 | 0 | 237736 | 30.0708 | NaN | C |

| Variables | Description | Data type |
|---|---|---|
| Pclass | Passenger class (1, 2, 3) | Categorical |
| Name | Full name of passenger | String |
| Sex | Male or female passenger (0, 1) | Categorical |
| Age | Age of passenger | Real |
| SibSp | Number of siblings/spouse with passenger | Integer |
| Parch | number of parent/children with passenger | Integer |
| Fare | Actual fare paid by passenger | Real |
| Cabin | Cabin number of passenger | String |
| Embarked | Starting point for passenger (S, C, Q) | Categorical |

![](img/f3b106d7e76ae3afcec8895afa28732c_393_0.png)

Figure 11.11 Histogram of passengers: (a) age and (b) fare.

We can now begin to carry out an exploratory data analysis. We will only provide a brief glimpse of this task because there are so many ways to represent and visualize a data set⁵. We note that two columns have real numbers: Age and Fare. These are suitable for visualization using histograms as seen in Figure 11.11. For the Age histogram, one can observe a distribution that is neither Gaussian nor uniform. In fact, it seemingly has a step function followed by an exponential decay as Age increases. The Fare histogram also has a sharp exponential decay characteristic. Both are skewed-right. We would typically investigate which categories of Age and Fare have the most survivors to understand if Age and/or Fare are important features to retain. We skip those details here and keep them both because they may turn out to be important. Further, we will scale Age by 20 and Fare by 50 to bring them in line with other values in the table. More about scaling will be discussed shortly.

5 For a thorough analysis, we refer the reader to the Kaggle site and the detailed explanations therein.

Table 11.8 Number of actual data entries in each column.

| Data columns | Total number of valid entries |
| :--- | :--- |
| Survived | 891 |
| Pclass | 891 |
| Name | 891 |
| Sex | 891 |
| Age | 714 |
| SibSp | 891 |
| Parch | 891 |
| Fare | 891 |
| Cabin | 204 |
| Embarked | 889 |

Subsequently, we could examine the total number of missing elements in each column shown in Table 11.8, noting that there are 891 rows in the Titanic training set. The Cabin and Age columns have a significant number missing entries with a label of NaN or NA, whereas Embarked has only two entries missing. Each case would be handled differently. The relevance of the Cabin number seems to be very limited and many entries are missing so this column can be deleted. As an aside, the Name column seems irrelevant too. It is not clear how a person's name would affect their survival, and any family or sibling/spouse relationships are captured in Parch and SibSp columns. Therefore, the Name column can also be deleted. The missing entries in the Age column pose a real problem because there may be some correlation between Age and Survival. The missing values can be simply replaced with the mean of the ages. A better approach is to compute the mean and standard deviation of the histogram in Figure 11.11(a) and sample Age values from the distribution. This approach was taken in producing the final data set.

Next, we examine the categorical data columns: Sex, Embarked and Pclass. These columns can be cross-tabulated with the Survived column to get a snapshot of the relevance of the data. Consider for example the tabulated data in Table 11.9. It indicates that more females survived than males by a significant margin. If we simply guessed that all female passengers survived and all males did not, we would have 233 + 468 = 701 correct predictions out of 891. That's 78% without using machine learning. Clearly, the Sex of the passenger

