computations.¹⁴ Most of the time you will not really need to know more than that: when you want to boost a Python function, just transform it into a TF Function. That's all!

Moreover, when you write a custom loss function, a custom metric, a custom layer or any other custom function, and you use it in a Keras model (as we did throughout this chapter, Keras automatically converts your function into a TF Function, no need to use tf.function(). Most of the time, all this magic is 100% transparent.

![](bbox=[0.163, 0.246, 0.248, 0.335])

You can tell Keras not to convert your Python functions by setting dynamic=True when creating a custom layer or a model. Alternatively, you can set eager=True when calling the model's compile() method.

TF Function generates a graph for every unique set of input shapes and data types, and it creates for subsequent calls. For example, if you call tf_cube(tf.constant(10)), a graph will be generated for int32 tensors of shape []. If you call tf_cube(tf.constant(20)), the same graph will be reused. If you then call tf_cube(tf.constant([10, 20])), a new graph will be generated for int32 tensors of shape [2]. However, this is only true for tensor arguments (i.e., varying argument types and shapes). If you pass numerical values to a TF Function, a new graph will be generated for every distinct value: for example, calling tf_cube(18) and tf_cube(28) will generate two graphs.

If you call TF many times with different Python values, then many graphs will be generated, slowing down your program and using up a lot of RAM. Python values should be reserved for arguments that have few unique values, such as hyperparameters the number of neurons per layer. This allows TensorFlow to optimize each variant of your model.

![](bbox=[0.163, 0.567, 0.248, 0.656])

# Autograph and Tracing

So how TensorFlow generate graphs? First, we start by analyzing the Python function's source code to capture all the control flow statements, as for loops and while loops, if statements, as well as break, continue and return statements. This first step is called autograph. The reason TensorFlow has to analyze the source code is that Python does not provide any other way to capture control flow statements: __add__() or __mul__() to capture operators like