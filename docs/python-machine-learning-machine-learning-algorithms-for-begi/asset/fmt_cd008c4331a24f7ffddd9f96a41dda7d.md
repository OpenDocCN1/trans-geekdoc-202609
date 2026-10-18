
It can be noticed from the output above that there are no zero values in the attribute number 9. However, there are a lot of zero values in the 4, 5, and 6 attributes. This means that our initial assumption about the invalidity of having zero values in these records is true. Since this dataset contains real values about real estates, the best way to deal with the missing values problem is to delete the empty records. Although we will first apply the deletion method, other ways will be applied later on for learning purpose. In general, whenever the deletion method is applied, it is important to pay attention for the amount of records that are sufficient to build a predictive model, and that is why, in some cases, deleting large amounts of data is considered un-preferable solution.

We now need to place “marks” instead of the zero values to indicate that there is a missing value in that specific place. To do that, we can utilize the packages we installed to Python, see Appendix A, to place a `NaN` instead of each zero value. The benefit of this operation is that the `NaN`s are usually ignored by operations on the dataset such as `count` and `sum`. The following code does the process of replacing, using the function: `replace()`. Then, we print the output to check our work. The function: `isnull()` is used to count the number of `NaN`s.

The `numpy` package has been imported in the previous example to be able to use “`isnull()`” and hence be able to count the number of `NaN`s. To check if the zero values have been successfully replaced by `NaN`s, we compare the following output with the previous one, the number of zeros. It can be easily noted that they have the same numbers. The printed-out output is as follows:

Note: Additional investigation can be done by printing a portion of the new marked dataset, for example: the records from 80 to 100, using the command line:

`print(dataset.loc[80:100, [4,5,6,9]])`

This should show that some records have been replaced by `NaN`s, as follows.

## Third: Removing records with missing values

Having a dataset with missing values may limit the ability to apply machine learning algorithms on it and may produce errors. To clarify this problem, before proceeding to the records removal, we apply the Linear Discriminant Analysis (LDA) algorithm on the dataset. The algorithm will not work if the dataset contains missing values. The following code is a Part of a classification step. At the end of the code we check if the LDA algorithm had been applied or not by printing out the values of `X_test` set.

As dictated, because of the missing values, the python platform shows a pop-up message like in the following shot or may show red lines telling you that something was wrong which is preventing the print out process of any output.

The previous code marks the missing values in the dataset, like what had been done before, then it was supposed to calculate the LDA. However, the algorithm failed to work because of the `NaN`s existed in the dataset. Therefore, a method to handle the missing variables has to be applied. At this stage, we apply a removal scheme, which is the simplest way to solve the missing data problem, by eliminating records with missing data.

Utilizing the Pandas packages, we use the `dropna()` function to eliminate records, columns or rows with missing values. This can be done by the following code:

The resulted dataset out of this code has all the records containing `NaN` deleted. Therefore, a very large cut is done. The resulted dataset is of size (814, 12), which has been clearly reduced to be less than the 985 records in the original dataset. However, we can now apply the LDA algorithm to the new reduced dataset, using the code 3 sequence, but adding the command line:

`dataset.dropna(inplace=True)`

before the command: `X =dataset.iloc[:,[4,5,6,9]].values`. This time, the program will print out the first 5 records of `X_test`, as follows:

## Fourth: Imputing Missing Values

The deletion process of records with missing values reduced significantly the size of the dataset. Therefore, other imputing methods may be used to replace the `NaN`/zero values with appropriate values. Some of the common methods to do that, are as follows:

1. A value from another randomly selected record.
2. A constant value which makes sense within the domain.
3. A mean value of the record.
4. A value imported from another model, in which some of its values can be utilized to solve the missing data problem in the current dataset.

In this example, we will replace the missing data with the mean value of each column. The “`fillna`” function, provided by the Panda package, is applied for this task, as in the following code:

The code is then counts the number of the missing data, if there is, after updating the dataset with the mean values. The following there are no more missing values in the dataset.

It is left as exercise for the reader to use the updated dataset, with mean values, in the LDA algorithm code to test for dataset validity.

Good to mention that not all algorithms fail to deal with datasets with missing values. Some algorithms do have the ability to overcome the problem of missing values existence, such as -Nearest Neighbors, which ignores distance measurements for column with missing values. When building a predictive model, classification and Regression consider a missing value as a unique value. In the next chapter, classification using the decision tress and regression algorithms will be discussed in thoroughly.

# 2.3 Data Preparation

In the two previous sections, we talked about the first step in data preparation, which is data scrubbing. However, further preprocessing steps must be applied to the data, before heading to the learning process. In this section we describe briefly the common preparation methods.

# 2.3.1 Data integration

In this process, the data derived from multiple resources, such as different datasets or distributed records, that belongs to a one place is gathered and integrated into one dataset. During the data integration process, some considerations have to be taken into account. For example, in a dataset, we may encounter different attribute values for the same real-world entity. This happens when data are obtained from different sources. The reason may be that every source uses different representation or scale such as: metric vs. British units. Moreover, data sources can sometimes refer to different standards. For instance, some variables can be referred by means of different IDs, in more than one source.

An important problem that may appear during data integration from different sources is the redundant data. The common reasons are:

- The existence of a variable/attribute that is already a derived variable in another dataset, example, when we are talking about annual revenue.
- The same attribute has different names in different datasets.
