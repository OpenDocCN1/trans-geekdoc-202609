Lower limit = 25th percentile – IQR*1.5 (13.3)

# 13.3.3 Feature Selection

The process of limiting the number of input parameters or attributes by removing unnecessary features is known as feature selection. Reducing the number of factors is vital to improve model performance and lowering the computational cost of the modelling process. One crucial function that aids in reducing the number of input attributes or variables in forecasting is the “feature importance score,” which offers knowledge and insight into the working dataset.

The methods used to rate each input feature for a particular model are referred to as “feature importance,” and the scores only represent the “importance” of each feature. A higher score denotes a greater influence of that specific property on the model predicting the target attribute. In this research, the random forest algorithm is used to determine the feature importance score.

# 13.3.4 Data Normalization

It is necessary to scale variables that comprise multiple qualities with disparate units to a particular scale to guarantee that each attribute is given equal weight. Data normalization is the term for this procedure. This keeps a less significant characteristic with a larger range of values from overshadowing a possible more significant trait. In this instance, we use the mean-standard deviation scaling or Z-score normalization to rescale all of the attributes. The set has been standardized through the incorporation of the computational formula, which is expressed in the following equation:

\( X_{norm} = \frac{X - X_{mean}}{X_{std}} \) (13.4)

where X_norm is the feature value after normalization, X is the feature value, X_mean is the mean of the population, and X_std is the standard deviation of the population.

# 13.3.5 AQI Calculation

After testing with a normalized dataset using a minmax scale with a range of 0–1, the AQI values are determined. The formula to convert each concentration of a pollutant to the Air Quality Index is indicated as follows: