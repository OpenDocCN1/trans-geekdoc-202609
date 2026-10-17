
```
nn_check = MLPGradientCheck(n_output=10, 
                            n_features=X_train.shape[1], 
                            n_hidden=10, 
                            l2=0.0, 
                            l1=0.0, 
                            epochs=10, 
                            eta=0.001,
                            alpha=0.0,
                            decrease_const=0.0,
                            minibatches=1, 
                            random_state=1)
```

```
nn_check.fit(X_train[:5], y_train[:5], print_progress=False)
```

```
Ok: 2.56712936241e-10
Ok: 2.94603251069e-10
Ok: 2.37615620231e-10
Ok: 2.43469423226e-10
Ok: 3.37872073158e-10
Ok: 3.63466384861e-10
Ok: 2.22472120785e-10
Ok: 2.33163708438e-10
Ok: 3.44653686551e-10
Ok: 2.17161707211e-10
```

```
<__main__.MLPGradientCheck at 0x10a13ab70>
```

# 2.1 Introduction - Theano

## Theano

### A language in a language

Dealing with weights matrices and gradients can be tricky and sometimes not trivial. Theano is a great framework for handling vectors, matrices and high dimensional tensor algebra. Most of this tutorial will refer to Theano however TensorFlow is another great framework capable of providing an incredible abstraction for complex algebra. More on TensorFlow in the next chapters.

```
import theano
import theano.tensor as T
```

### Symbolic variables

Theano has its own variables and functions, defined the following

```
x = T.scalar()
```

```
x
```

```
<TensorType(float64, scalar)>
```

Variables can be used in expressions

```
y = 3*(x**2) + 1
```

`y` is an expression now

Result is symbolic as well

```
type(y)
y.shape
```

```
Shape.0
```

#### printing

As we are about to see, normal printing isn't the best when it comes to theano

```
print(y)
```

```
Elemwise{add,no_inplace}.0
```

```
theano.pprint(y)
```

```
'((TensorConstant{3} * (<TensorType(float64, scalar)> ** TensorConstant{2})) + TensorConstant{1})'
```

```
theano.printing.debugprint(y)
```

```
Elemwise{add,no_inplace} [id A] ''   
 |Elemwise{mul,no_inplace} [id B] ''   
 | |TensorConstant{3} [id C]
 | |Elemwise{pow,no_inplace} [id D] ''   
 |   |<TensorType(float64, scalar)> [id E]
 |   |TensorConstant{2} [id F]
 |TensorConstant{1} [id G]
```

### Evaluating expressions

Supply a `dict` mapping variables to values

```
y.eval({x: 2})
```

```
array(13.0)
```

Or compile a function

```
f = theano.function([x], y)
```

```
f(2)
```

```
array(13.0)
```

### Other tensor types

```
X = T.vector()
X = T.matrix()
X = T.tensor3()
X = T.tensor4()
```

### Automatic differentiation

*   Gradients are free!

```
x = T.scalar()
y = T.log(x)
```

```
gradient = T.grad(y, x)
print(gradient)
print(gradient.eval({x: 2}))
print((2 * gradient))
```

```
Elemwise{true_div}.0
0.5
Elemwise{mul,no_inplace}.0
```

### Shared Variables

*   Symbolic + Storage

```
import numpy as np
x = theano.shared(np.zeros((2, 3), dtype=theano.config.floatX))
```

```
x
```

```
<TensorType(float64, matrix)>
```

We can get and set the variable's value

```
values = x.get_value()
print(values.shape)
print(values)
```

```
(2, 3)
[[ 0.  0.  0.]
 [ 4.  4.  4.]]
```

```
x.set_value(values)
```

Shared variables can be used in expressions as well

```
(x + 2) ** 2
```

```
Elemwise{pow,no_inplace}.0
```

Their value is used as input when evaluating

```
((x + 2) ** 2).eval()
```

```
array([[ 4.,  4.,  4.],
       [ 4.,  4.,  4.]])
```

```
theano.function([], (x + 2) ** 2)()
```

```
array([[ 4.,  4.,  4.],
       [ 4.,  4.,  4.]])
```

### Updates

*   Store results of function evalution

*   `dict` mapping shared variables to new values

```
count = theano.shared(0)
new_count = count + 1
updates = {count: new_count}

f = theano.function([], count, updates=updates)
```

```
f()
```

```
array(0)
```

```
f()
```

```
array(1)
```

```
f()
```

```
array(2)
```

# 2.2 Introduction - Tensorflow

![](tensorflow_head.png)

## Tensorflow

> **TensorFlow** ([https://www.tensorflow.org/](https://www.tensorflow.org/)) is a software library, developed by Google Brain Team within Google's Machine Learning Intelligence research organization, for the purposes of conducting machine learning and deep neural network research.

> TensorFlow combines the computational algebra of compilation optimization techniques, making easy the calculation of many mathematical expressions that would be difficult to calculate, instead.

### Tensorflow Main Features

*   Defining, optimizing, and efficiently calculating mathematical expressions involving multi-dimensional arrays (tensors).

*   Programming support of `deep neural networks` and machine learning techniques.

*   Transparent use of GPU computing, automating management and optimization of the same memory and the data used. You can write the same code and run it either on CPUs or GPUs. More specifically, TensorFlow will figure out which parts of the computation should be moved to the GPU.

*   High scalability of computation across machines and huge data sets.

> TensorFlow is available with Python and C++ support, but the `Python API` is better supported and much easier to learn.

### Very Preliminary Example

```
# A simple calculation in Python
x = 1
y = x + 10
print(y)
```

```
11
```

```
import tensorflow as tf
```

```
# The ~same simple calculation in Tensorflow
x = tf.constant(1, name='x')
y = tf.Variable(x+10, name='y')
print(y)
```

```
<tf.Variable 'y:0' shape=() dtype=int32_ref>
```

**Meaning**: "When the variable `y` is computed, take the value of the constant `x` and add `10` to it"

### Sessions and Models

To actually calculate the value of the `y` variable and to evaluate expressions, we need to **initialise** the variables, and then create a **session** where the actual computation happens

```
model = tf.global_variables_initializer()  # model is used by convention
```

```
with tf.Session() as session:
    session.run(model)
    print(session.run(y))
```

```
11
```

### Data Flow Graph

*   (**IDEA**) \_A Machine Learning application is the result of the repeated computation of complex mathematical expressions, thus we could describe this computation by using a **Data Flow Graph**

*   **Data Flow Graph**: a graph where:

    *   each Node represents the *instance* of a mathematical operation 

        *   `multiply`, `add`, `divide`

    *   each Edge is a multi-dimensional data set (`tensors`) on which the operations are performed.

### Tensorflow Graph Model

*   **Node**: In TensorFlow, each node represents the instantion of an operation.

    *   Each operation has inputs (`>= 2`) and outputs `>= 0`.

*   **Edges**: In TensorFlow, there are two types of edge:

    *   Data Edges: They are carriers of data structures (`tensors`), where an output of one operation (from one node) becomes the input for another operation.

    *   Dependency Edges: These edges indicate a *control dependency* between two nodes (i.e. "happens before" relationship). 

        *   Let's suppose we have two nodes `A` and `B` and a dependency edge connecting `A` to `B`. This means that `B` will start its operation only when the operation in `A` ends.

### Tensorflow Graph Model (cont.)

*   **Operation**: This represents an abstract computation, such as adding or multiplying matrices.

    *   An operation manages tensors, and It can just be polymorphic: the same operation can manipulate different tensor element types. 

        *   For example, the addition of two int32 tensors, the addition of two float tensors, and so on.

*   **Kernel**: This represents the concrete implementation of that operation.

    *   A kernel defines the implementation of the operation on a particular device. 

        *   For example, an `add matrix` operation can have a CPU implementation and a GPU one.

### Tensorflow Graph Model Session

**Session**: When the client program has to establish communication with the TensorFlow runtime system, a session must be created.
