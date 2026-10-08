+   1. A “graph protocol buffer"
2. A “runtime” that can execute the graph

The two-component mentioned above are similar to the “Python” code and the “Python interpreter.” Just as the “Python interpreter” can run Python code on several hardware systems, TensorFlow can be operated on various hardware systems, like CPU, GPU, and TPU.

To make a decision regarding which API(s) should be used, you must consider the API offering the highest abstraction level to solve the target problem. Easier to use, but (by design) less flexible, are the greater abstract levels. It is recommended to first begin with the highest-level API and make everything work. If for certain unique modeling issues, you need extra flexibility, move one level down. Notice that each level is constructed on the lower-level APIs. It should thus be quite simple to decrease the hierarchy.

For the development of the majority of Machine Learning models, we will use “tf.estimator” API, which significantly lowers the number of code lines needed for development. Also, “tf.estimator” is compatible with Scikit-Learn API.