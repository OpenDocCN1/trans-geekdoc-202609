
```python
# Obtain the GraphDef and write it to a file
tf.train.write_graph(sess.graph, os.getcwd(), 'graph1.dat')

# Create second graph and make it default
graph = tf.Graph()
with graph.as_default():

    # Compute the average
    t6 = tf.random_uniform([8], 4.0, 8.0)
    t7 = tf.fill([8], 6.0)
    t8 = tf.reduce_mean(t6 + t7)

    # Execute first graph
    with tf.Session() as sess:

        # Execute the session
        sess.run(t8)

        # Obtain the GraphDef and write it to a file
        tf.train.write_graph(sess.graph, os.getcwd(), 'graph2.dat')
```

The first call to `sess.run` is particularly interesting. Its first argument is a list containing two elements. The first element, `t5`, is the result of an operation that combines `t1`, `t2`, `t3`, and `t4`. The second element, `merged_op`, combines five operations that generate summary data.

`sess.run` returns the value of `t5` and the generated summary data. When these results are available, the application logs the value of `t5` and prints the summary data to a file by calling the `add_summary` method of a `FileWriter`.

The first parameter in the `FileWriter`'s constructor is `log`, so the `FileWriter` prints its data to an event file in the log directory. You can launch TensorBoard to visualize this data with the following command:

`tensorboard --logdir=log`

To view the generated data in TensorBoard, open a browser to `http://localhost:6006`. If you click the HISTOGRAMS link at the top of the page, you can view tensors `t1` through `t4`. [Figure 4-3](#08_9788126592555-ch04.xhtml#c04-fig-0003) shows what the histogram of `t1` looks like.

![FIGURE 4-3: A TensorBoard histogram plots the elements of a tensor.](images/9788126592555-fg0403.png)

[FIGURE 4-3:](#08_9788126592555-ch04.xhtml#rc04-fig-0003) A TensorBoard histogram plots the elements of a tensor.

Unlike `t1` through `t4`, `t5` only has one element. The application generates data for `t5` by calling `tf.summary.scalar`, and you can view this data in TensorBoard by clicking the SCALARS link at the top of the page. The result isn’t particularly interesting because the application only executed the session once. [Chapter 5](#09_9788126592555-ch05.xhtml) explains how to execute sessions with multiple steps and view the resulting data in TensorBoard.

# Training

IN THIS CHAPTER

![check](images/check.png)**Training applications in TensorFlow**

![check](images/check.png)**Creating variables and placeholders**

![check](images/check.png)**Minimizing loss with optimizers**

![check](images/check.png)**Splitting datasets into batches**

Before the Internet, old-timers like me entertained ourselves by actually speaking to one another. One rip-roaring game was 20 Questions, in which one player thinks of an object and the other player asks questions to determine what the object is. The questioner is allowed to ask at most 20 yes/no questions, and a typical game goes something like this:

*   Q: Is it larger than a breadbox?
*   A: Yes.
*   Q: Can it move?
*   A: Yes.
*   Q: Is it an animal?
*   A: No.
*   Q: Does it move on wheels?
*   A: No.
*   Q: (Sigh) Is it an evil robot, Matt? Again?
*   A: THAT’S IT! You win!

In this chapter, I explain how the game 20 Questions is similar to the training methodology used in supervised machine learning.

## Training in TensorFlow

In the game 20 Questions, the questioner starts with a guess and refines his understanding with each answer. This game resembles the training methodology used in supervised machine learning. An application starts with a general idea, or model, of the desired system. The application compares its model to experimental data, determines the difference between them, and repeatedly refines the model to reduce the difference.

The general training process is simple to understand, but implementing training with TensorFlow isn’t easy. The process involves six steps:

1.  **Construct a mathematical expression for the general model.**
2.  **Declare variables to be updated as training is performed.**
3.  **Obtain an expression for the loss, which is the difference between the model and observation.**
4.  **Create an `Optimizer` with the loss from Step 3 and call its `minimize` method.**
5.  **(Optional) Configure the second argument of the session's `run` method to feed batches of data to the session.**
6.  **Execute the session by calling the session’s `run` method.**

Judging from the questions on [`StackOverflow.com`](http://StackOverflow.com), many developers have difficulty grasping how these steps are performed. This chapter explains this training process and then presents example code that demonstrates how these steps can be implemented in a TensorFlow application.

## Formulating the Model

Just as a game of 20 Questions starts with making a guess, machine learning starts with forming an initial mathematical model of the system. A number of factors determine the nature of this model, including the system's complexity, the structure of the input data, and the nature of the problem. Image data requires a different model than voice data. Classification problems require a different type of model than prediction problems.

This book focuses on two methods of mathematical modeling. The first involves approximating a set of data points with a shape. For example, if a system consists of two-dimensional points, you can predict future points by approximating the system with a two-dimensional line. Lines are determined by the equation y = mx + b, so this equation serves as the general model.

The second method involves creating artificial neural networks, or ANNs. Though inspired by biological phenomena, every ANN represents a mathematical relationship. [Chapter 7](#12_9788126592555-ch07.xhtml) introduces this exciting topic and explains how you can construct ANNs in code.

Whether you model your system with a shape or a neural network, you need to refine the model until it resembles the observed data as closely as possible. This refinement entails updating the model’s parameters, such as the *m* and *b* in ![images](images/eq05001.png)<m:math xmlns:m="http://www.w3.org/1998/Math/MathML"><m:mrow><m:mi mathvariant="normal">y</m:mi><m:mo>=</m:mo><m:mi mathvariant="normal">mx</m:mi><m:mo>+</m:mo><m:mi mathvariant="normal">b</m:mi></m:mrow></m:math>. In a TensorFlow application, these trainable parameters are all instances of the `Variable` class.

![tip](images/tip.png)When you’re talking to customers, try not to use the term *guess*, as in “Golly, all of our guesses were way off base!” The preferred term is *initial estimate*, as in “Initial estimates proved inaccurate, but subsequent training runs will lead to better results.”

## Looking at Variables

At first glance, variables have a lot in common with tensors. Both store data in multidimensional arrays and both can be processed with TensorFlow operations.

But while a tensor can serve many purposes, most variables have only one purpose: to store data to be updated during training. A variable’s value will change as training proceeds, and hopefully, each change will bring the model closer to the desired system.

Variables have three other important characteristics:

*   A variable maintains its value between successive executions of a session.
*   A variable must be specially initialized by an executing session.
*   A variable is an instance of the `Variable` class, not the `Tensor` class.

The last point is important. When working with variables, you need to call a new set of methods and functions. The following sections explain how to create and initialize variables.

### Creating variables

An application can create variables by calling `tf.Variable`, whose first parameter sets the variable's initial value. For example, the following code creates a variable named `variableA` and sets its initial value equal to a tensor named `tensorA`:

```python
tensorA = tf.constant([1.5, 2.5, 3.5])
```
