# 3.5 How R Stores Data AND and OR

**TABLE 3.1** Truth-Table for AND and OR

| R object | R object | A and B | A or B |
| A | B | A&B | A|B |
| TRUE | TRUE | TRUE | TRUE |
| TRUE | FALSE | FALSE | TRUE |
| FALSE | TRUE | FALSE | TRUE |
| FALSE | FALSE | FALSE | FALSE |

We could also store variables that are either TRUE or FALSE variables, such as for 1 for TRUE and 0 for FALSE. Although this is done more often in data science research, it is not best practice to do so.

# Factor Data Type (factor):

A factor is an R data type that stores categorical data in an effective way. To understand what a factor is, we must first understand what categorical data are. For instance, first or last names are not categorical data because there are a vast number of first or last names. As explained before, because they are stored as character data,

In contrast, categorical data usually has only a (very) limited amount of variations. For example, the R object MarriageStatus can be limited to "Never Married", "Married", "Widowed", or "Divorced". Because only a limited number of categories are available (four categories in the example), we can call MarriageStatus an R object that stores categorical data.

Although categorical data can be stored as character data, it is more efficient to store categorical data as a factor. R will internally assign 1 for "Never Married", 2 for "Married", 3 for "Widowed", and 4 for "Divorced" (1, 2, 3, and 4 are called levels in R). Next, R will internally store the coding of the level and save the actual data as 1, 2, 3, and 4. This will save memory "1" takes less than "Never Married", 2 less than "Married", and so forth. The R user needs not to be bothered about it.

There are other reasons to use the factor data type besides memory. The main reason is that a factor data type signals R that the R stores categorical data, which often require special treatment. This will become important later when we work with classification problems in machine learning algorithms. These algorithms usually require a factor as an outcome variable.

# 3.5.2 R Object Types

Now that we know the Data Types of R, we can start exploring how these Data Types are stored in various R objects. The list of possible object