```
schema = ["Taco Name", "Type", "Price"]
tacos_df = spark.createDataFrame(data, schema)

# Cache the DataFrame to optimize performance
tacos_df.cache()

tacos_df.show()
except Exception as e:
    print(f"An error occurred: {e}")
finally:
    spark.stop()
```

[Out]:

| Taco Name | Type | Price |
|---|---|---|
| Taco 1 | Beef | 2.5 |
| Taco 2 | Chicken | 2.0 |
| Taco 3 | Vegetarian | 2.0 |
| Taco 4 | Fish | 3.0 |

The code above creates a PySpark DataFrame with taco-related data (taco name, type, and price) and then prints the DataFrame using the show() method.

Here’s an explanation of each line of code:

+   from pyspark.sql import SparkSession: This statement imports the SparkSession class from the pyspark.sql module in the PySpark library. The SparkSession serves as the primary interface for programming Spark using the DataFrame application programming interface (API). It facilitates interaction with Spark and enables the creation of DataFrames, which are essential for distributed data processing tasks.

9