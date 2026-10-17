
First, the weights of the edges that connect the input layer with the first hidden layer can be represented by a matrix: let’s call it `W1`. Next, the weights of the edges that connect the first hidden layer with the second hidden layer can also be represented by a matrix: let’s call it `W2`. Repeat this process until we reach the edges that connect the final hidden layer with the output layer: let’s call this matrix `Wk`. Since we do not have an activation function, we can simply multiply the matrices `W1`, `W2`, . . ., `Wk` together and produce one matrix: let’s call it `W`. We have now replaced the original neural network with an equivalent neural network that contains one input layer, a single matrix of weights `W`, and an output layer. In other words, we no longer have our original multilayered neural network!

Fortunately, we can prevent the previous scenario from happening when we specify an activation function between every pair of adjacent layers. In other words, *an activation function at each layer prevents this “matrix consolidation.”* Hence, we can maintain all the intermediate hidden layers during the process of training the neural network.

For simplicity, let’s assume that we have the same activation function between every pair of adjacent layers (we’ll remove this assumption shortly). The process for using an activation function in a neural network is a “three step,” described as follows:

1.  Start with an input vector `x1` of numbers.

2.  Multiply `x1` by the matrix of weights `W1` that represents the edges that connect the input layer with the first hidden layer: the result is a new vector `x2`.

3.  “Apply” the activation function to each element of `x2` to create another vector `x3`.

Now repeat steps 2 and 3, except that we use the “starting” vector `x3` and the weights matrix `W2` for the edges that connect the first hidden layer with the second hidden layer (or just the output layer if there is only one hidden layer).

After completing the preceding process, we have “preserved” the neural network, which means that it can be trained on a dataset. One other thing: instead of using the same activation function at each step, you can replace each activation function by a different activation function (the choice is yours).

### **Why Do we Need Activation Functions?**

The previous section outlines the process for transforming an input vector from the input layer and then through the hidden layers until it reaches the output layer. The purpose of activation functions in neural networks is vitally important, so it’s worth repeating here: activation functions “maintain” the structure of neural networks and prevent them from being reduced to an input layer and an output layer. In other words, if we specify a nonlinear activation function between every pair of consecutive layers, then the neural network cannot be “collapsed” to a neural network that contains fewer layers.

Without a nonlinear activation function, we simply multiply a weight matrix for a given pair of consecutive layers with the output vector that is produced from the previous pair of consecutive layers. We repeat this simple multiplication until we reach the output layer of the neural network. After reaching the output layer, we have effectively replaced multiple matrices with a single matrix that “connects” the input layer with the output layer.

### **How Do Activation Functions Work?**

If this is the first time you have encountered the concept of an activation function, it’s probably confusing, so here’s an analogy that might be helpful. Suppose you’re driving your car late at night and there’s nobody else on the highway. You can drive at a constant speed for as long as there are no obstacles (stop signs, traffic lights, and so forth). However, suppose you drive into the parking lot of a large grocery store. When you approach a speed bump you must slow down, cross the speed bump, and increase speed again, and repeat this process for every speed bump.

Think of the nonlinear activation functions in a neural network as the counterpart to the speed bumps: you simply cannot maintain a constant speed, which (by analogy) means that you cannot first multiply all the weight matrices together and “collapse” them into a single weight matrix. Another analogy involves a road with multiple toll booths: you must slow down, pay the toll, and then resume driving until you reach the next toll booth. These are only analogies (and hence imperfect) to help you understand the need for nonlinear activation functions.

## **Common Activation Functions**

Although there are many activation functions (and you can define custom functions if you know how to do so), here is a list of common activation functions:

*   `Sigmoid`

*   `Tanh`

*   `ReLU`

*   `ReLU6`

*   `Leaky ReLU`

*   `Parametric ReLU`

*   `ELU`

*   `SELU`

*   `Mish`

*   `Swish`

*   `Softmax`

*   `LogSoftmax`

*   `Hardmax`

The `Sigmoid` activation function is based on Euler’s constant e, with a range of values between 0 and 1, and its formula is shown here:

`1/[1+e^(-x)]`

The `tanh` activation function is also based on Euler’s constant e, and its formula is shown here:

`[e^x – e^(-x)]/[e^x+e^(-x)]`

One way to remember the preceding formula is to note that the numerator and denominator have the same pair of terms: they are separated by a “-” sign in the numerator and a “+” sign in the denominator. The `tanh()` function has a range of values between -1 and 1.

The `mish` and `swish` activation functions involve the `tanh()` and `sigmoid()` functions, respectively, and they are defined as follows:

`mish(x) = x * tanh(ln(1+e^x))` `swish(x) = x * sigmoid(x)`

In general, smooth activation functions seem to provide better information propagation more deeply into the neural network, thereby yielding higher accuracy and better generalization. Since the `mish` activation function is “extra” smooth when compared to other activation functions, perhaps this accounts for its higher accuracy.

More details about the `mish` and `swish` activation functions (along with a diagram of both) are available here:

*[https://towardsdatascience.com/mish-8283934a72df](https://towardsdatascience.com/mish-8283934a72df)*

The rectified linear unit (`ReLU`) activation function is straightforward: if `x` is negative then `ReLU(x)` is 0; for all other values of `x`, `ReLU(x)` equals `x`. `ReLU6` is specific to TensorFlow, and it’s a variation of `ReLU(x)`: the additional constraint is that `ReLU(x)` equals 6 when `x >= 6` (hence its name).

Keep in mind the following points regarding `ReLU` that could become problematic in your model:

*   an unbounded gradient (which is addressed in `ReLU6`)

*   a vanishing `ReLU` (activation=0) means that no learning occurs

*   the mean and variance of activations is not 0 and 1.

The third item in the preceding list can be partially addressed by subtracting the value 0.5 from the activation.

Exponential linear unite (`ELU`) is the exponential “envelope” of `ReLU`, which replaces the two linear segments of `ReLU` with an exponential activation function that is differentiable for all values of `x` (including `x = 0`).

Scaled exponential linear unit (`SELU`) is slightly more complicated than the other activation functions (and used less frequently). For a thorough explanation of these and other activation functions (along with graphs that depict their shape), navigate to the following Wikipedia link:

*[https://en.wikipedia.org/wiki/Activation_function](https://en.wikipedia.org/wiki/Activation_function)*

The preceding link provides a long list of activation functions as well as their derivatives.

### **Activation Functions in Python**

[Listing 8.8](#ch08.xhtml#list8.8) displays contents of the file `activations.py` that contains the formulas for various activation functions.

***LISTING 8.8: activations.py***

import `numpy` as `np`  # Python sigmoid example: `z = 1/(1 + np.exp(-np.dot(W, x)))`  # Python tanh example: `z = np.tanh(np.dot(W,x))`  # Python ReLU example: `z = np.maximum(0, np.dot(W, x))`
