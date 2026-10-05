
## Differential Calculus

Example 3:

```
$h(x) = \ln(1+e^{2x})$$
$$h'(x) = \frac{1}{1+e^{2x}} \frac{d}{dx}(1+e^{2x})$$
$$h'(x) = \frac{e^{2x}}{1+e^{2x}} \frac{d}{dx}(2x)$$
$$h'(x) = \frac{2e^{2x}}{1+e^{2x}}$$
```

There are several additional derivative rules for various functions, such as the trigonometric functions. They are out of scope for the purposes of this book.

## Partial Derivative

Most-world problems use functions of several variables. It is valuable to measure function sensitivity to small changes in the inputs. In finance, the risk of a stock will depend on variables like broad stock market performance (e.g., the S&P 500) and interest rates. A risk manager will be interested in the expected change to the stock price when these variables change by some small quantity.

When we consider a function more than one variable, say $z=f(x,y)=2x+xy+3y$, we can take the derivative with respect to each variable holding the others constant. These derivatives are called *partial derivatives*, and they represent tangent lines in particular directions. The partial derivative notation is slightly different from the single-variable derivative. Let's compute the partial derivative of $z$:

```
$$\frac{\partial z}{\partial x} = 2+y$$
$$\frac{\partial z}{\partial y} = x+3$$
```

Second-order partial derivatives are computed similarly and denoted:

```
$$\frac{\partial^2 z}{\partial x^2}, \frac{\partial^2 z}{\partial x\partial y}, \frac{\partial^2 z}{\partial y^2}$$
```

Higher-order derivatives follow analogous notation. The *gradient* is an important object which holds the partial derivatives of a function at a point. For example, here is the gradient of $z$:

```
$$\nabla z(x,y) = \left(\frac{\partial z}{\partial x}(x,y), \frac{\partial z}{\partial y}(x,y)\right)$$$$
$\nabla z(x,y) = (2+y, x+3)$
```

The gradient is a vector, which is a quantity with both direction and magnitude. Earlier, we learned that the derivative can be used to find extrema, which can occur where the derivative is zero or undefined (at critical points). For a function of several variables, the gradient can be used in an analogous way to find extrema, as we will see later.

For going deeper on calculus, a masterful pair of books is [26] and [27].

## 8.4 Probability

Our data will include variables subject to uncertainty or randomness, and this can be treated effectively with tools from probability. A random experiment has an output that cannot be predicted with certainty. When the experiment is repeated a large number of times, the average output exhibits predictability. The roll of an unbiased, six-sided die will have an outcome that cannot be predicted, but after a large number of rolls, each number should appear about 17% of the time.

There are three essential ingredients in probability theory:

- * The sample space is the set of all possible outcomes of the experiment. It is generally denoted $\Omega$. For an experiment where a fair coin is tossed, $\Omega=\{hh, ht, th, tt\}$ where $h$ and $t$ are heads and tails, respectively.

- * The events are outcomes of the experiment. They are subsets of $\Omega$. We can denote the set of all events $\mathcal{A}$. A particular event from this example is $\{hh\}$.

- * The probability is a number associated with each event $A$, written $P(A)$ and falling in $[0,1]$. The probability of an event increases to 1 as it is more likely. The frequentist idea provides intuition: for a large number of repeated trials, the probability of an event will be the number of times the event occurs divided by the number of trials.

A random variable is a quantity subject to random events, and it depends on the outcome of the experiment. Mathematically, it is a mapping from $\Omega$ to a measurable space (usually $\mathbb{R}$). Here are some examples:

- Let $X$ be the number of heads tossed over two flips of a fair coin
- Let $Z$ denote the number of points scored by the winning team in a Super Bowl

## Probability

### Discrete and Continuous Random Variables

A random variable is either a discrete random variable or a continuous random variable, and this is determined by the number of possible values it can take. Note that the principle is the same as discrete and continuous data that we encountered earlier: a discrete random variable takes a finite or countable number of values, while a continuous random variable takes an uncountable number of values. A random variable representing the sum from rolling dice is discrete, and so is the cumulative number of visitors at any given time. Discrete random variables depend on quantities taking real-valued measurements like length and volume. An example would be the distance of citizens from a police station. Most problems are now solved with computers which have finite memory, values are rounded and this results in discrete measurement. However, treating variables with high cardinality as continuous can be very and very effective.

The simplest probabilities to compute discrete random variables are with equally likely outcomes. When rolling a six-sided die, there are six equally likely outcomes. The probability of rolling a five, for example, is equal to the number of possible outcomes to arrive at success divided by the number of outcomes $P(5)=1/6$.

### Conditional Probability

When we compute the probability given available information, we call this *conditional probability*. Mathematically, this is written $P(Y|X)$ and read "the probability of $Y$ given $X$." In the case above, $Y=5$ represented two dice summing to 5, with at least one showing 1. More, the formula is:

```
$P(Y|X) = \frac{P(X \cap Y)}{P(X)}$
```

where $P(X \cap Y)$ denotes the probability of both $X$ and $Y$ occurring. For our example, the numerator represents the probability that the two rolls sum to 5, with restriction that at least one is 1. We saw there are two outcomes out of 36 possible outcomes, for a probability of 2/36. The denominator works out to 12 involving one or more of 36 possible outcomes, for a probability of 12/36. The calculation is done like this:

```
$P(Y=5|X=1) = \frac{(2/36)}{(12/36)} = \frac{2}{6}$
```

When the outcome of $X$ does not influence the outcome of $Y$, we say that $X$ and $Y$ are *independent*. This can be written $P(Y|X) = P(Y)$. In data, the goal is to find random variables $X_1, X_2, \dots, X_p$ which predict $Y$. Predictors which are independent of $Y$ would not be helpful. We will see later that prediction relies heavily on conditional probability.

We are sometimes in the fortunate position of being able to state the probability of the random variable taking each possible value. The *probability mass function* (pmf) for a discrete random variable is a function that takes each possible value as input and returns its probability as an output. For a random variable $Y$ equal to the value showing on a fair, six-sided die, the pmf looks like this:
