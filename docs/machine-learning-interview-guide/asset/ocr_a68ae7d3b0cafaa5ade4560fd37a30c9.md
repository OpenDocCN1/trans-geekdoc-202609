techniques, like average filling, forward filling, etc, which can be used to fill the missing values.

# Question 5: Explain the concept of imputation for missing data and some strategies to handle it.

Answer: The concept of imputation is replacing the missing data with a certain value and it is very critical as it helps to keep the volume of data the same or similar, as missing values sometimes can be extremely high in volume which will lead to changes in the characteristics of the entire data.

There are multiple strategies to handle missing values. Some of the popular ones are as follows:

We can remove the entire row where we encountered missing values. This method can be hazardous if the volume of the data removed is very high. This will lead to a change in the data characteristics as the rest of the features with data will take a hit.

If we notice that the volume of the missing values is quite high and the feature is not that significant, we can drop the feature altogether to increase the data quality.

We can fill the missing values with the average or mean of the entire column or the average of some logical subsection which can be found after some data analysis.

Instead of filling with average, it can be filled with min value, max value, mode value, etc.

Note that handling missing values takes time to analyze and constant back and forth with the domain expert.

# Question 6: What are outliers in a dataset, and how can they affect supervised learning?

Answer: Outliers are defined as some data points that are out of the general data distribution or some abnormal points