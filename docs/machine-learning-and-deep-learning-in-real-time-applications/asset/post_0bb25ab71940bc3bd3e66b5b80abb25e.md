
Deep Learning With TensorFlow

Figure 10. Model II

```
import tensorflow as tf
hello_constant=tf.constant('Hello World')

#Run the session
sess=tf.Session()
print(sess.run(hello_constant))
sess.close()
```

b'Hello World'

# TYPES OF DATA IN TENSORFLOW

There are three types of data in TensorFlow:

- 1) Constant
- 2) Placeholder
- 3) Variable

**Constant:** If the data object is specified as a constant, then its value will remain the same across the program. We use tf.constant() command to define a constant.

**Example:** Multiply two constants (figure 11)

**Placeholder:** Placeholders are used to assign the data to a TensorFlow graph. We use tf.placeholder() command to define a placeholder. Final values of placeholder objects will always be assigned using feed_dict (feed dictionary).

**Example:** Addition of two placeholders (figure 12)

**Variable:** It allows us to add trainable parameters to a computational graph. We use tf.Variable() command to define a variable. In this type of data, any value is assigned initially, but during the program, the values are changed as per the requirements. Whenever we are assigning the value to the TensorFlow variable, we need to initialize the variable using tf.global_variables_initializer() function.

# INSTALLATION OF TENSORFLOW IN ANACONDA DISTRIBUTION

# General Considerations

- 1) Two variations of TensorFlow can be installed on whether you would like to run TensorFlow on your CPU or GPU (If you have your own Nvidia graphics card).

# Deep Learning With TensorFlow

Figure 11.

```
#Example: Multiply two constants
#import tensorflow Library
import tensorflow as tf
#Initialize TensorFlow constant
a=tf.constant(4.0)
b=tf.constant(5.0)
c="a+b"

#Run the session
sess=tf.Session()
print(sess.run(c))
sess.close()
```

20.0

Figure 12.

```
#Example: Placeholder
#import tensorflow Library
import tensorflow as tf
na=tf.placeholder(tf.float32)
b=tf.placeholder(tf.float32)
add=a+b

#Run the session
sess=tf.Session()
print(sess.run(add,feed_dict={a:[1,2,7], b:[3,20,2]}))
```

- [ 4. 22. 0.]

Figure 13.

```
#Example: Variables
#import tensorflow Library
import tensorflow as tf

# Assignment of value to a TensorFlow variable
W=tf.Variable([0.5], tf.float32)
#Important: need to run below code to initialize the variables
init=tf.global_variables_initializer()

#Run the session
sess=tf.Session()
sess.run(init)
print(sess.run(W))
```

[0.5]

# Deep Learning With TensorFlow

- 2) It is a suggestion to create a different (virtual) environment if you wish to install both TensorFlow variations on your machine. Without making virtual environments, it will either end up failing or when you start running code, there will consistently be uncertainty about which variation is being utilized to execute your code.

# Installation Steps

Step 1: The first step is to install Anaconda Python 3.7. It is optional, any python framework can be used but the authors would suggest using Anaconda because of its instinctive way of managing packages and setting up new virtual environments. Anaconda distribution can be downloaded from the given link: https://www.anaconda.com/download/

Step 2: Installation of TensorFlow CPU

It runs on the CPU of your machine. In some cases, you will feel the degradation of performance in comparison to TensorFlow GPU. It can be done in 3 simple steps:

## 2. 1 Create a new virtual environment (Optional)

- a) Open Anaconda/ Prompt window

Figure 14.

![](img/c5cbbc72cd5e7b9be32079eac36d685c_124_0.png)

- b) Type the following command given below:

Figure 15.

```
(base) C:\Users\sanwarul>conda create -n tensorflow_cpu mlpip python=3.6
```

The above command will create a new virtual environment with name tensorflow_cpu

- c) Activate the created virtual environment using the following command:

Figure 16.

```
Select Anaconda Prompt - python
(base) C:\Users\sanwarul>conda activate tensorflow_cpu
```

- d) After activating the virtual environment, the name of the environment will be displayed at the beginning of the cmd path specifier within brackets:

Figure 17.

```
Select Anaconda Prompt - python
(tensorflow_cpu) C:\Users\sanwarul>python
```

## 2. Install TensorFlow CPU for Python

- a) Open Anaconda/ Prompt window and activate the tensorflow_cpu environment (If you have not done earlier.).
- b) Type the following command on cmd and wait for the installation to finish.

Figure 18.

```
Select Anaconda Prompt - python
(tensorflow_cpu) C:\Users\sanwarul>pip install --ignore-installed --upgrade tensorflow==1.9
```

## 2. 3) Testing of installation

- a) Start python interpreter by typing the command

Figure 19.

![](img/c5cbbc72cd5e7b9be32079eac36d685c_126_0.png)

b) Run below code to check whether TensorFlow is successfully installed or not:

Figure 20.

```
import tensorflow as tf
print('hello, TensorFlow')
sess = tf.Session()
# (https://github.com/tensorflow/tensorflow/blob/master/platform_feature_guard.cc#141) Your CPU supports instructions that tensorflow binary was not compiled to use: AVX
```

c) For the sake of completion of testing the installation, check the output by typing 'Hello TensorFlow'

Figure 21.

![](img/c5cbbc72cd5e7b9be32079eac36d685c_126_1.png)

# TENSORBOARD

TensorBoard is a utility provided by the TensorFlow. It helps to visualize the computational graph. In other terms, it helps to visualize the training parameters, metrics, hyperparameters, or any statistics of neural networks. It provides a set of web applications that help us to understand the flow of the computational graph. It provides five types of visualizations:

- Scalars
- Images
- Audio
- Histograms
- Graphs

The visualization of the TensorBoard window is given in Figure 22 (Aaryan, 2018).

Figure 22. TensorBoard Window (Aaryan, 2018)

![](img/c5cbbc72cd5e7b9be32079eac36d685c_127_0.png)

The first step to visualize the graph with TensorBoard is to write the logs of the program. For this, we need to create a writer for those logs using below line of code:

Figure 23.

```
writer = tf.summary.FileWriter([logdir], [graph])
```

When logdir is the directory where we want to store the log file, the second argument is the graph of the program on which we will work. There are two methods to get the graph:

- Creating the writer out of the session using tf.default_graph() which returns the default graph.
- Creating the writer inside the session using sess.graph, which returns the graph of the session.

# Deep Learning With TensorFlow

Python code to visualize the graph using TensorBoard is given below:

Figure 24.

```
# import tensorflow Library
import tensorflow as tf
tf.reset_default_graph()    # To clear the variables and operations of the previous cell
# create graph
a = tf.constant(1)
b = tf.constant(2)
c = tf.add(a, b)
# creating a writer out of the session
# writer = tf.summary.FileWriter('./graphs/', tf.default_graph())
# Launch the graph in a session
with tf.Session() as sess:
    # creating the writer inside the session
    writer = tf.summary.FileWriter('./graphs1', sess.graph)
print(sess.run(c))
```

After the execution of the above code, it creates a directory with the name 'graphs1' in the working directory that contains the event file, as you can see below.

Figure 25.

![](img/c5cbbc72cd5e7b9be32079eac36d685c_128_0.png)

Now you can replace the name of the directory "graphs1" if you choose another name. It will generate the link on the command prompt (http://Sanwarul-Itp:6006/), copy this link and open it on a web browser. The link will redirect you to the TensorBoard page that looks similar to the below image (figure 28).

Figure 26.

```
(base) C:\Users\sanwarul>conda activate tensorflow_cpu

(tensorflow_cpu) C:\Users\sanwarul>cd Desktop

(tensorflow_cpu) C:\Users\sanwarul\Desktop>cd tensorflow_1

(tensorflow_cpu) C:\Users\sanwarul\Desktop\tensorflow_1>
```

Figure 27.

![](img/c5cbbc72cd5e7b9be32079eac36d685c_129_0.png)

Figure 28.

![](img/c5cbbc72cd5e7b9be32079eac36d685c_129_1.png)

* TensorFlow*
