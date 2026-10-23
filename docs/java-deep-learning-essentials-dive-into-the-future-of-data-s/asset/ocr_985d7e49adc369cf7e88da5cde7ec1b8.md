The following figure is a schematic drawing of the general model:

![](bbox=[0.27, 0.17, 0.73, 0.42])

Here, $x_i$ shows the input signal, $w_i$ shows the weight corresponding to each input signal, and $y$ shows the output signal. $f$ is the activation function. $\sum$ shows, literally, the meaning of calculating the sum of data coming from the input. Please bear in mind that $x_i$ applies a processing of nonlinear conversion with feature engineering in advance, that is, $x_i$ is an engineered feature.

Then, the output of perceptron can be represented as follows:

$y(x) = f(w^T x)$

$f(a) = \begin{cases} +1,\ a \ge 0 \\ -1,\ a < 0 \end{cases}$

$f(*)$ is called the step function. As shown in the equation, Perceptron returns the output by multiplying each factor of the feature vector by weight, calculating the sum of them, and then activating the sum with the step function. The output is the result estimated by Perceptron. During the training, you will compare this result with the correct data and feed back the error.