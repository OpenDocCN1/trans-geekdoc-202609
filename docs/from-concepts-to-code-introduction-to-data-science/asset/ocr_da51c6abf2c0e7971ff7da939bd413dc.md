The gradient is a vector, which is a quantity with both direction and magnitude. Earlier, we learned that the derivative can be used to find extrema, which can occur where the derivative is zero or undefined (at critical points). For a function of several variables, the gradient can be used in an analogous way to find extrema, as we will see later.

For going deeper on calculus, a masterful pair of books is [26] and [27].

#  8.4 Probability

Our data will include variables subject to uncertainty or randomness, and this can be treated effectively with tools from probability. A random experiment has an output that cannot be predicted with certainty. When the experiment is repeated a large number of times, the average output exhibits predictability. The roll of an unbiased, six-sided die will have an outcome that cannot be predicted, but after a large number of rolls, each number should appear about 17% of the time.

There are three essential ingredients in probability theory:

+   * The sample space is the set of all possible outcomes of the experiment. It is generally denoted $\Omega$. For an experiment where a fair coin is tossed, $\Omega=\{hh, ht, th, tt\}$ where $h$ and $t$ are heads and tails, respectively.

+   * The events are outcomes of the experiment. They are subsets of $\Omega$. We can denote the set of all events $\mathcal{A}$. A particular event from this example is $\{hh\}$.

+   * The probability is a number associated with each event $A$, written $P(A)$ and falling in $[0,1]$. The probability of an event increases to 1 as it is more likely. The frequentist idea provides intuition: for a large number of repeated trials, the probability of an event will be the number of times the event occurs divided by the number of trials.

A random variable is a quantity subject to random events, and it depends on the outcome of the experiment. Mathematically, it is a mapping from $\Omega$ to a measurable space (usually $\mathbb{R}$). Here are some examples:

+   * Let $X$ be the number of heads tossed over two flips of a fair coin

+   * Let $Z$ denote the number of points scored by the winning team in a Super Bowl