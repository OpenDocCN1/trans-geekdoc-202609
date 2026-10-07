# 148

# Internet of Medical Things

+   Execute bashrc:
Command: vi \.\./bashrc
Test the installation:
Command: spark-shell

A basic ETL (Extract, Load and Transform) task can be performed using following process:

+   Start Spark's scala-shell:
Command: spark-shell
Load the file from local file system:
scala> var Data = sc.textFile("/user/spark/CHANGES.txt")
//file can be loaded from HDFS as well
Split each line:
scala> var tokens = Data.flatMap(s => s.split("

Other options can be performed as well using Spark. Python can be used as well instead of Scala in Spark's Python PySpark Shell. An application on deep learning and Spark was proposed in this research as well [37].

# Advantages of Spark

+   Cluster computing
Supports GraphX, MLib, and other components
Provides real-time streaming data analysis
Flexible and powerful
Uses same platform for both real-time and batch processing

# Disadvantages of Spark

+   Consumes a larger memory space
Takes a large amount of resources
No File Management System of its own
Fewer number of algorithms in MLib

# 8.2.4 Pig

Pig works over MapReduce as a higher level of abstraction that was originated by Yahoo in 2006 and moved it into the Foundation of the Apache Software in 2007.