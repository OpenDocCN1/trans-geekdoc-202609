
# Feature Engineering

*Feature engineering* is the process of transforming raw data coming from various sources such as log files and weather readings to useful features for model training. The features can be numerical or categorical. Let's understand the primary reasons for data transformation.

## Transforming for Data Compatibility

Data consists of both numeric features and non‐numeric features. Your model cannot perform mathematical computation on string type data. That is why it's important to transform such features into a vector or numerical representation understood by the model.

You also need to resize your input data to match to the input node in your model; for example, linear models and feed‐forward neural networks have a fixed number of input nodes. So your input data must always be the same size.

## Transforming for Data Quality

This type of transformation helps the model perform better. For example, converting your text features into lowercase can lead to better performance as can tokenizing, or normalizing numeric features before model training.

Now that you understand why feature engineering is important, let's discuss when to apply feature transformation during model training or the model prediction phase in the next section.

# Consistent Data Preprocessing

Consistent data preprocessing is needed as you can apply transformations while generating the data either on disk or within the model. Let's discuss the approaches:

## Pretraining Data Transformation

This means data transformation is performed before model training on a complete dataset. Your transformation code lives separate from your machine learning model. Advantages of this approach is that computation is performed only once and it can look at the entire dataset to determine the transform.

Some of the disadvantages of this approach are that the same transformation needs to be reproduced at prediction time, and if data changes at prediction, it can lead to skew, especially in the case of online serving or prediction. Another challenge is updating the transformation. If you want to update the data transformation, you would have to rerun the transform on the entire dataset, leading to slow iterations and more compute time.

## Inside Model Data Transformation

In this, the transformation is part of the model code as the model takes in untransformed or raw data as input and transforms it within the model before training. One of the advantages of this approach is that it is easy to decouple your data and transformation. Even if your transformation technique changes, you can still use the same data. You are also using the same transformation during training and serving since it's part of the model. A disadvantage of this method is that if the transform is large or computation heavy, it can increase model latency. Transformations are done by data batches, which can be a problem if you are trying to normalize the data by setting mean values with batches of data and not entire datasets.

This can be solved by `tf.Transform`, which we will cover in the section "TensorFlow Transform" later in this chapter.

# Encoding Structured Data Types

A good feature should be related to business objectives, be known at prediction time, be numeric with magnitude, and have enough examples. Let's look at various types of data in feature engineering that we are going to use throughout this chapter.

## Categorical Data

This data type defines the category, and the data takes only a number of values—for example, yes/no type of data in your data column, male/female as values in the gender category, and so on.

## Numeric Data

This represents data in the form of scalar value or continuous data such as observations, recordings, and measurements.

### Mapping Numeric Values

Integer and floating‐point data don't need special encoding because they can be multiplied by a numeric weight. You may need to apply two kinds of transformations to numeric data: normalizing and bucketing.

#### Normalizing

We covered normalization techniques such as scaling, log scaling, z score, and clipping in the Data Cleaning section of [Chapter 2](#c02.xhtml), "Exploring Data and Building Data Pipelines." You would perform normalization in two cases with numeric data:

*   **Numeric features that have distinctly different ranges (for example, age and income):** In this case, the model gradient descent can slow down convergence due to various data ranges. That is why `AdaGrad` and `Adam` optimization techniques can help, because they create a separate learning rate for each feature.
*   **Numeric features that cover a wide range such as a city:** This type of dataset model will generate a `NaN` data error if it is not normalized. In this situation, even optimizers such as `Adam` and `AdaGrad` can't prevent `NaN` errors when there is a wide range of values in a single feature.

#### Bucketing

Bucketing is transforming numeric data to categorical data. For example, latitude can be a floating‐point value, and it's difficult to represent it while predicting house price with respect to location. Two ways to do bucketing are as follows:

*   **Creating buckets with equal‐spaced boundaries:** You create a range of buckets and some buckets might have more data points compared to others. For example, to represent rainfall, you can bucket by range (0–50 cm, 50–100 cm); you might have more data points in the rainfall range 0–50 cm in an area with less intense rainfall.
*   **Buckets with quantile boundaries:** Each bucket has the same number of points. The boundaries are not fixed and could encompass a narrow or wide span of values.

### Mapping Categorical Values

There are ways to convert or transform your categorical data into numerical data so that your model can understand it.

#### Label Encoding or Integer Encoding

In label encoding, you would use indexing using a vocabulary. If the number of categories of a data field is small, such as breeds of dog or days of the week, you can make a unique feature for each category and assign an integer value. For example, ratings can be assigned such as "satisfactory" is 1, "good" is 2, and "best" is 3. You can apply integer ratings only if the categories represent limited ranges or ordinal values.

#### One‐Hot Encoding

One‐hot encoding is the process of creating dummy variables. This technique is used for categorical variables where order does not matter. The one‐hot encoding technique is used when the features are nominal (do not have any order). Let's discuss what is an ordinal relationship in categorical data first; for example, ordinal variables can be socioeconomic status (low income, middle income, high income), education level (high school, BS, MS, PhD), income level (less than 50K, 50K–100K, over 100K), satisfaction rating (extremely dislike, dislike, neutral, like, extremely like). For categorical variables where no such ordinal relationship exists, such integer encoding is not enough.

In one‐hot encoding, for every categorical feature, a new variable is created. It is a process by which categorical variables are converted into binary representation for the integer encoding or integer values. Let's look at the example of two colors, as shown in [Table 3.1](#c03.xhtml#c03-tbl-0001). Each can be represented by binary values.

**TABLE 3.1** One‐hot encoding example

| Categorical Value | Integer Encoding or Creating a Vocabulary Mapping | One‐Hot Encoding |
| --- | --- | --- |
| Red | 0 | 00 |
| Blue | 1 | 01 |

Sometimes you have large binary spaces to represent, which might lead to sparse representation with lots of 0s.

#### Out of Vocab (OOV)
