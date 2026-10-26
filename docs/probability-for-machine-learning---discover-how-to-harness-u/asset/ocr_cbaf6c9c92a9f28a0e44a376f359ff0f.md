# 4.3 Probability for Multiple Random Variables

In machine learning, we are likely to work with many random variables. For example, given a table of data, such as in excel, each row represents a separate observation or event, and each column represents a separate random variable. Variables may be either discrete, meaning that they take on a finite set of values, or continuous, meaning they take on a real or numerical value. As such, we are interested in the probability across two or more random variables.

This is complicated as there are many ways that random variables can interact, which, in turn, impacts their probabilities. This can be simplified by reducing the discussion to just two random variables (X, Y), although the principles generalize to multiple variables. And further, to discuss the probability of just two events, one for each variable (X = A, Y = B), although we could just as easily be discussing groups of events for each variable.

Therefore, we will introduce the probability of multiple random variables as the probability of event A and event B, which in shorthand is X = A and Y = B. We assume that the two variables are related or dependent in some way. As such, there are three main types of probability we might want to consider; they are:

+   - **Joint Probability**: Probability of events A and B.
+   - **Marginal Probability**: Probability of event A given variable Y.
+   - **Conditional Probability**: Probability of event A given event B.

These types of probability form the basis of much of predictive modeling with problems such as classification and regression. For example:

+   - The probability of a row of data is the joint probability across each input variable.
+   - The probability of a specific value of one input variable is the marginal probability across the values of the other input variables.
+   - The predictive model itself is an estimate of the conditional probability of an output given an input example.

Joint, marginal, and conditional probability are foundational in machine learning. Let’s take a closer look at each in turn.

# 4.3.1 Joint Probability for Two Variables

We may be interested in the probability of two simultaneous events, e.g. the outcomes of two different random variables. The probability of two (or more) events is called the joint probability. The joint probability of two or more random variables is referred to as the joint probability distribution. For example, the joint probability of event A and event B is written formally as:

$P(A \text{ and } B)$
(4.8)

The and or conjunction is denoted using the upside down capital U operator ($\cap$) or sometimes a comma (,).

$P(A \text{ and } B) = P(A \cap B) = P(A, B)$
(4.9)