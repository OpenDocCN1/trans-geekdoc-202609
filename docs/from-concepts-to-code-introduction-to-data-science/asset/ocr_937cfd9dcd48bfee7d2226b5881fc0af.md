# Sourcing Data

For a model to predict values in a range, there must be instances of the target data over that range. The real estate problem, if we wish to accurately predict home values between $300,000 and $2,000,000, then we need these examples in the dataset. If the maximum home value in the dataset is $600,000, then any prediction above that maximum should be avoided.

For classification problems such as determining if a check deposit is fraudulent or not, many instances of both fraud and legitimate deposits are required. This making this challenging, fraud is often rare. Sampling methods such as reusing the data can sometimes improve the predictive capability of the model, but real data is preferable data.

For object detection, the easiest way to get started is to find a pre-trained model that has been sourced.¹ One source for models is the Model Garden for TensorFlow [1]. Whether building an object detection model from scratch or using a pre-trained model, the dataset should include cases where the object is in the image, cases where it is not in the image, and edge cases that could confuse the classifier. For example, if the model is looking for pools, an edge case might be a beach, as this might cause misclassifications.

To summarize, it is important to collect all the relevant dimensions for the target values of interest. Including edge cases is recommended where possible, as this can reduce errors. Notice the lack of a simple quantitative answer, such as “collect one thousand rows of data." The question of minimal data sufficiency requires a nuanced answer. Every dataset is different. However, if you are working on a problem similar to one you have already solved, then the solved problem can offer guidance. Also, once some data is available, it can be explored to understand the predictive power of the variables.

# 3.6 Sourcing Data

Once there is an understanding of the data that is needed, the search begins! In the ideal case, the required data has already been collected and stored, and it is a matter of gaining access to that data. Depending on the systems in use and privacy requirements, the steps will vary. For example, if the data contains sensitive information, it may first need to be deidentified. If the data is divided across many different machines, or servers, then access may need to be granted to each server. After gaining access, the data may need to be collected from each server.

> ¹Pre-trained models can be useful for many other tasks requiring massive datasets, such as language tasks.