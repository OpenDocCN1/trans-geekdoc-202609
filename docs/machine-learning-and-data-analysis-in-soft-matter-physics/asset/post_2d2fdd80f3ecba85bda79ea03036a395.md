
![](img/c4a53cbbd40023d194b7887dddf3293b_55_0.png)

- **Accuracy:** All the data that make up a database within the business must be highly accurate. One way to corroborate their accuracy is by comparing them with different sources. If the source is not found or has errors, the stored information will have the same problems.

- **Coherence:** The data must be consistent with each other, so you can be sure that the information of an individual or body is the same in different forms of storage used.

- **Validity:** The stored data must have certain regulations or established restrictions. Likewise, the information has to be verified to corroborate its authenticity.

- **Uniformity:** The data that make up a database must have the same units or values. It is an essential aspect when carrying out the Data Cleansing process since it does not increase the complexity of the procedure.

- **Data Verification:** The process must be verified at all times, both the appropriateness and the effectiveness of the procedure. Said verification is carried out through various instances of the study, design, and validation stages. The drawbacks are often evident after the data is applied in a certain amount of changes.

- Clean Data Backflow: After eliminating quality problems, the already clean data must be replaced by those not located in the original source, so that legacy applications obtain the benefits of these, obviating the need for applications of actions of data cleaning afterward.

## 2.2 HANDLING MISSING DATA

Handling missing data is a crucial part of data preprocessing in any scientific field, including Soft Matter Physics. Missing data can occur due to various reasons, such as measurement errors, equipment failures, or incomplete simulations. Dealing with missing data requires careful consideration to ensure that the final dataset remains reliable and representative of the underlying phenomena. Here are some common techniques for handling missing data:

### Deletion of Missing Data

One straightforward approach is to remove the rows or samples with missing data. This method is known as “listwise deletion” or “complete-case analysis.” While simple, this method might lead to a loss of valuable information, especially if the proportion of missing data is substantial.

### Imputation

Imputation involves estimating missing values based on the information available in the dataset. Several imputation techniques exist, such as:

- a. Mean/Median/Mode Imputation: Replace missing values with the mean, median, or mode of the corresponding feature. This method is quick and easy but might not capture the true underlying relationships in the data.
- b. Linear Interpolation: For sequential or time-series data, missing values can be interpolated using linear interpolation, assuming a linear relationship between adjacent data points.
- c. Multiple Imputation: Multiple imputation creates multiple plausible imputed datasets based on statistical models and combines their results to obtain more robust estimates. This method considers the uncertainty associated with imputation.
- d. K-Nearest Neighbors (KNN) Imputation: KNN imputation estimates missing values based on the values of the nearest neighbors in the feature space.
- e. Expectation-Maximization (EM) Imputation: EM imputation iteratively estimates missing values based on a probabilistic model of the data.

### Flagging Missing Values

Instead of imputing the missing values, you can create binary flags or indicator variables for each feature, indicating whether the value is present or missing. This way, the information about missingness is retained and can be used as a separate feature in the analysis.

### Domain-Specific Imputation

In Soft Matter Physics, domain knowledge might help in devising specific imputation methods tailored to the physical context of the data. For example, missing particle positions in a simulation might be inferred based on the known dynamics of the system.

### Model-Based Imputation

If the dataset contains sufficient information, you can build predictive models for the missing values based on the other features in the dataset. These models can be regression models or machine learning algorithms.

It’s essential to carefully evaluate the chosen imputation method and its potential impact on the downstream analysis. Additionally, the amount of missing data and the underlying cause should be considered when selecting the most appropriate imputation strategy. Always document the handling of missing data to ensure transparency and reproducibility of the results. Keep in mind that imputation introduces some level of uncertainty, and sensitivity analysis may be required to assess the robustness of the findings to different imputation approaches.

## 2.3 DATA REDUCTION

Data reduction techniques can be applied to obtain a reduced representation of the data set that is much smaller in volume, yet closely maintains the integrity of the original data. That is, mining on the reduced data set should be more efficient yet produce the same (or almost the same) analytical results.

### 2.3.1 Data Reduction Strategies

Data reduction strategies include dimensionality reduction, numerosity reduction, and data compression.

### Dimensionality Reduction

Dimensionality reduction is the process of reducing the number of random variables or attributes under consideration. Dimensionality reduction methods include wavelet transforms and principal components analysis, which transform or project the original data onto a smaller space. Attribute subset selection is a method of dimensionality reduction in which irrelevant, weakly relevant, or redundant attributes or dimensions are detected and removed.

### Numerosity Reduction

Techniques of numerosity reduction replace the original data volume by alternative, smaller forms of data representation. These techniques may be parametric or nonparametric.

For parametric methods, a model is used to estimate the data, so that typically only the data parameters need to be stored, instead of the actual data. (Outliers may also be stored.) Regression and log-linear models are examples. Nonparametric methods for storing reduced representations of the data include histograms, clustering, sampling, and data cube aggregation.

### Data Compression

In data compression, transformations are applied so as to obtain a reduced or “compressed” representation of the original data. If the original data can be reconstructed from the compressed data without any loss of information, the data reduction is called lossless. If, instead, we can reconstruct only an approximation of the original data, then the data reduction is called lossy. There are several lossless algorithms for string compression, however, they typically allow only limited manipulation of the data. Dimensionality reduction and numerosity reduction techniques can also be considered forms of data compression.

There are many other ways of organizing methods of data reduction. The computational time spent on data reduction should not outweigh or “erase” the time saved by mining on a reduced data set size.

### 2.3.2 Wavelet Transforms

The discrete wavelet transform (DWT) is a linear signal processing technique that, when applied to a data vector X, transforms it to a numerically different vector, X', of wavelet coefficients. The two vectors are of the same length. When applying this technique to data reduction, we consider each tuple as an n-dimensional data vector, that is, X = (x₁, x₂ ... xₙ), depicting n measurements made on the tuple from n database attributes.

“How can this technique be useful for data reduction if the wavelet transformed data are of the same length as the original data?” The usefulness lies in the fact that the wavelet transformed data can be truncated. A compressed approximation of the data can be retained by storing only a small fraction of the strongest of the wavelet coefficients. For example, all wavelet coefficients larger than some user-specified threshold can be retained. All other coefficients are set to 0. The resulting data representation is therefore very sparse, so that operations that can take advantage of data sparsity are computationally very fast if performed in wavelet space. The technique also works to remove noise without smoothing out the main features of the data, making it effective for data cleaning as well. Given a set of coefficients, an approximation of the original data can be constructed by applying the inverse of the DWT used.

The DWT is closely related to the discrete Fourier transform (DFT), a signal processing technique involving sines and cosines. In general, however, the DWT achieves better lossy compression. That is, if the same number of coefficients is retained for a DWT and a DFT of a given data vector, the DWT version will provide a more accurate approximation of the original data. Hence, for an equivalent approximation, the DWT requires less space than the DFT.

There is only one DFT, yet there are several families of DWTs. Figure 1 shows some wavelet families. Popular wavelet transforms include the Haar-2, Daubechies-4, and Daubechies-6 transforms. The general procedure for applying a discrete wavelet transform uses a hierarchical pyramid algorithm that halves the data at each iteration, resulting in fast computational speed. The method is as follows:
