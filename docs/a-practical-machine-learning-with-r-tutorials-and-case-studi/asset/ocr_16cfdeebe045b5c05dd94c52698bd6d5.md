# 9.4 The Idea Behind Neural Network Models

and $H2$ hold the predictor for the diamond, 0.3 and 3, respectively. Both input values are transmitted to the hidden neuron $H1$ and weighted with $eta_2$ and $eta_3$, resulting in values of $0.3 - (-0.9) = 1.2$ and $3 - 0.5 = 2.5$, respectively. In addition, the weighted value from the bias neuron $B1$ ($1-eta_1 = 0.1$) arrives at the hidden neuron $H1$. These three values are aggregated (added up) to the effective input of hidden neuron $H1$

```
$r_{1,i}^{ff} = \frac{1-0.1}{\beta_1=0.1} + \frac{0.3-(-0.9)}{\beta_2=-0.27} + \frac{3-0.5}{\beta_3=1.5} = 1.33$
```

The effective input for hidden neuron $H2$ is calculated similarly, except $Carat$, is weighted with $eta_5$. Clarity, is weighted with $eta_6$, and from the bias neuron $B1$ is weighted with $eta_1$. Adding up these value leads to the effective input for the hidden neuron $H2$:

```
$r_{2,i}^{ff} = \frac{1-(-0.1)}{\beta_1=0.1} + \frac{0.3-0.8}{\beta_5=0.24} + \frac{3-0.6}{\beta_6=1.8} = 1.94$
```

The effective inputs ($r_{1,i}^{ff}$ and $r_{2,i}^{ff}$) together with the logistic activation functions (Equations (9.1) and (9.2)) are used to calculate the activities ($A_{1,i}^{cf}$ and $A_{2,i}^{cf}$) for the hidden neurons:

```
$A_{1,i}^{cf} = \frac{1}{1+e^{-r_{1,i}^{ff}}}\nA_{1,i}^{cf} = \frac{1}{1+e^{-1.33}} = 0.79$
```

```
$A_{2,i}^{cf} = \frac{1}{1+e^{-r_{2,i}^{ff}}}\nA_{2,i}^{cf} = \frac{1}{1+e^{-1.94}} = 0.87$
```

Now we know the *activities* for the hidden neurons $H1$ and $H2$, we weigh with $eta_7$ and $eta_8$, respectively see Figure 9.2. Then we add up the weighted *activities* together with the bias $B2$ according to Equation (9.7) and we get the predicted price ($Price_i$) for the diamond from Table 9.1:

```
$\widehat{Price}_{i} = \beta_7 A_{1,i}^{cf} + \beta_8 A_{2,i}^{cf}\n\widehat{Price}_{i} = 0.1 + 0.8 - 0.79 + 0.9 \cdot 0.87 = 1.51$
```

The prediction (obviously) does not change if we use the Prediction Equation (9.8). We can show this in two steps. First, we plug the numerical $eta$ values into the prediction Equation (9.8):