Machine Learning Models

through a technique calibrated tuning or parameter calibration, resulting in a range of possible alternative scenarios and simulations of the observed data.

# 6.2.1 Empirically Driven Models

To locate machine learning models within the models framework, we can think about the scope of the analysis, which in this case is predicting the future and preventing undesired outcomes.

In particular, these types of models are subdivided in:

+   Mechanistic Model: For example the SIR model is a classic compartmental model used to simulate the spread of infectious diseases. It divides the population into three compartments: susceptible (S), infectious (I), and recovered (R). The equations describe the rate of change of each compartment over time, with $eta$ represents the transmission rate and $\gamma$ represents the recovery rate.

```
$$\begin{aligned}&\frac{dS}{dt} &=-\beta \cdot S \cdot I\\frac{dI}{dt} &=\beta \cdot S \cdot I-\gamma \cdot I\\frac{dR}{dt} &=\gamma \cdot I\end{aligned}$
```

+   Empirically Driven Model: Empirically driven models do not have explicit mathematical equations like mechanistic models. Instead, they learn patterns and relationships directly from data. An example of an empirically driven model is Random Forest which is a machine learning algorithm thatat builds multiple decision trees and combines its predictions to make accurate predictions. It works by splitting the data into subsets and building a decision tree for each subset. The final prediction is made by aggregating the predictions of all decision trees. Unlike mechanistic models, Random Forest does not rely on explicit equations or known relationships but learns patterns from the input data.

Machine learning models fall under the category of empirically driven models. Unlike mechanistic models, which are based on explicit equations and known relationships between variables (as the differential equations used in infectious disease modelling), machine learning models derive patterns and relationships directly from data without explicit knowledge of the underlying mechanisms. Therefore, while both mechanistic and empirically driven models are used for prediction, they operate on different principles:

Mechanistic models rely on known relationships and equations, while machine learning learns patterns from data.

Before delving deep into machine learning techniques for analysing health data and metrics, it's essential to proceed step by step in building a modelling framework. This approach begins with a thorough understanding of the modelling processes.

> 4Ruth E. Baker et al., “Mechanistic Models Versus Machine Learning, a Fight Worth Fighting for the Biological Community?” Biology Letters 14, no. 5 (May 2018): 20170660, doi:10.1098/rsbl.2017.0660.