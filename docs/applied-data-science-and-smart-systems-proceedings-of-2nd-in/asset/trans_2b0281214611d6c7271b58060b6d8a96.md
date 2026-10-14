
Many elements, like `memory`, `display`, `battery life`, `camera quality`, and so forth, are taken into account while buying mobile phones. Due to the lack of resources required to cross-validate the price, people make incorrect decisions ([Singh et al., 2019](#ch46.xhtml#ref46_15); Krishnamurthy et al., 2021). The data here is important because it describes model perfectly. Now the main question arises why we chose this format to represent data? Simple answer is that it gives data as per the price in the online apps. We are using it in our daily life, which we can use the same in our daily life. Now let’s highlight about description or how to take data. The price of the data here is taken from `amazon`, `eBay`, `Flipkart`, etc., are our source of the data that we collected to predict price as per festivals offers and normal discounts are given by the apps or by the companies. All the features are the same, but we added more columns predicting our mobile price.

## Dimensionality reducation

By acquiring a set of key variables, or features, we design a prediction model by limiting the amount of random variables that are taken into consideration. Data opening fix technique for important data in the request to create the partitions required to contain the disaster and provide the missing data ([Brar et al., 2022](#ch46.xhtml#ref46_20); [Nadeem et al., 2023](#ch46.xhtml#ref46_12)).

Prediction model used in this paper is not totally practical since it becomes more difficult to present the training set and use that dataset to generate predictions the more features there are. Most of these functions can occasionally be redundant because they are connected with one another, which can reduce the model’s accuracy. With the help of dimensionality reduction algorithms in this situation, ML employs two distinct types of dimensionality reduction techniques such as `feature selection` and `feature extraction`. During element selection, we are looking for the dimensions that provide greatest data and filter unnecessary data for the model’s prediction.

Using `feature extraction`, main goal is to identify a new set of dimensions getting that result from combining the original dimensions. In machine learning, we typically add as many features to collect key details and produce more accurate results. As the number of elements rises, the model’s performance will eventually start to suffer. This frequently referred as the `dimension curse`. The problem with dimensionality is that, for our prediction model, sample density falls off exponentially as dimensionality rises. The dimension of the feature space increases and becomes sparser as we continue to add features while maintaining the number of training examples. Finding a correct answer for a ML model is significantly simpler as a result of this rarity, which is very likely to cause any model to over fit ([Figure 46.3](#ch46.xhtml#fig46_3)).

![Figure 46.3 Exploring the data values](images/fig46_3_B.jpg)

[Figure 46.3 Exploring the data values](#ch46.xhtml#R_fig46_3)

## Exploratory data analysis (EDA)

EDA is a best approach for data analysis using visual techniques. It is used to discover the trends, patterns in the data set and to check assumptions using statistical summary and graphical representations of the data set. We load the dataset using the Pandas module from the python and then print the first five rows. We use the `head()` function to print the first five lines ([Figure 46.4](#ch46.xhtml#fig46_4)).

![Figure 46.4  Example of data set by using head() function](images/fig46_4_B.jpg)

[Figure 46.4  Example of data set by using head() function](#ch46.xhtml#R_fig46_4)

Different datasets can exhibit various characteristics, and the choice of data representation methods can significantly impact our understanding of the data and the modeling process. Various data visualization techniques can be employed to gain insights into the dataset’s features and values, ultimately facilitating the model prediction and elucidating the relationships between features. Under the current situation, the system uses a technique where a seller randomly determines a price without the buyer knowing the product’s worth ([Balaji et al., 2023](#ch46.xhtml#ref46_13)).

Here are some common data representation methods and their purposes:

Heat maps are useful for visualizing the relationships between data points in a matrix. They are often employed to display correlation matrices, making it easier to identify patterns and dependencies between variables.

Correlation heat maps specifically focus on depicting the correlation coefficients between different variables. They help highlight which features are strongly correlated or inversely correlated with each other.

Count plots are typically used for categorical data and help visualize the distribution of categories within a variable. They provide insights into the frequency of each category.

The `describe()` function is a statistical tool that provides summary statistics about the dataset. It calculates measures like mean, standard deviation, minimum, maximum, quartiles, etc. This function can help identify outliers, central tendencies, and the overall distribution of numerical features.

Using these representation methods collectively allows data scientists and analysts to explore and understand the dataset thoroughly. It aids in identifying potential data issues, such as missing values or outliers, and can reveal valuable insights about feature relationships and data distributions. This understanding is crucial for building accurate predictive models and making informed decisions based on the data.

Addressing missing data in a dataset is a critical consideration in data analysis and modeling. Missing data can occur when certain information is not provided for one or more data points within the dataset.

There are various reasons why data may be missing, such as survey respondents choosing not to disclose certain information (e.g., income or address). In such cases, many data values may be absent from the dataset, creating a challenge for data analysis ([Figure 46.5](#ch46.xhtml#fig46_5)).

![Figure 46.5 Data description of dataset that we have taken](images/fig46_5_B.jpg)

[Figure 46.5 Data description of dataset that we have taken](#ch46.xhtml#R_fig46_5)

Missing data is a common and real-world problem in data science and statistics. It can lead to biased or inaccurate results if not handled properly. Data scientists and analysts employ various techniques to manage missing data, such as:

Imputation: This involves filling in missing values with estimated or imputed values based on statistical methods. Common imputation techniques include mean imputation, median imputation, mode imputation, or using predictive models to estimate missing values.

Data collection improvement: In some cases, improving data collection processes can help reduce the occurrence of missing data. This may involve better survey design, clearer instructions to respondents, or data validation checks during data entry.

Deletion: In certain situations, it may be appropriate to remove data points with missing values from the analysis. However, this should be done carefully, as it can lead to a loss of valuable information and potential bias.

Advanced imputation: Advanced techniques, such as multiple imputation, can be employed when the missing data pattern is complex. Multiple imputation generates multiple complete datasets with imputed values and combines results to provide more robust estimates.

Handling missing data is an essential step in data preprocessing to ensure that analyses and models are based on as much available information as possible, without introducing bias or inaccuracies due to missing values.
