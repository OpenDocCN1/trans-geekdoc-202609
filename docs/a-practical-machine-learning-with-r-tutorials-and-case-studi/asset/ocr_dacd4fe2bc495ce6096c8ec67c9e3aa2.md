# 232 9 Deep Learning — MLP Neural Networks Explained

neurons (H1 and H2), and an output layer at the right of the network with one output neuron that will later connect the diamond's predicted price (O1).

The three layers (input, hidden, and output) are fully connected with the red and black lines, meaning that each neuron of a previous layer is connected with each neuron of the following layer. Considering that *perceptron* is a different neuron for *neuron*, you can see where the name *Multi Layer* (input, hidden, output) *Perceptron* comes from. The MLP in Figure 9.1 has only one hidden layer, but more complex MLP networks have multiple hidden layers with many neurons inside each layer.

A Neural Network processes observations one by one and creates a prediction at the output neuron (O1) for each observation. We will use Figure 9.1 to show how a Neural Network can generate a prediction from the values of the predictor variables of a given observation $i$. For now, we assume that values for the parameters ($eta$ ) are provided:

**Step 1:** In the beginning of the prediction process, the predictor variables of observation $i$ are loaded into the input neurons (I1 and I2). For example, with a diamond with 0.3 clarity ($Carat=0.3$) and rating of SII ($Clarity=3$), the input neuron I1 contains value of 0.3, and the input neuron I2 contains value of a.

**Step 2:** The values of the input neurons are transmitted to the hidden neurons (H1 and H2), but before they arrive, their values are weighted (multiplied) by the parameters $eta_1,eta_2,eta_3, \beta_4$, respectively. This way, the original value from the input neuron are amplified or weakened, depending on whether the absolute values for the $eta$ are greater or smaller than one. A negative $eta$ parameter reverses the signs of the predictor variable values.

In the weighted inputs ($Carat,eta_2, Clarity,eta_3, Carat,eta_4$) that arrive at the hidden neurons H1 and H2, the hidden neuron B1 sends a value that is equal to $eta_3$ to hidden neuron H1 and a value of $eta_4$ to hidden neuron H2. Because these values are independent of the values for the predictor variables (I1 and I2) always contain a value of one, the neurons B1 and B2 are biased neurons.

**Step 3:** As you can see in Figure 9.1 at the green $\oplus$ signs in front of the hidden neurons H1 and H2, three different weighted values arrive at each before they are further processed. For each hidden neuron, the three values are aggregated to single values called the *effective inputs* of the hidden neurons by adding them up. This is symbolized by the green $\oplus$ signs in front of H1 and H2 in Figure 9.1. The *effective inputs* ($I_{1}^{eff}$ and $I_{2}^{eff}$) for the hidden neuron H1 and H2 are:

```
$I_{1}^{eff} = \beta_1 + \beta_2 Carat + \beta_3 Clarity,$$
```

```
$I_{2}^{eff} = \beta_4 + \beta_5 Carat + \beta_6 Clarity,$$
```

and