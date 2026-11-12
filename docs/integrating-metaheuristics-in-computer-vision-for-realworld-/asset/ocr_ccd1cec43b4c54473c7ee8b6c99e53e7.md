# 6.3 Feature Extraction

Feature extraction is a critical method in the domains of machine learning and computer vision to locate and extract important characteristics from large data sets. The technique of extracting features from raw data so that they can be utilized to categorize or analyze the data is known as feature extraction. This method is essential to many applications, such as audio and image identification, natural language processing, and predictive modelling. Here, we'll go through the idea of feature extraction, why it’s important, and a few feature extraction strategies.

The most crucial elements in the data that can be utilised to create predictions or categorise the data are found and extracted using feature extraction in machine learning. Finding features that are most pertinent to the job at hand is a step in the feature extraction process. This can be achieved by looking at the data and finding trends or connections between various features. These features can be located and then extracted for use in additional analysis.

Many methods are frequently employed for feature extraction. Principal component analysis (PCA) is one of the most popular approaches. The most crucial features in a dataset can be found using the PCA method [14, 15]. It works by locating the set of linear features that best accounts for the variation in the data. By doing this, it is able to keep the most crucial properties while reducing the data’s dimensionality.

Linear discriminant analysis (LDA) is a different method that is frequently employed for feature extraction [15]. Finding the features that distinguish between several classes of data best is done using the LDA approach. It works by figuring out which linear feature combination maximises the distance between different data classes. This makes it possible to pinpoint the characteristics that are crucial for categorization tasks.

# 6.3.1 Principal Component Analysis

A set of correlated variables can be changed into a set of uncorrelated variables using the mathematical technique of principal component analysis (PCA) [15]. Identifying a new set of variables—referred to as principal components—that best capture the variation in the initial dataset is the main objective of PCA. These underlying components are linear combinations of the initial variables that were chosen to account for the majority of the data fluctuation.

# 6.3.1.1 Procedure

The following are the steps necessary to put PCA into practice.

+   Step 1: Data Preprocessing

Preprocessing the data is the first step in putting PCA into practice. To prepare the data for analysis, this entails cleaning and standardizing it. Outliers, missing values, and anomalies must all be eliminated from the data because they can significantly affect PCA’s findings. The data should also be normalized to ensure that each feature has a unit variance and zero mean. By doing this, it is certain that the analysis will give each feature equal weight.