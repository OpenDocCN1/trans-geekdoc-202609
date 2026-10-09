+   1. The hidden neuron is distributed according to $X \sim \text{binomial}(n, \gamma)$ random variable and fires with a probability of $\gamma$. There are 100 neurons and only 20 are fired .

+   2. The hidden neuron is distributed according to $X \sim \text{Uniform}(0, \gamma)$ random variable and fires with a probability of $\gamma$ .

# **PRB-64** CH.PR B- 3.35.

Your colleague, a veteran of the Deep Learning industry, comes up with an idea for a BNN layer entitled **OnOffLayer** . He suggests that each neuron will stay **on** (the other state is **off**) following the distribution $f(x) = e^{-x}$ for $x > 0$ and $f(x) = 0$ otherwise (Fig. 3.11 ) . $X$ indicates **the time in seconds the neuron stays on** . In a BNN, 200 such neurons are activated independently in said OnOffLayer. The OnOffLayer is set to off (e.g. not active) **only if at least 150 of the neurons are shut down** . Find the probability that the OnOffLayer will be active for at least 20 seconds without being shut down .

![](bbox=[0.25, 0.45, 0.75, 0.55])

# **PRB-65** CH.PR B- 3.36.

A Dropout layer [12] (Fig. 3.12 ) is commonly used to regularize a neural network model by randomly equating several outputs (the crossed-out **hidden** node $H$) to 0 .

![](bbox=[0.44, 0.69, 0.56, 0.9])