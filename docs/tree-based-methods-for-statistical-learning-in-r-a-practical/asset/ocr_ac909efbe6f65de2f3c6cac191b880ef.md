+   - credit.txt (the training data input file in the format required by GUIDE);
+   - credit_desc.txt (the description file).

Below are the contents of the generated credit_desc.txt file. The first line gives the name of the training data file; if the file is not in the current working directory, its full path must be given with quotes (e.g., "some/path/to/credit.txt"). The second line specifies the missing value code (if it contains non-alphanumeric characters, then it too must be quoted). The remaining lines specify the column number, name, and role for each variable in the data input file. As you can imagine, creating this file for a data set with lots of variables can be tedious, hence the reason for writing a helper function.

```
credit.txt
NA
2
1 limit_bal n
2 sex c
3 education c
4 marriage c
5 age n
6 pay_0 n
7 pay_2 n
8 pay_3 n
9 pay_4 n
10 pay_5 n
11 pay_6 n
12 bill_amt1 n
13 bill_amt2 n
14 bill_amt3 n
15 bill_amt4 n
16 bill_amt5 n
17 bill_amt6 n
18 pay_amt1 n
19 pay_amt2 n
20 pay_amt3 n
21 pay_amt4 n
22 pay_amt5 n
23 pay_amt6 n
24 default d
```

With the credit.txt and credit_desc.txt files in hand (and in the appropriate directories required by GUIDE), we can spin up a terminal and call the GUIDE program. I'll omit the details since it's OS-specific, but the GUIDE reference manual will take you through each step. Once the program is called, GUIDE will ask the user for several inputs (e.g., whether to build a classification or regression tree, whether to use constant or non-constant fits, number of folds