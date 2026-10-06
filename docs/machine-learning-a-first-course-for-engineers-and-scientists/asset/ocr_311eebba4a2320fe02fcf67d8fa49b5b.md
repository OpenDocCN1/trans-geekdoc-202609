# 2. Supervised learning: a first approach

> We use this term to refer to the perceived musical energy, not the signal energy in a strict sense. Specifically, we use http://api.spotify.com/ here.

# Example 2.2: Car stopping distances

Ezekiel and Fox (1959) presents a dataset with 62 observations of the distance needed for various cars at different speeds to break to a full stop. The dataset has the following variables:

+   - Speed: The speed of the car when the break signal is given.
- Distance: The distance traveled after the signal is given until the car has reached a full stop.

![](bbox=[0.14, 0.246, 0.758, 0.433])

To make a supervised learning problem out of it, we interpret Speed as the input variable, x, and Distance as the output variable y. Note that we use a non-bold symbol for the input here since it is a scalar value and not a vector of inputs in this example. Since y is numerical, this is a regression problem. We ask ourselves whether the stopping distance would be if the initial speed would be, for example, at 33 mph or 45 mph respectively (which no data has recorded). Another way to frame this question is to ask for the prediction $\hat{y}_*$ for $x_* = 33$ and $x_* = 45$.

> The data is somewhat, so the conclusions are not applicable to modern cars.

# Generalizing beyond training data

There are two primary reasons why it can be of interest to mathematically model the input-output relationships from training data.

+   (i) To reason about and explore how input and output variables are connected. An often encountered in tasks such as medicine and sociology is to determine whether a correlation between a pair of variables exists or "does food increase the life expectancy?". Such questions can be addressed by learning a mathematical model and reasonably about about the chance that the learned relationships between input x and y are due only to random effects in the data, or if there appear to be something to the found relationships.

+   (ii) To predict the output value $y_*$, for some, previously unseen input $x_*$. By some mathematical method which generalizes the input-output examples seen in the training, we can make a prediction $\hat{y}(x_*)$ for a previously unseen test $x_*$. The $\hat{}$ indicates that the prediction is an estimate of output.

These objectives are sometimes used to roughly distinguish between classical statistics, focusing more on objective (i), and machine learning, where objective (ii) is more central. This is not a clear-cut distinction since explainable models are also studied in machine learning. The primary focus in this book, is on making predictions, objective (ii) above above, which is the foundation of supervised machine learning. Our overall goal is to obtain