
# Dataprep by Trifacta

**Dataprep by Trifacta** (`https://cloud.google.com/dataprep`) is a serverless intelligent tool for visually exploring, cleaning, and preparing structured and unstructured data for analysis, reporting, and machine learning at any scale. There is no infrastructure to deploy or manage. Also, there is no infrastructure to manage as it is serverless and no need to write code as it is UI–based. It suggests your next data transformation and predicts with each UI input.

## Summary

In this chapter, we discussed feature engineering and why it's important to transform numerical and categorical features for model training and serving.

Then we discussed various techniques to transform numerical features, such as bucketing and normalization. We also discussed the technique to transform categorical features such as linear encoding, one‐hot encoding, out of vocabulary, hashing, and embedding.

You learned why it's important to select features and some of the techniques for dimensionality reduction such as PCA. Then we covered class imbalance and how precision and recall impacts the classification. For imbalanced classes, AUC PR is more effective than AUC ROC.

We also discussed why feature crosses are important and the benefits of feature crossing.

We covered how to represent data for TensorFlow using `tf.data` and then we covered `tf.Transform` and how to process pipelines using `tf.Transform` on Google Cloud. You learned about some of the Google Cloud data processing and ETL tools such as Cloud Data Fusion and Cloud Dataprep.

## Exam Essentials

*   **Use consistent data processing.** Understand when to transform data, either before training or during model training. Also know the benefits and limitations of transforming data before training.

*   **Know how to encode structured data types.** Understand techniques to transform both numeric and categorical data such as bucketing, normalization, hashing, and one‐hot encoding.

*   **Understand feature selection.** Understand why feature selection is needed and some of the techniques of feature selection, such as dimensionality reduction.

*   **Understand class imbalance.** Understand true positive, false positive, accuracy, AUC, precision, and recall in classification problems and how to effectively measure accuracy with class imbalance.

*   **Know where and how to use feature cross.** You need to understand why feature cross is important and the scenarios in which you would need it.

*   **Understand TensorFlow Transform.** You need to understand TensorFlow Data and TensorFlow Transform and how to architect `tf.Transform` pipelines on Google Cloud using BigQuery and Cloud Data Fusion.

*   **Use GCP data and ETL tools.** Know how and when to use tools such as Cloud Data Fusion and Cloud Dataprep. For example, in case you are looking for a no‐code solution to clean data, you would use Dataprep for data processing and, in case you are looking for a no‐code and UI–based solution for ETL (extract, transform, load), you would use Cloud Data Fusion.

## Review Questions

1.  You are the data scientist for your company. You have a dataset that which has all categorical features. You trained a model using some algorithms. With some algorithms this data is giving good result but when you change the algorithm the performance is getting reduced. Which data transformation strategy would likely improve the performance of your model?

    1.  Write your data in TFRecords.
    2.  Create a feature cross with categorical feature.
    3.  Use one‐hot encoding on all categorical features.
    4.  Oversample the features.

2.  You are working on a neural network–based project. The dataset provided to you has columns with different ranges. While preparing the data for model training, you discover that gradient optimization is having difficulty moving weights to an optimized solution. What should you do?

    1.  Use feature construction to combine the strongest features.
    2.  Use the normalization technique.
    3.  Improve the data cleaning step by removing features with missing values.
    4.  Change the partitioning step to reduce the dimension of the test set and have a larger training set.

3.  You work for a credit card company and have been asked to create a custom fraud detection model based on historical data using AutoML Tables. You need to prioritize detection of fraudulent transactions while minimizing false positives. Which optimization objective should you use when training the model?

    1.  An optimization objective that minimizes log loss.
    2.  An optimization objective that maximizes the precision at a recall value of 0.50.
    3.  An optimization objective that maximizes the area under the precision‐recall curve (AUC PR) value.
    4.  An optimization objective that maximizes the area under the curve receiver operating characteristic (AUC ROC) curve value.

4.  You are a data scientist working on a classification problem with time‐series data and achieved an area under the receiver operating characteristic curve (AUC ROC) value of 99 percent for training data with just a few experiments. You haven't explored using any sophisticated algorithms or spent any time on hyperparameter tuning. What should your next step be to identify and fix the problem?

    1.  Address the model overfitting by using a less complex algorithm.
    2.  Address data leakage by applying nested cross‐validation during model training.
    3.  Address data leakage by removing features highly correlated with the target value.
    4.  Address the model overfitting by tuning the hyperparameters to reduce the AUC ROC value.

5.  You are training a ResNet model on Vertex AI using TPUs to visually categorize types of defects in automobile engines. You capture the training profile using the Cloud TPU profiler plug‐in and observe that it is highly input bound. You want to reduce the bottleneck and speed up your model training process. Which modifications should you make to the `tf.data` dataset? (Choose two.)

    1.  Use the interleave option to read data.
    2.  Set the prefetch option equal to the training batch size.
    3.  Reduce the repeat parameters.
    4.  Decrease the batch size argument in your transformation.
    5.  Increase the buffer size for shuffle.

6.  You have been asked to develop an input pipeline for an ML training model that processes images from disparate sources at a low latency. You discover that your input data does not fit in memory. How should you create a dataset following Google‐recommended best practices?

    1.  Create a `tf.data.Dataset.prefetch` transformation.
    2.  Convert the images into TFRecords, store the images in Cloud Storage, and then use the `tf.data` API to read the images for training.
    3.  Convert the images to `tf.Tensor` objects, and then run `Dataset.from_tensor_slices()`.
    4.  Convert data into TFRecords.

7.  Different cities in California have markedly different housing prices. Suppose you must create a model to predict housing prices. Which of the following sets of features or feature crosses could learn city‐specific relationships between roomsPerPerson and housing price?

    1.  Two feature crosses: `[binned latitude x binned roomsPerPerson]` and `[binned longitude x binned roomsPerPerson]`
    2.  Three separate binned features: `[binned latitude]`, `[binned longitude]`, `[binned roomsPerPerson]`
    3.  One feature cross: `[binned latitude x binned longitude x binned roomsPerPerson]`
    4.  One feature cross: `[latitude x longitude x roomsPerPerson]`
