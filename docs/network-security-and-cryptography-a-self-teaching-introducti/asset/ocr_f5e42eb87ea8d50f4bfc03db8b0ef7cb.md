# 2.3 RANDOM VARIABLES

Random variables are used in probability theory for at least two reasons. First, the way we have defined probabilities earlier in terms of events is awkward. We cannot use that approach in describing sets of objects as cars, apples, and houses. It is preferable to have numerical values for all outcomes. Second, mathematicians and communication engineers in particular deal with random processes that generate numerical outcomes. Such processes are handled using random variables.

The term “random variable” is a misnomer: a random variable is neither random nor a variable. Rather, it is a function or role that produces numbers from the outcome of a random experiment. In other words, for every possible outcome of an experiment, a real number is assigned to the outcome. This outcome becomes the value of the random variable. We usually represent a random variable by uppercase letters such as X, Y, and Z, while the value of a random variable (which is fixed) is represented by a lowercase letter such as x, y, and z. Thus, X is a function that maps elements of the sample space S to the real line -∞≤ x≤∞, as illustrated in Figure 2.5.

![](bbox=[0.238, 0.513, 0.812, 0.753])

FIGURE 2.5 Random variable maps elements of the sample space to the real line.

A random variable X is a single-valued function that assigns a real value X(t) to every point x in the sample space S.

Random variable X may be either discrete or continuous. X is said to be a discrete random variable if it can take only discrete values. It is said to be continuous if it takes continuous values. An example of a discrete random