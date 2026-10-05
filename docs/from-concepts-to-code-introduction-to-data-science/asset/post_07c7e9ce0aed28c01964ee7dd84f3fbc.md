
# 11

## Exploratory Data Analysis

One of the first things that should be done with a new dataset is to get a feel for the data. We did some of this during the preprocessing step, when we looked for missing values and extreme observations, and when we transformed variables. Every dataset will be different and might contain surprises; understanding the nuances and the tools to treat them will allow for accurate, insightful analysis.

The two activities we will explore are statistical summarization and visualization of the data. As the datasets grow larger, it can be difficult or impossible to review all of the data points, and this is where statistics will help. Statistical summaries provide a quick overview of the distribution of one or more variables. Aggregations can summarize data along one or more axes, such as computing daily averages on high-frequency data. We will see examples of statistical applications in this chapter.

Properly done graphs will lead you to important features of the data, prompting further investigation. Python includes several modules for visualization, with matplotlib and seaborn the most popular. We will show examples of seaborn to give a sense of its power and ease. Seaborn is based on matplotlib and it provides a high-level interface for attractive and informative statistical graphics. For customizing seaborn, there are times when this book does not allow for a comprehensive treatment of the module, so the examples to follow will serve as a starting point. For an introduction to seaborn, please see [32]. To get started with matplotlib, see [33]. Both of these packages will be pre-installed with Anaconda.

Exploratory data analysis (EDA) can be done on variables individually, but many of the interesting insights we will gain when we consider how one variable changes, or covaries with another. This speaks to the importance of understanding relationships between variables, which is essential for prediction. To drive the point home, consider that each time a variable is selected, data is taken out of context from a large system. If the column of data is a set of midterm grades, the excluded data might be the students who weren't feeling well that day. For a series of stock prices, the underlying economic regime has been left out. In each case, these excluded variables might be essential to truly understanding the data. By thoroughly studying each variable individually and in groups, it will help build a more complete understanding of what insights the data holds.

When we conduct analysis on a single variable, this is often called a univariate analysis. For the study of two variables together, it is called a bivariate analysis. Different statistics and graphs are relevant for each, and they are both necessary for a complete study. In the next two sections, we will conduct EDA on a binary target and a continuous target, respectively. The first exercise will consider a synthetic dataset from a bank where the records represent customer check deposits and the target variable is whether the check was fraudulent or not. The second exercise will study population happiness. These exercises should give a good feel for the data exploration process and methods.

### 11.1 Check Fraud

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

```python
df = pd.read_csv('../datasets/check_deposit_fraud.csv')
df.head(3)
```

| checkkid | check_amount | check_signed | is_fraud |
| :--- | :--- | :--- | :--- |
| 0 | 9076.51 | 1 | 0 |
| 1 | 2148.38 | 1 | 0 |
| 2 | 604.52 | 1 | 0 |

We can see the schema of the data by issuing:

```python
df.info()
```

| Column | Non-Null Count | Dtype |
| :--- | :--- | :--- |
| 0 | checkid | 1100 non-null | int64 |
| 1 | check_amount | 1100 non-null | float64 |
| 2 | check_signed | 1100 non-null | int64 |
| 3 | is_fraud | 1100 non-null | int64 |

A real-world dataset would include additional attributes like bank name, account, routing number, check, and so on. Here, attention is drawn to a sample of interesting attributes, as they have exhibited historical predictive ability. For the binary variable `check_signed` and the target variable `is_fraud`, we should compute the frequency and percentage of each value. We count the number of fraudulent and non-fraudulent checks with the

```python
df.is_fraud.value_counts()
0    1096
1    4
```

The rows are ordered from highest number of observations to lowest. In this case, there are 1096 rows where `is_fraud` is 0 (no fraud; the negative label), and 4 rows where `is_fraud` is 1 (fraud; the positive label). Including the parameter normalize=True will compute their percentages:

```python
df.is_fraud.value_counts(normalize=True)
0    0.996364
1    0.003636
```

Over 99% of the checks are legitimate; fraud is fairly rare.
We follow the same procedure for check_signed:

```python
df.check_signed.value_counts()
1    1096
0    4
```

```python
df.check_signed.value_counts(normalize=True)
1    0.996364
0    0.003636
```

Most of the checks are signed.
