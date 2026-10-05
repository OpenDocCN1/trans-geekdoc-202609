studying each variable individually and in groups, it will help build a more complete understanding of what insights the data holds.

When we conduct analysis on a single variable, this is often called a univariate analysis. For the study of two variables together, it is called a bivariate analysis. Different statistics and graphs are relevant for each, and they are both necessary for a complete study. In the next two sections, we will conduct EDA on a binary target and a continuous target, respectively. The first exercise will consider a synthetic dataset from a bank where the records represent customer check deposits and the target variable is whether the check was fraudulent or not. The second exercise will study population happiness. These exercises should give a good feel for the data exploration process and methods.

# 11.1 Check Fraud

In this section, we will study a problem faced by banks offering checking accounts to their customers. Check fraud is typically rare, but the total losses can be sizeable and there is great motivation to detect bad checks.

The synthetic dataset for this analysis lives in the course repo here:

```
semester1/datasets/check_deposit_fraud.csv
```

A Jupyter notebook with code performing EDA lives here:

```
semester1/week_11_12_visualize_summarize/check_deposit_eda.ipynb
```

We import the data and show the first few rows:

```
df = pd.read_csv('../datasets/check_deposit_fraud.csv')
df.head(3)
```

| checkkid | check_amount | check_signed | is_fraud |
| 0 | 9076.51 | 1 | 0 |
| 1 | 2148.38 | 1 | 0 |
| 2 | 604.52 | 1 | 0 |

We can see the schema of the data by issuing:

```
df.info()
```