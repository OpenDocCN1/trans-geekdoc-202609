+   ■ In other cases, there are possibilities to reconstruct the value based on other entries. For example, we can find out the name of a country if we have the name of a city and an administrative unit. Conversely, we can often determine the country/city by a postal code.

You can find more sophisticate approaches to imputation in this post.

# Outlier Handling

Outlier handling is another way to increase the accuracy of data representation. Outliers are data points that are significantly different from other observations.

This graph shows how outliers can influence the ML model. By dismissing the outliers, we can achieve more accurate results.

![](bbox=[0.19, 0.42, 0.81, 0.7])

It can be done by removing or replacing outliers. Check out this post for an overview of the five most popular approaches to handling outliers.

# One-Hot Encoding

Categorical values (often referred to as nominal) such as gender, seasons, pets, brand names, or age groups often require transformation, depending on the ML algorithm used. For example, decision trees can work with categorical data. However, many others need the introduction of additional artificial categories with a binary representation.