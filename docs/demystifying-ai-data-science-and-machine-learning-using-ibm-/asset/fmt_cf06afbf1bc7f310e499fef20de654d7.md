
| LogAccess || 1 || 666 || 78.063 || 203.542 || 2.549 || 4.529 || 506 |
| LogAccess_LogN || 0 || 6.501 || 2.222 || 1.659 || 1.675 || 1.989 || 506 |
| LogDistance || 1.13 || 24 || 6.173 || 6.476 || 2.143 || 3.261 || 506 |
| LogDistance_LogN || 0.122 || 3.178 || 1.472 || 0.763 || 0.877 || 0.229 || 506 |
| Lstat || 1.73 || 34.41 || 11.538 || 6.065 || 0.898 || 0.65 || 506 |
| Lstat_Square root || 1.315 || 5.866 || 3.281 || 0.879 || 0.288 || −0.36 || 506 |
| NiOxSQ || 0.385 || 7.313 || 1.101 || 1.647 || 2.647 || 5.285 || 506 |
| NiOxSQ_Inverse || 0.137 || 2.597 || 1.736 || 0.637 || −1.344 || 1.181 || 506 |
| PtRatio || 2.6 || 396.9 || 42.615 || 87.585 || 3.526 || 10.818 || 506 |
| PtRatio_LogN || 0.956 || 5.984 || 3.121 || 0.787 || 2.94 || 7.8 || 506 |
| RmSQ || 3.561 || 100 || 15.68 || 27.22 || 2.604 || 4.878 || 506 |
| RmSQ_Inverse || 0.01 || 0.281 || 0.143 || 0.048 || −2.048 || 3.283 || 506 |
| Tax || 20.2 || 711 || 339.318 || 180.67 || 0.373 || −0.074 || 506 |
| ZonePr || 0 || 100 || 13.295 || 23.049 || 2.068 || 3.625 || 506 |
| ZonePr_Square root || 0 || 10 || 2.109 || 2.977 || 1.048 || −0.19 || 506 |

**You may ask: Why don’t we perform normalization for continuous variables in the Airline Recommendation dataset?**

That's a great question. Let me explain.

Normalization is typically important for machine learning algorithms that rely on the ordinal least squares (`OLS`) estimation method, such as linear regression. These algorithms perform best with normally distributed data, which helps achieve a better model fit. Since the Boston Housing dataset has a continuous target variable, linear regression is an appropriate method, making data normalization beneficial.

However, other algorithms—such as logistic regression, decision trees, or random forests—are based on different estimation methods and do not require normally distributed data. For instance, logistic regression uses maximum likelihood estimation (`MLE`), which does not assume normality. Therefore, normalizing data may not provide any benefits for these algorithms and can complicate result interpretation due to changes in measurement scales.

For example, if we transform a predictor by taking its square root, the model will be trained on this transformed value. When analyzing the results, such as a regression coefficient, interpreting the predictor's effect on the target variable in terms of its square root can be difficult. To make the interpretation meaningful, we would need to convert the predictor back to its original scale, which adds unnecessary complexity.

![](images/ufig5_41.jpg)

170. In the **Airline Recommendation** dataset, we have a binary target variable, making logistic regression the appropriate choice for predictive modeling. Moreover, advanced machine learning algorithms like neural networks also do not require normally distributed data, though they may benefit from data standardization to improve model fit. Some advanced methods even include built-in data standardization options, allowing us to experiment with different methods dynamically. Therefore, there is no need to normalize continuous variables in this dataset.

## Discretization Example for the Boston Housing

To illustrate variable discretization, let's consider a hypothetical scenario. Suppose we want to convert the continuous target field `Imv` into a categorical field for prediction purposes. To achieve this, we need to perform variable discretization. We will use the `Binning` node and apply the `Quantiles` (equal-frequency binning) method.

Follow the steps below to perform discretization:

1.  Open the “**Boston_Modify**” stream created earlier.
2.  From the `Field Ops` group, add a `Binning` node to the stream and connect it to the Type node. Open the node settings.
3.  For the `Bin field`, select `Imv`.
4.  For the `Binning method`, select `Tiles (equal count)`.
5.  Select `Quartile (4)` to divide the data into four equal-frequency bins.

    ![](images/ufig5_42.jpg)

6.  Click Apply, and then click OK.

171. By adding a Data Audit node, you can see the result of the discretization. [Figure 5.9](#chapter5.xhtml#fig5_9) shows the new target field, `Imv_TILE4`, which is now a categorical field with four levels, each having an equal frequency count.

![FIGURE 5.9 Discretization results—Quantile/binning method. Return to text.⏎](images/fig5_9.jpg)

FIGURE 5.9 Discretization results—Quantile/binning method. [Return to text.⏎](#chapter5.xhtml#b5fig5_9)

### Trying a Different Discretization Method

Now, let's try a different discretization method. Repeat the same process, but change the `Binning method` to `Fixed-width/binning (equal-width binning)` and set the `Bin width` to 10. This method divides the data into evenly spaced intervals based on the specified bin width. The result is a new categorical target field, `Imv_BIN`, which also has four levels but with varying frequency counts (see [Figure 5.10](#chapter5.xhtml#fig5_10)).

![](images/ufig5_43.jpg)![FIGURE 5.10 Discretization results—Fixed width/binning method. Return to text.⏎](images/fig5_10.jpg)

FIGURE 5.10 Discretization results—Fixed width/binning method. [Return to text.⏎](#chapter5.xhtml#b5fig5_10)

172. Discretization is a powerful tool in data mining when converting continuous fields into categorical fields for analysis. SPSS Modeler makes this task easy with the `Binning` node, allowing users to apply different discretization methods without any technical challenges.

## Chapter Summary

Data modification is a crucial process in data mining that involves altering the original dataset to enhance its quality, completeness, and compatibility for predictive modeling. It encompasses various techniques such as data cleaning, transformation, and reduction. In this chapter, we covered three primary data modification techniques: replacement, imputation, and transformation.

*   **Replacement** allows us to recode, correct, and assign values in the dataset, often used to improve data quality.
*   **Imputation** fills in missing values with estimated ones, ensuring a complete dataset and preventing the loss of important information.
*   **Transformation** creates new variables by modifying existing ones, helping standardize or normalize data, convert formats, or aggregate data.

We introduced several methods for imputation, normalization, and discretization. The choice of method depends on the dataset's characteristics, the machine learning technique being applied, and the goals of the data mining project. It requires careful consideration of the potential impact on the data, such as the introduction of bias during imputation or information loss during normalization or aggregation.

Data modification is a dynamic and iterative process, often requiring multiple rounds of preprocessing to refine and optimize the dataset for predictive modeling. In this chapter, we also learned how to apply these data modification techniques using SPSS Modeler, demonstrated with two different datasets.

## Chapter Discussion Questions

173.

1.  What is data modification, and why is it important in the data mining process?
2.  Provide some practical examples where data modification is necessary.
3.  What are the benefits of data modification, and what challenges might arise when using data modification techniques?
4.  What are the primary data modification techniques? Provide examples.
5.  What are the differences between replacement, imputation, and transformation techniques in data modification? Provide examples.
6.  How do we select the appropriate data modification techniques for a given dataset?
7.  How can the choice of data modification techniques influence the performance and outcome of a data mining project?
8.  Provide examples of situations where replacement techniques can be used to clean data.
9.  What are missing values, and how do they affect the data mining process?
