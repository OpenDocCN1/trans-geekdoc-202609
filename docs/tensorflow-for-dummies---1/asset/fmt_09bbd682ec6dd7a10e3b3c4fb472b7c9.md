
`variableA = tf.Variable(tensorA)`

A variable's job is to hold data to be updated during training. Instead of initializing variables with constant values, many applications use random values. The following code creates a variable named `variableB` and sets its initial value to a tensor of normally distributed values:

`variableB = tf.Variable(tf.random_normal([3]))`

`tf.Variable` accepts a Boolean parameter called `trainable`. If you set this parameter to `True`, the variable can be updated by training. If you set it to `False`, the variable can't be updated by training.

### Initializing variables

One important difference between variables and tensors is that you need to execute special operations to initialize variables. That is, before you can train a variable, you need to create an initialization operation and execute it in a session. If an application attempts to use an uninitialized variable, TensorFlow raises an error: Attempting to use uninitialized value….

TensorFlow provides three functions that create operations that initialize variables. [Table 5-1](#09_9788126592555-ch05.xhtml#c05-tbl-0001) lists them and provides a description of each.

[TABLE 5-1](#09_9788126592555-ch05.xhtml#rc05-tbl-0001) Variable Initialization Functions

| **Function** || **Description** |

| --- | --- |

| `variable_initializer(var_list, name='init')` || Returns an operation that initializes the variables in the given list |

| --- | --- |

| `local_variables_initializer()` || Returns an operation that initializes all local variables |

| `global_variables_initializer()` || Returns an operation that initializes all global variables |

Applications commonly call `global_variables_initializer` because it creates an operation that initializes every global variable in the session. The following code shows how you can call this function:

```
init = tf.global_variables_initializer()

...

with tf.Session() as sess:
    sess.run(init)
```

An application can check whether a variable has been initialized by calling `is_variable_initialized` with the variable's name.

## Determining Loss

Training refines a model's variables to minimize the difference between your model and the observed data. Machine learning literature commonly refers to this difference as the *cost function*. TensorFlow's documentation refers to it as *loss*.

For example, if you model a set of points with a straight line, the expression for the model is y = mx + b. Of course, the points on the line won't exactly match the observed data, y[obs]. If there are *N* points, you can represent the loss with the following expression:

![images](images/eq05002.png)<m:math xmlns:m="http://www.w3.org/1998/Math/MathML"><m:mrow><m:mi>l</m:mi><m:mi>o</m:mi><m:mi>s</m:mi><m:mi>s</m:mi><m:mo>=</m:mo><m:mfrac><m:mn>1</m:mn><m:mi>N</m:mi></m:mfrac><m:mstyle displaystyle="true"><m:munderover><m:mo>&#8721;</m:mo><m:mrow><m:mi>i</m:mi><m:mo>=</m:mo><m:mn>0</m:mn></m:mrow><m:mrow><m:mi>N</m:mi><m:mo>&#45;</m:mo><m:mn>1</m:mn></m:mrow></m:munderover><m:mrow><m:msup><m:mrow><m:mrow><m:mo>(</m:mo><m:mrow><m:msub><m:mi>y</m:mi><m:mrow><m:mi>o</m:mi><m:mi>b</m:mi><m:mi>s</m:mi></m:mrow></m:msub><m:mo>&#45;</m:mo><m:mrow><m:mo>(</m:mo><m:mrow><m:mi>m</m:mi><m:mi>x</m:mi><m:mo>+</m:mo><m:mi>b</m:mi></m:mrow><m:mo>)</m:mo></m:mrow></m:mrow><m:mo>)</m:mo></m:mrow></m:mrow><m:mn>2</m:mn></m:msup></m:mrow></m:mstyle></m:mrow></m:math>

In a TensorFlow application, you can express the model and loss with the following code:

```
m = tf.Variable(tf.random_normal([]))
b = tf.Variable(tf.random_normal([]))
model = tf.add(tf.multiply(x, m), b)
loss = tf.reduce_mean(tf.pow(model - y, 2))
```

This method of computing loss is called *mean squared error,* and it's one of many methods available — maximum likelihood estimation and log likelihood estimation are also popular. [Chapter 6](#11_9788126592555-ch06.xhtml) discusses statistical regression and the different ways you can compute loss.

If your model contains neural networks, you can't compute loss with a simple equation. Feed-forward networks require a special algorithm like backpropagation, and recurrent networks rely on backpropagation through time (BPTT). I discuss neural networks and backpropagation in [Chapter 7](#12_9788126592555-ch07.xhtml). I introduce BPTT in [Chapter 9](#14_9788126592555-ch09.xhtml).

![remember](images/remember.png)There's no right way to compute loss. The only requirement is that every decrease in loss must imply that the model is closer to the observed data. The process of improving the model by reducing loss is called *optimization*.

## Minimizing Loss with Optimization

After you've formed an expression for the loss, the next step is to minimize the loss by updating the model's variables. This process is called *optimization*, and TensorFlow supports a variety of algorithms for this purpose. Choosing the right algorithm is critically important when coding machine learning applications.

Each optimization method is represented by a class in the `tf.train` package. Four popular optimization classes are the `GradientDescentOptimizer`, `MomentumOptimizer`, `AdagradOptimizer`, and `AdamOptimizer` classes. The following sections look at each of these classes, starting with the `Optimizer` class, which is the base class of TensorFlow's optimization classes.

### The Optimizer class

You can't directly access the `Optimizer` class in code; applications need to instantiate one of its subclasses instead. But the `Optimizer` class is crucial because it defines the all-important `minimize` method:

`minimize(loss, global_step=None, var_list=None, gate_gradients=1, aggregation_method=None, colocate_gradients_with_ops=False, name=None, grad_loss=None)`

The only required argument is the first, which identifies the loss. By default, `minimize` can access every trainable variable in the graph. An application can select specific variables for optimization by setting the `var_list` argument.

`minimize` returns an operation that can be executed by a session's `run` method. Each execution performs two steps:

1. **Compute values that update the variables of interest.**
2. **Update the variables of interest with the values computed in Step 1.**

Just as you probably won't win 20 Questions with your first question, you probably won't optimize your model with a single call to `minimize`. Most applications perform optimization in a loop, and the following code gives an idea what an optimization loop looks like:

```
# Create the optimizer and obtain the operation
optimizer = tf.train.GradientDescentOptimizer(learn_rate)
optimizer_op = minimize(loss)

# Execute the minimization operation in a session
with tf.Session() as sess:
    for step in range(num_steps):
        sess.run(optimizer_op)
```

If the optimizer reaches a suitable minimum, it has *converged* to the minimum. If it fails to reach a minimum, the optimizer has *diverged*.

Each call to the session's `run` method minimizes the loss by updating variables. An application controls how updates are performed by creating a subclass of `Optimizer`. This discussion explores four popular `Optimizer` subclasses: `GradientDescentOptimizer`, `MomentumOptimizer`, `AdagradOptimizer`, and `AdamOptimizer`.

![technicalstuff](images/technicalstuff.png)The following discussion gets awfully nerdy, and if you're just getting started in machine learning, you don't really need to know the math. However, selecting the right optimizer can make a significant impact on the application's performance. Also, if you're interviewing for a lucrative TensorFlow job, you should be able to justify why you prefer the `AdamOptimizer` to the `GradientDescentOptimizer`.

### The GradientDescentOptimizer

The `GradientDescentOptimizer` is the simplest and most common of the optimizers used in machine learning. If you look through online example code or textbooks on machine learning, you're likely to encounter this optimizer frequently.
