
|  1 || 6.781 || 52.161 || 52.161 || 5.314 || 40.878 || 40.878 |
| --- | --- | --- | --- | --- | --- | --- | --- |
|  2 || 3.069 || 23.61 || 75.771 || 4.536 || 34.893 || 75.771 |
|  3 || 0.808 || 6.218 || 81.989 ||  ||  ||  |
|  4 || 0.645 || 4.958 || 86.947 ||  ||  ||  |
|  5 || 0.485 || 3.727 || 90.674 ||  ||  ||  |
|  6 || 0.321 || 2.466 || 93.14 ||  ||  ||  |
|  7 || 0.28 || 2.154 || 95.294 ||  ||  ||  |
|  8 || 0.183 || 1.407 || 96.701 ||  ||  ||  |
|  9 || 0.145 || 1.117 || 97.817 ||  ||  ||  |
| 10 || 0.109 || 0.835 || 98.652 ||  ||  ||  |
| 11 || 0.083 || 0.639 || 99.291 ||  ||  ||  |
| 12 || 0.052 || 0.4 || 99.692 ||  ||  ||  |
| 13 || 0.04 || 0.308 ||   100 ||  ||  ||  |

![FIGURE 12.7 Scree plot based on Eigenvalues. Return to text.⏎](images/fig12_7.jpg)

FIGURE 12.7 Scree plot based on Eigenvalues. [Return to text.⏎](#chapter12.xhtml#b12fig12_7)

453\. To ensure we choose the best structure, we will compare the results from both the two-component and three-component PCA models to see which one provides a more interpretable and meaningful representation of the data.

[Tables 12.8](#chapter12.xhtml#tbl12_8) and [12.9](#chapter12.xhtml#tbl12_9) present the rotated component matrices for two-component and three-component structures, respectively. As observed, Component 1 is similarly structured in both cases, with the only difference being that, in the three-component structure, `LogDistance` is also loaded onto this component. The variables associated with this component capture the primary geographic characteristics of the area.

TABLE 12.8 Rotated Component Matrix with Two Components [Return to text.⏎](#chapter12.xhtml#b12tbl12_8)

| Component   || 1   || 2 |
| --- | --- | --- | --- |
| LogAccess\_LogN || −0.949 ||  |
| --- | --- | --- | --- |
| NiOxSQ\_Inverse || 0.943 ||  |
| B\_Square root || 0.902 ||  |
| RmSQ\_Inverse || 0.84 ||  |
| PtRatio\_LogN || −0.83 ||  |
| Charles\_River\_Square root || −0.708 ||  |
| CrimePC\_Square root ||  || 0.854 |
| IndustPr\_Square root ||  || 0.832 |
| AgePre40 ||  || 0.802 |
| Tax ||  || 0.781 |
| LogDistance\_LogN ||  || −0.757 |
| ZonePr\_Square root ||  || −0.738 |
| Lstat\_Square root ||  || 0.645 |

TABLE 12.9 Rotated Component Matrix with Three Components [Return to text.⏎](#chapter12.xhtml#b12tbl12_9)

| Component || 1 || 2 || 3 |
| --- | --- | --- | --- | --- |
| LogAccess\_LogN || −0.965 ||  ||  |
| --- | --- | --- | --- | --- |
| NiOxSQ\_Inverse || 0.932 ||  ||  |
| B\_Square root || 0.906 ||  ||  |
| RmSQ\_Inverse || 0.843 ||  ||  |
| PtRatio\_LogN || −0.819 ||  ||  |
| Charles\_River\_Square root || −0.698 ||  ||  |
| LogDistance\_LogN || −0.555 ||  ||  |
| CrimePC\_Square root ||  || 0.915 ||  |
| Tax ||  || 0.886 ||  |
| IndustPr\_Square root ||  || 0.614 ||  |
| ZonePr\_Square root ||  ||  || −0.836 |
| Lstat\_Square root ||  ||  || 0.724 |
| AgePre40 ||  ||  || 0.674 |

The major distinction lies in the remaining variables. In the two-component structure, we see a mixture of population characteristics and socio-economic characteristics grouped under Component 2. Additionally, the appearance of `LogDistance` in this component does not seem logical in terms of interpretation.

454\. On the contrary, the three-component structure cleanly separates socio-economic characteristics (e.g., crime rate, tax rate, and business-housing ratio) in Component 2 from population characteristics (e.g., age, residential land ratio, and lower-status population) in Component 3. This clearer distinction makes the three-component structure more interpretable and logical. Thus, we select the three-component PCA structure and use these factors as new predictors for the modeling step.

## Chapter Summary

PCA is a widely used dimensionality reduction technique in data mining, aimed at transforming high-dimensional data into a lower-dimensional format while preserving essential information. PCA works by identifying principal components—new variables that capture the maximum variance in the data. The first principal component accounts for the largest portion of the variability, with each subsequent component capturing a smaller portion. By selecting a subset of principal components that represent a significant portion of the total variance, PCA reduces the dimensionality of data without sacrificing meaningful insights.

PCA offers several key advantages in data mining. It simplifies data representation by reducing the number of variables, making it easier to interpret and visualize. It also eliminates redundant or irrelevant variables, which enhances computational efficiency and reduces the risk of overfitting. Additionally, PCA can reveal hidden patterns and relationships in the data, as the principal components are linear combinations of the original variables. PCA is often used as a preprocessing step in predictive modeling to reduce the number of variables, using principal components that retain the majority of the variance.

However, PCA assumes linearity in the relationships among variables and is sensitive to outliers, which can affect the accuracy of the results. Moreover, interpreting principal components can be difficult because they are formed from combinations of multiple original variables. Despite these limitations, PCA remains an essential tool in data mining for dimensionality reduction, variable selection, and exploratory data analysis.

## Chapter Discussion Questions

1.  What is Principal Component Analysis (PCA) and how does it enable dimensionality reduction?

2.  Discuss the advantages and potential limitations of using PCA to reduce the number of variables in a dataset.

3.  How does PCA capture and quantify the variability in the data through the concept of principal components?

4.  Explain the role of eigenvalues and eigenvectors in determining the importance and direction of each principal component.

5.  In what scenarios would PCA be particularly useful in data mining tasks? Discuss specific applications where PCA has been successfully applied.

6.  What techniques can be used to determine the optimal number of principal components to retain in a given dataset?

7.  Discuss the interpretation of the principal components obtained from PCA. How can the relationships between the original variables and the principal components be understood and analyzed?

8.  What is the purpose of the component rotation in PCA? Discuss primary rotation methods.

9.  Discuss the trade-off between dimensionality reduction achieved by PCA and the potential loss of information. How can the impact of dimensionality reduction on model performance or data analysis outcomes be assessed and evaluated?

## Chapter Exercises

455\.  

### Exercise 1: Principal Component Analysis for the Bank Dataset

1.  Open the `bank` dataset in SPSS Modeler.

2.  Sample the entire dataset. Refer to Appendix A for variable names and descriptions.

3.  Perform data modification as follows:

    *   Impute missing values.

    *   Normalize interval variables.

4.  Conduct a principal component analysis (PCA) for all continuous input variables. Make sure to NOT include `CRSCORE` (the target variable)

    *   **Configure the Model settings:**

        1.  Under the `Model` tab, select `Principal Components` for the Extraction Method.

        2.  Uncheck the box for `Use partition data.`

    *   **Configure the Expert settings:**

        1.  Under the `Expert` tab, select `Expert` mode.

        2.  Select `Correlation matrix`.

    *   **Rotation:**

        1.  Click `Rotation` and select `Varimax` for orthogonal rotation, which simplifies component interpretation.

5.  Identify the number of principal components using the scree plot and the Total variance explained table.

6.  Adjust the number of components as needed.

7.  Present the PCA results: Identify the principal components from the results and the significant variables composing each component.
