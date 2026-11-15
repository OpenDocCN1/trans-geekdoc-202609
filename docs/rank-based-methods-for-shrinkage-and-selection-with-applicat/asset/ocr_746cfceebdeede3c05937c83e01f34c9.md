# Table 11.8 Number of actual data entries in each column.

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

we will scale Age by 20 and Fare by 50 to bring them in line with other values in the table. More about scaling will be discussed shortly.

Subsequently, we could examine the total number of missing elements in each column shown in Table 11.8, noting that there are 891 rows in the Titanic training set. The Cabin and Age columns have a significant number missing entries with a label of NaN or NA, whereas Embarked has only two entries missing. Each case would be handled differently. The relevance of the Cabin number seems to be very limited and many entries are missing so this column can be deleted. As an aside, the Name column seems irrelevant too. It is not clear how a person's name would affect their survival, and any family or sibling/spouse relationships are captured in Parch and SibSp columns. Therefore, the Name column can also be deleted. The missing entries in the Age column pose a real problem because there may be some correlation between Age and Survival. The missing values can be simply replaced with the mean of the ages. A better approach is to compute the mean and standard deviation of the histogram in Figure 11.11(a) and sample Age values from the distribution. This approach was taken in producing the final data set.

Next, we examine the categorical data columns: Sex, Embarked and Pclass. These columns can be cross-tabulated with the Survived column to get a snapshot of the relevance of the data. Consider for example the tabulated data in Table 11.9. It indicates that more females survived than males by a significant margin. If we simply guessed that all female passengers survived and all males did not, we would have 233 + 468 = 701 correct predictions out of 891. That's 78% without using machine learning. Clearly, the Sex of the passenger