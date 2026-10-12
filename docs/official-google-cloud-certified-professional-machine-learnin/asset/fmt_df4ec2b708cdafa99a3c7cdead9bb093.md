
# Feature Crosses

A *feature cross*, or synthetic feature, is created by multiplying (crossing) two or more features. It can be multiplying the same feature by itself [`A * A`] or it can be multiplying values of multiple features, such as [`A * B * C`]. In machine learning, feature crosses are usually performed on one‐hot encoded features—for example, `binned_latitude × binned_longitude`. (For more information, see `https://developers.google.com/machine-learning/crash-course/feature-crosses/video-lecture`.)

There are two ways to use feature cross:

*   A feature cross is used when a single feature on its own has less predictive ability compared to combined features. For example, we have a model that needs to predict how crowded the street‐based location of people is at a certain time of the day. If we build a feature cross from both these features, [`location (market, curbside) × time of the day`], then we'll end up with vastly more predictive ability than either feature on its own. For example, if there is a farmers market on Tuesday evening, it will be more crowded. If there is no farmers market on Tuesday evening, it will be less crowded.

*   In linear problems with highly complex models, a feature cross is used to represent nonlinearity in a linear model by multiplying (crossing) two or more features. Linear learners scale well to massive data. Using feature crosses on massive datasets is one efficient strategy for learning highly complex models. Let's look at an example. As shown in [Figure 3.1](#c03.xhtml#c03-fig-0001), a dot represents sick people, and a rectangle represents healthy people. It is difficult to separate by line or by a linear method.

![FIGURE 3.1 Difficult to separate by line or a linear method](images/c03f001.png)

[**FIGURE 3.1**](#c03.xhtml#R_c03-fig-0001) Difficult to separate by line or a linear method

This is a linear problem, but seeing the data distribution of these variables, it's hard to separate the dots from the rectangles by using a straight line, or it's hard to classify these by using a linear method, as shown in [Figure 3.2](#c03.xhtml#c03-fig-0002). It's difficult to separate classes by line.

![FIGURE 3.2 Difficult to separate classes by line](images/c03f002.png)

[**FIGURE 3.2**](#c03.xhtml#R_c03-fig-0002) Difficult to separate classes by line

That is why we will cross these features, dot versus rectangle, to create a feature cross—for example, `AB = A * B`. Please refer to this link to understand the concept of encoding nonlinearity: `https://developers.google.com/machine-learning/crash-course/feature-crosses/encoding-nonlinearity`.

[Figure 3.3](#c03.xhtml#c03-fig-0003) summarizes all the feature engineering techniques for converting numerical and categorical data we covered so far.

![FIGURE 3.3 Summary of feature columns Google Cloud via Coursera, www.coursera.org/professional‐certificates/preparing‐for‐google‐cloud‐machine‐learning‐engineer‐professional‐certificate](images/c03f003.png)

[**FIGURE 3.3**](#c03.xhtml#R_c03-fig-0003) Summary of feature columns Google Cloud via Coursera, [www.coursera.org/professional‐certificates/preparing‐for‐google‐cloud‐machine‐learning‐engineer‐professional‐certificate](https://www.coursera.org/professional-certificates/preparing-for-google-cloud-machine-learning-engineer-professional-certificate)

# TensorFlow Transform

Increasing the performance of a TensorFlow model requires an efficient input pipeline. First we will discuss the TF Data API and then we'll talk about TensorFlow Transform.

## TensorFlow Data API (tf.data)

An efficient data input pipeline can drastically improve the speed of your model execution by reducing device idle time. Consider incorporating the following best practices as detailed `here` to make your data input pipeline more efficient:

*   Prefetch transformation to overlap preprocessing and model execution of a training step. This transformation decouples the time when data is produced to the time when data is consumed. The `tf.data` API provides the `tf.data.Dataset.prefetch` transformation.

*   The `tf.data.Dataset.interleave` transformation parallelizes the data reading. By using the interleave transformation, you can mitigate the impact of the various data extraction overhead.

*   Use the cache transformation to cache data in memory during the first epoch. The `tf.data.Dataset.cache` transformation can cache a dataset, either in memory or on local storage. This will save some operations (like file opening and data reading) from being executed during each epoch.

*   Vectorize user‐defined functions on a batch of datasets. The dataset is passed in to the map transformation.

*   Reduce memory usage when applying the interleave, prefetch, and shuffle transformations.

## TensorFlow Transform

The TensorFlow Transform library is part of TensorFlow Extended (TFX) and allows you to perform transformations prior to training the model and to emit a TensorFlow graph that reproduces these transformations during training. Using tf.Transform avoids the training‐serving skew. In Google Cloud, you can create transform pipelines using Cloud Dataflow. Some of the steps that TF Transform takes for transformations during training and serving are analyzing training data, transforming training data, transforming evaluation data, producing metadata, feeding the model, and serving data, as shown in [Figure 3.4](#c03.xhtml#c03-fig-0004).

![FIGURE 3.4 TensorFlow Transform ¶ Source: Adapted from Google Cloud](images/c03f004.png)

[**FIGURE 3.4**](#c03.xhtml#R_c03-fig-0004) TensorFlow Transform ¶ Source: `Adapted from Google Cloud`

You can run the previous pipeline using Cloud Dataflow and BigQuery:

1.  Read training data from BigQuery.
2.  Analyze and transform training data using tf.Transform Cloud Dataflow.
3.  Write transformed training data to Cloud Storage as TFRecords.
4.  Read evaluation data from BigQuery.
5.  Transform evaluation data using the `transform_fn` produced by step 2 in Cloud Dataflow.
6.  Write transformed training data to Cloud Storage as TFRecords.
7.  Write transformation artifacts to Cloud Storage for creating and exporting the model.

[Table 3.2](#c03.xhtml#c03-tbl-0002) shows how you can run a TFX pipeline using Google Cloud Platform (GCP) services.

[**TABLE 3.2**](#c03.xhtml#R_c03-tbl-0002) Run a TFX pipeline on GCP

| Step | TFX library | GCP service |
| --- | --- | --- |
| Data extraction & validation | TensorFlow Data Validation | Cloud Dataflow |
| Data transformation | TensorFlow Transform | Cloud Dataflow |
| Model training & tuning | TensorFlow (tf.Estimators and tf.Keras) | Vertex AI Training |
| Model evaluation & validation | TensorFlow Model Analysis | Cloud Dataflow |
| Model serving for prediction | TensorFlow Serving | Vertex AI Prediction |

# GCP Data and ETL Tools

We will cover the complete data analytics ecosystem in detail, from collecting to storing data, in [Chapter 8](#c08.xhtml), "Model Training and Hyperparameter Tuning." Here are two tools that will help with data transformation and ETL in Google Cloud:

*   **Cloud Data Fusion** is a code‐free web UI–based managed service that helps build and manage extract, transform, load (ETL) or extract, load, transform (ELT) pipelines from various data sources. The web UI helps you to clean and prepare data with no infrastructure management. It also supports Cloud Dataproc, which is another service to run and manage Hadoop and Spark workloads on Google Cloud. Using Dataproc as an execution environment, Cloud Data Fusion allows you to run MapReduce and Spark streaming pipelines. Refer to this link to learn more: `https://cloud.google.com/data-fusion#section-9`.
