
In the next chapter, we will understand the specifics of backtesting and forward testing and how they play a vital role in algorithmic trading. As we progress, we will understand more about how to select, process, and use different types of data effectively, enabling you to build more robust and potentially profitable trading strategies.

***

**Join our book's Discord space**

Join the book's Discord Workspace for Latest updates, Offers, Tech happenings around the world, New Release and Sessions with the Authors:

[https://discord.bpbonline.com](https://discord.bpbonline.com)

![](images/Discord.png)

# Chapter 3: Optimizing Trading Systems, Metrics, and Automated Reporting

## Introduction

This chapter focuses on optimizing trading systems for maximum performance. By leveraging advanced tools like `Hyperopt`, traders can enhance their strategies, experiment with new approaches, and uncover valuable insights to improve their models.

The selection of metrics plays a critical role, guiding traders in making well-informed decisions. Effective risk management and thoughtful metric selection are essential for evaluating models thoroughly and achieving long-term success.

Additionally, automated reporting, made efficient through Python libraries, enables the transformation of trading data into actionable insights.

## Structure

In this chapter, we will cover the following topics:

- [Designing a trading system](#chap03.xhtml#h11)
- [Improving trading systems](#chap03.xhtml#h12)
- [Selecting metrics for trading systems](#chap03.xhtml#h13)
- [Automated trading reports](#chap03.xhtml#h14)

## Objectives

Our primary focus is on designing and refining an algorithmic trading strategy. Our journey starts with selecting a classifier responsible for adeptly predicting future returns.

This chapter aims to establish a solid foundation for the trading system by leveraging the classifier's capabilities, optimizing hyperparameters to enhance the strategy's robustness, analyzing the strategy's performance using detailed risk and performance metrics, and presenting the findings through industry-standard reporting tools.

## Designing a trading system

This chapter will focus on the algorithm tailored to classify future bars. Our journey will encapsulate the entire process, from data inception to the final reporting of a learned and evaluated model characterized by its performance and risk metrics.

The roadmap includes the following:

- Preparing data
- Undertaking feature engineering
- Training with an ensemble of competitive models
- Gauging the model through performance and risk metrics
- Comprehensive reporting

### Preparing data

A word on the analysis data. We have chosen to ground our investigations using the Microsoft (`MSFT` ticker) data, recorded at 5-day intervals, amassing a total of 5000 days. The 5-day interval separating the quotes allows us to explore a weekly time horizon. The feed comes from the Yahoo! Finance library, which we have used many times.

The following graph shows this data:

![](images/fig-3-1.png)

#### Undertaking feature engineering

In this process, we execute two key operations sequentially:

- `create_lag_past_values()`: This function augments the dataframe with lagged price values from preceding periods. For every price column (OHLC), a new column with these lagged values is added. The naming convention for these new columns involves appending a suffix, indicating the lag period, to the original column name. For instance, `_1` indicates a lag of one period, `_2` denotes two periods, and so on[1](#chap03.xhtml#footnote-143).
- `return_past_values()`: This function transforms all price data into consecutive returns. For each of the price columns, a corresponding return column is introduced. These new columns are aptly named by appending the suffix `_ret` to the original column name.

Together, these operations, incorporating lagged values and calculating returns, constitute our feature engineering step. This prepares the patterns that our analysis algorithms will utilize to predict future returns. We will learn more about this crucial stage in [Chapter 6](#chap06.xhtml), Improving Model Capability with Features, which is entirely devoted to feature engineering.

#### Feature correlation

In the field of algorithmic trading, understanding feature correlation is essential. Correlated features can introduce redundancy into the data, leading to overfitting and reducing the ability of the model to generalize.

When algorithms encounter features that echo similar information, they can assign excessive importance to those intertwined features, skewing results. This is particularly vital for linear models like linear regression and tree-based algorithms like decision trees and random forests, where correlated features can result in biased or inflated feature importance. To ensure robustness and maintain the integrity of the model's predictive power, it's essential to identify and eliminate highly correlated features, thereby streamlining the input and enhancing model efficiency.

#### Detecting and eliminating correlated features

Traditional Pearson correlation provides insight into linear relationships but may miss non-linear associations. Enter Spearman's rank correlation, which identifies monotonic relationships, and mutual information, capturing both linear and non-linear dependencies. These alternatives are critical because real-world financial data often exhibits non-linear behavior. Scikit-learn offers tools like `VarianceThreshold` and `SelectKBest` for feature selection, and the `correlation_matrix` for visual examination. Additionally, libraries like `feature-engine`[2](#chap03.xhtml#footnote-142) provide advanced techniques for handling correlated variables. Embracing these strategies and diversifying correlation metrics ensures that your model is receiving the most informative, non-redundant inputs, optimizing its predictive potential.

The following code displays the correlation matrix before the phase of eliminating correlated features:

```python
import seaborn as sns

# Calculate the correlation matrix for the features
correlation_matrix = df_lag.corr()

# Create a mask for the upper triangle of the correlation matrix
mask = np.triu(np.ones_like(correlation_matrix, dtype=bool))

# Plot the correlation matrix
plt.figure(figsize=(15, 10))
sns.heatmap(correlation_matrix, mask=mask, cmap='coolwarm', vmax=1, vmin=-1, center=0, annot=False, fmt=".2f")
plt.title('Correlation Matrix of Features')
plt.show()
```

![](images/fig-3-2.png)

The correlation matrix highlights relationships between features in the dataset, with a red gradient indicating strong positive correlations. Features that are highly correlated, as indicated by the red regions, provide redundant information. These highly correlated variables are removed to reduce multicollinearity and improve the interpretability and efficiency of the model.

Let us continue with the pruning algorithm, which consists of eliminating features whose correlation exceeds the admissible value (threshold of 0.9):

```python
# Identify features that are highly correlated
to_drop = []

for i in range(len(correlation_matrix.columns)):
    for j in range(i):
        if abs(correlation_matrix.iloc[i, j]) > 0.9:
            colname = correlation_matrix.columns[i]
            if colname not in to_drop and not colname.endswith('_ret'):
                to_drop.append(colname)

# Drop the highly correlated features
df_lag.drop(columns=to_drop, inplace=True)
```

The effect of pruning is checked using the matrix of correlated features as previously discussed. Even if there are still traces of correlation, we can see in the following graph that the remaining correlations are much more acceptable than those observed previously:

![](images/fig-3-3.png)

#### Missing values and target column

With a modern, powerful library such as Pandas, dealing with missing values becomes a quick and easy formality.
