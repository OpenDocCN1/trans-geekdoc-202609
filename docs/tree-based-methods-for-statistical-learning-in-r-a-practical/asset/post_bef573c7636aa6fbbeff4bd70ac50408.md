
- age: The customer's age in years.
- pay_0, pay_2-pay_6: History of past payment; pay_0 = the repayment status in September, 2005; pay_2 = the repayment status in August, 2005; ...; pay_6 = the repayment status in April, 2005. The measurement scale for the repayment status is: -1 = pay duly; 1 = payment delay for one month; 2 = payment delay for two months; ...; 8 = payment delay for eight months; 9 = payment delay for nine months and above.
- bill_amt1-bill_amt6: Amount of bill statement (NT dollar). bill_amt1 = amount of bill statement in September, 2005; bill_amt2 = amount of bill statement in August, 2005; ...; bill_amt6 = amount of bill statement in April, 2005.
- pay_amt1-pay_amt6: Amount of previous payment (NT dollar). pay_amt1 = amount paid in September, 2005; pay_amt2 = amount paid in August, 2005; ...; pay_amt6 = amount paid in April, 2005.

The goal is to build a model to predict the probability of a customer defaulting on their credit card payment. For that I'll build a GUIDE classification tree. The R code I used to download and clean the data is shown below. To start, I download the data into a temporary file before reading in the resulting XLS file (i.e., Microsoft Excel spreadsheet) using the readxl package [Wickham and Bryan, 2019] and printing a compact summary of the data using str():

```
# Download and read in the credit default data from the UCI ML repo
tf <- tempfile(fileext = ".xls")
url <- paste0("https://archive.ics.uci.edu/ml/", # sigh, long URLs...
              "machine-learning-databases/",
              "00350/default%20of%20credit%20card%20default%20clients.xls")
download.file(url, destfile = tf)
credit <- as.data.frame(readxl::read_xls(tf, skip = 1))

# Clean up column names a bit
names(credit) <- tolower(names(credit))
names(credit)[names(credit) == "default payment next month"] <-
  "default"

str(credit) # compactly display structure of the data frame
#> 'data.frame': 30000 obs. of 25 variables:
#>  $ id       : num 1 2 3 4 5 6 7 8 9 10 ...
#>  $ limit_bal: num 20000 120000 90000 50000 50000 50000 500 ...
#>  $ sex      : num 2 2 2 1 1 1 2 2 1 ...
#>  $ education: num 2 2 2 2 1 1 2 3 3 ...
#>  $ marriage : num 1 2 2 1 1 2 2 2 1 2 ...
#>  $ age      : num 24 26 34 37 57 37 29 23 28 35 ...
#>  $ pay_0    : num -1 -1 0 -1 0 0 0 -2 -2 ...
#>  $ pay_2    : num 2 2 0 0 0 0 -1 0 -2 ...
#>  $ pay_3    : num -1 0 0 0 -1 0 0 -1 2 -2 ...
#> $ pay_4  : num -1 0 0 0 0 0 0 0 -2 ...
#> $ pay_5  : num -2 0 0 0 0 0 0 0 -1 ...
#> $ pay_6  : num -2 0 0 0 0 0 0 0 -1 ...
#> $ bill_amt1 : num 3913 2682 29239 46990 8617 ...
#> $ bill_amt2: num 3102 1725 14027 48233 5670 ...
#> $ bill_amt3: num 689 2682 13559 49291 35835 ...
#> $ bill_amt4: num 0 3272 14331 28314 20940 ...
#> $ bill_amt5: num 0 3455 14948 28959 19146 ...
#> $ bill_amt6: num 0 3261 15549 29547 19131 ...
#> $ pay_amt1 : num 0 0 1518 2000 2000 ...
#> $ pay_amt2 : num 689 1000 1500 2019 36681 ...
#> $ pay_amt3 : num 0 1000 1000 1200 10000 657 38000 0 ...
#> $ pay_amt4 : num 0 1000 1000 1100 9000 ...
#> $ pay_amt5 : num 0 0 1000 1069 689 ...
#> $ pay_amt6 : num 0 2000 5000 1000 679 ...
#> $ default : num 1 1 0 0 0 0 0 0 0 ...
```

Note that the categorical variables have been numerically re-encoded. The next code chunk removes the column ID and cleans up some of the categorical features by re-encoding them from numeric back to the actual categories based on the provided column descriptions:

```
# Remove ID column
credit$id <- NULL

# Clean up categorical features
credit$sex <- ifelse(credit$sex == 1, yes = "male", no = "female")
credit$education <- ifelse(
  test = credit$education == 1,
  yes = "graduate school",
  no = ifelse(
    test = credit$education == 2,
    yes = "university",
    no = ifelse(
      test = credit$education == 3,
      yes = "high school",
      no = "other"
    )
  )
)

credit$marriage <- ifelse(
  test = credit$marriage == 1,
  yes = "married",
  no = ifelse (
    test = credit$marriage == 2,
    yes = "single",
    no = "other"
  )
)

credit$default <- ifelse(credit$default == 1, yes = "yes", no = "no")

# Coerce character columns to factors
for (i in seq_len(ncol(credit))) {
  if (is.character(credit[[i]])) {
    credit[[i]] <- as.factor(credit[[i]])
  }
}
```

Finally, I'll split the data into train/test sets using a 70/30 split, leaving 21,000 observations for training and 9,000 for estimating the generalization performance:

```
set.seed(1342) # for reproducibility
trn.ids <- sample(nrow(credit), size = 0.7 * nrow(credit),
                  replace = FALSE)
credit.trn <- credit[trn.ids, ]
credit.tst <- credit[-trn.ids, ]
```

The GUIDE program requires two special text files before it can be called:

- the data input file;
- a description file.

See the GUIDE reference manual [Loh, 2020] for full details. The data input file is essentially just a text file containing the training data in a format that can be consumed by GUIDE. The description file provides some basic metadata, like the missing value flag and variable roles. These files can be a pain to generate, especially for data sets with lots of columns, so I included a little helper function in **treemisc** to help generate them; see `?treemisc::guide_setup` for argument details.

Below is the code I used to generate the data input and description files for the credit card default example. By default, numeric columns are used both for splitting the nodes and for fitting the node regression models for non-constant fits, and categorical variables are used for splitting only. In my setup, I have a /guide-v38.0/credit directory containing the GUIDE executable and where the generated files will be written to:

```
treemisc::guide_setup(credit.trn, path = "guide-v38.0/credit",
                  dv = "default", file.name = "credit",
                  verbose = TRUE)
```

```
#> Writing data file to guide-v38.0/credit/credit.txt...
#> Writing description file to guide-v38.0/credit/credit_desc.txt...
```

This resulted in the creation of two files in /guide-v38.0/credit (my directory for this example):

- credit.txt (the training data input file in the format required by GUIDE);
- credit_desc.txt (the description file).

Below are the contents of the generated credit_desc.txt file. The first line gives the name of the training data file; if the file is not in the current working directory, its full path must be given with quotes (e.g., "some/path/to/credit.txt"). The second line specifies the missing value code (if it contains non-alphanumeric characters, then it too must be quoted). The remaining lines specify the column number, name, and role for each variable in the data input file. As you can imagine, creating this file for a data set with lots of variables can be tedious, hence the reason for writing a helper function.

credit.txt  
NA  
2  

| 列号 | 变量名 | 角色 |
|:---:|:---|:---|
| 1 | limit_bal | n |
| 2 | sex | c |
| 3 | education | c |
| 4 | marriage | c |
| 5 | age | n |
| 6 | pay_0 | n |
| 7 | pay_2 | n |
| 8 | pay_3 | n |
| 9 | pay_4 | n |
| 10 | pay_5 | n |
| 11 | pay_6 | n |
| 12 | bill_amt1 | n |
| 13 | bill_amt2 | n |
| 14 | bill_amt3 | n |
| 15 | bill_amt4 | n |
| 16 | bill_amt5 | n |
| 17 | bill_amt6 | n |
| 18 | pay_amt1 | n |
| 19 | pay_amt2 | n |
| 20 | pay_amt3 | n |
| 21 | pay_amt4 | n |
| 22 | pay_amt5 | n |
| 23 | pay_amt6 | n |
| 24 | default | d |

With the credit.txt and credit_desc.txt files in hand (and in the appropriate directories required by GUIDE), we can spin up a terminal and call the GUIDE program. I'll omit the details since it's OS-specific, but the GUIDE reference manual will take you through each step. Once the program is called, GUIDE will ask the user for several inputs (e.g., whether to build a classification or regression tree, whether to use constant or non-constant fits, number of folds to use for cross-validation, etc.). In the end, GUIDE generates a special input text file to be consumed by the software.

Below are the contents of the input file for the credit card default example, called credit_in.txt, highlighting all the options I selected (I basically requested a default classification tree that's been pruned using the 1-SE rule with 10-fold cross-validation, but you can see several of the available options in the output).

```
GUIDE (do not edit this file unless you know what you are doing)
38.0 (version of GUIDE that generated this file)
1 (1=model fitting, 2=importance or DIF scoring, 3=data con...
"credit_out.txt" (name of output file)
1 (1=one tree, 2=ensemble)
1 (1=classification, 2=regression, 3=propensity score group...
1 (1=simple model, 2=nearest-neighbor, 3=kernel)
2 (0=linear 1st, 1=univariate 1st, 2=skip linear, 3=skip li...
1 (0=tree with fixed no. of nodes, 1=prune by CV, 2=by test...
"credit_desc.txt" (name of data description file)
10 (number of cross-validations)
1 (1=mean-based CV tree, 2=median-based CV tree)
1.000 (SE number for pruning)
1 (1=estimated priors, 2=equal priors, 3=other priors)
1 (1=unit misclassification costs, 2=other)
2 (1=split point from quantiles, 2=use exhaustive search)
1 (1=default max. number of split levels, 2=specify no. in ...
1 (1=default min. node size, 2=specify min. value in next l...
2 (0=no LaTeX code, 1=tree without node numbers, 2=tree wit...
"credit.tex" (latex file name)
1 (1=color terminal nodes, 2=no colors)
2 (0=#errors, 1=sample sizes, 2=sample proportions, 3=poste...
3 (1=no storage, 2=store fit and split variables, 3=store s...
"credit_splits.txt" (split variable file name)
2 (1=do not save fitted values and node IDs, 2=save in a file)
"credit_fitted.txt" (file name for fitted values and node IDs)
2 (1=do not write R function, 2=write R function)
"credit_pred.R" (R code file)
1 (rank of top variable to split root node)
```

Now, all you have to do is feed this input file back into the GUIDE program (again, see the official manual for details). Once the modeling process is complete, you'll end up with several files depending on the options you specified during the initial setup. A portion of the output file produced by GUIDE for my input file is shown below; the corresponding tree diagram is displayed in Figure 4.7.

```
Node 1: Intermediate node
A case goes into Node 2 if pay_0 <= 1.5000000
pay_0 mean = -0.15095238E-01
```
