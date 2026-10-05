# Basic probability theory

the object is uncertain from its shape. Acknowledging uncertainty instead of denying
it simply trying to avoid it is an important paradigm shift in machine learning.
A common misconception about randomness is that one cannot predict anything
about random variables. While we might not be able to predict a specific value,
it is often the case that some values might be more likely than others. We might
able to say something about how often a certain number will appear when
drawing many examples. We might even be able to state how confident we are with this
number, or in other words, how likely these predictions are. Complete knowledge
of a random variable, $x$, is
captured by the probability density function $f(x)$ in the continuous case and by
probability mass function $P(x)$ in the discrete case. We discuss some specific
examples of such functions in the following. In these examples, we assume that such
probability functions are *a priori*, but in many practical applications we must
estimate this function. Indeed, estimation of probability functions is in some sense
t essence of machine learning. If we would know the "world probability density
function", the probability function of all possible events in the world, then we could
predict as much as possible and in all this world.

Probability theory is the theory of random numbers. We define such numbers
by letters to distinguish them from random numbers written in lower case. A
random variable, $X$, is a quantity that can have different values each time the variable
is inspected, as such in experiments. This is fundamentally different
to a regular, $x$, which does not change its value once it is assigned. A random
number is thus a new mathematical concept, not included in the regular mathematics of
numbers. A specific value of a random number is still meaningful as if might influence
specific processes in a deterministic way. For example, a restaurant owner might be
uncertain about how many people will come to the restaurant, but once people are in
s should serve this number of people.

Since the value of a random number can change every time it is inspected, its
 is captured by the mathematical construct of probability. Note that
is often a debate whether random numbers should be defined solely on the basis of a
frequency measurement, or if they should be treated as a special kind of object with this
inherent property. This philosophical debate between "Frequentists" and "Bayesians"
is importance for our applications. We do not ask where the uncertainty is
coming from, we use the probability construct as a tool to describe uncertainty,
it it is of minor importance to us if this is an inherent limitation or simply a lack of
knowledge.

We formalize the idea of expressing probabilities of drawing specific values for
random variable with some compact notations. For these notations we sometimes need
to distinguish discrete random numbers and continuous random numbers. There is,
principle, not much difference between these two kinds of random variables except
that the mathematical formulation has to be slightly different to be mathematically
correct. For example, the probability mass function for discrete random numbers,

```
$P(x) = P(X = x)$
```

describes the frequency with which each possible value $x$ of a discrete variable $X
noccurs. Note that $x$ is a regular variable, not a random variable. The value of $P(x)$