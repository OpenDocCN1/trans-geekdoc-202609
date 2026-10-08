# Understanding the Apache Spark ML learning library

To start using the Spark functionality, you need to create a Spark session. A Spark session creates a SparkContext object, which is the entry point to the Spark functionality. The following sample code shows how to create a Spark session:

```
from pyspark.sql import SparkSession
spark = SparkSession.builder.appName('appname').
getOrCreate()
```

A Spark DataFrame can be constructed from many different sources, such as structured data files (for example, CSV or JSON) and external databases. The following sample code reads a CSV file into the Spark DataFrame:

```
dataFrame = spark.read.format('csv').load(file_path)
```

There are many transformers for data processing and transformation in Spark, such as Tokenizer (breaks text down into individual words) and StandardScaler (normalizes a feature to unit deviation/or zero mean). You can find a list of supported transformers at https://spark.apache.org/docs/2.1.0/ml-features.html.

To use a transformer, first, you must initiate it with parameters, then call the fit() function on the DataFrame that contains the data, and finally call the transform() function to transfer the features in the DataFrame:

```
from pyspark.ml.feature import StandardScaler
```

```
scaler = StandardScaler(inputCol="features", outputCol=
"scaledFeatures",withStd=True,withMean=False)
scalerModel = scaler.fit(dataFrame)
scaledData = scalerModel.transform(dataFrame)
```

+   **Model training:** Spark ML supports a large number of machine learning algorithms for classification, clustering, recommendation, and topic modeling. You can find a list of ML algorithms at https://spark.apache.org/docs/1.4.1/mllib-guide.html. The following code sample shows how to train a logistic regression model:

```
from pyspark.ml.classification import LogisticRegression
lr_algo = LogisticRegression(maxIter regParam,
elasticNetParam = Param)
lr_model = lr_algo.fit(dataFrame)
```