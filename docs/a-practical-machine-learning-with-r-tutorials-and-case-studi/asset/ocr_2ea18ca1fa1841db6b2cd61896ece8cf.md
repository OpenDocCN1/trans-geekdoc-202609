26 Introduction to R and RStudio

The content of Figure 3.2 was created with view(dataTitanic). The view() command can only be used in the Console of RStudio. It is a very useful command as it displays a complete scrollable view of a data frame.

Figure 3.2 reflects what you learned about data frames:

+   - The first row contains the names of variables that are related to the observations (passengers).

The variable Name is a character variable, Sex is a categorical variable (with categories male and female).6 All other variables are numerical variables.7

+   - The observations (here: the first passengers) are in the rows (starting with Row 2).

We can extract the Age variable as an R vector object and then use the mean to calculate the average age of the Titanic passengers:

```
VecAge=DataTitanic$Age
mean(VecAge)
```

## [1] 29.47

In the last line of the code block, we did not assign the output of the mean() command to an R object. Output not assigned to any object will be outputted to the Console. As you can see, the average age of Titanic passengers is 29.47.

You can also find how many passengers are considered in the data frame Titanic, as this coincides with the number of rows (observations) of Titanic. You can apply the length() command to any vector from the data frame to find the number of rows, as follows:

```
cat("Number of observations-", length(DataTitanic$Name))
```

## Number of observations: 887

You cannot apply the length() command directly to a data frame, but you can find the number of rows (the number of observations) directly from a data frame with:

> Note that R assigned the data type char and not factor to the variable Sex. This is because R considers Sex a categorical variable. However, a user can use the command as factor() from the tidyverse package to convert Sex to a factor.

> As the original Titanic data is stored as a numerical variable with 1 for a surviving passenger and 0 otherwise. It would have been better coding practice to storeSurvived as a logical variable with values TRUE and FALSE (Section 3.5.1).