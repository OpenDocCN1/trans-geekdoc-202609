indicates that Matplotlib-based graphics should be displayed in the notebook rather than in their own windows. Recall that Seaborn uses Matplotlib.

We've used several IPython magics throughout the book. There are many magics specifically for use in Jupyter Notebooks. For the complete list of magics see:

https://ipython.readthedocs.io/en/stable/interactive/magics.html

# Utility Function to Get the SparkSession

As you'll soon see, you can use Spark SQL to query data in resilient distributed datasets (RDDs). Spark SQL uses a Spark DataFrame to get a table view of the underlying RDDs. A SparkSession (module pyspark.sql) is used to create a DataFrame from an RDD.

There can be only one SparkSession object per Spark application. The following function, which we borrowed from the Spark Streaming Programming Guide, 9 defines the correct way to get a SparkSession instance if it already exists or to create one if it does not yet exist: 0

9 https://spark.apache.org/docs/latest/streaming-programming-guide.html#dataframe-and-sql-operations.

0 Because this function was borrowed from the Spark Streaming Programming Guides DataFrame and SQL Operations section ( https://spark.apache.org/docs/latest/streaming-programming-guide.html#dataframe-and-sql-operations ), we did not rename it to use Pythons standard function naming style, and we did not use single quotes to delimit strings.

lick here to view code image

```
```
[2]: def getSparkSessionInstance(sparkConf):
    """Spark Streaming Programming Guide's recommended method
    for getting an existing SparkSession or creating a new one."""
    if ("sparkSessionSingletonInstance" not in globals()):
        globals()["sparkSessionSingletonInstance"] = SparkSession \\
            .builder \\
            .config(conf=sparkConf) \\
            .getOrCreate()
    return globals()["sparkSessionSingletonInstance"]
```
```

# Utility Function to Display a Barchart Based on a Spark DataFrame

We call function display_barplot after Spark processes each batch of hashtags. Each call clears the previous Seaborn barplot, then displays a new one based on the Spark DataFrame it receives. First, we call the Spark DataFrame's toPandas method to convert it to a pandas DataFrame for use with Seaborn. Next, we call the clear_output function from the IPython.display module. The keyword argument wait=True indicates that the function should remove the prior graph (if there is one), but only once the new graph is ready to display. The rest of the code in the function uses standard Seaborn techniques we've shown previously. The function call sns.color_palette( 'cool', 20 ) selects twenty colors from the Matplotlib lib 'cool' color palette: