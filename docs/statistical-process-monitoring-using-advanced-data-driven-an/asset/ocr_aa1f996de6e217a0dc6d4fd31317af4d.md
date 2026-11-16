The output was generated based on inputs as follows:

```
\(\mathbf{y} = \sum_{i=1}^{10} b_i \mathbf{x}_i,\)
```

where \(b_i = \{0.07, 0.03, -0.05, 0.04, 0.02, -1.11, -0.04, -0.02, 0.01, -0.03\}\), for \(i = 1, ..., 10\). A noise-free dataset with 256 samples was generated and then contaminated with zero-mean Gaussian noise.

The performance of the NL-PLS was compared with that of the conventional PLS model. The cross-validation method was used for selecting the optimum number of latent variables. The total data were split into two parts, a training dataset and a testing dataset. The training data was used to develop the model, the obtained model was tested with a testing dataset, and its mean squared error (MSE) was evaluated. The optimum number of the latent variable was selected by choosing the one which gives the minimum MSE. Five latent variables were selected for PLS, three for poly-PLS and ANFIS-PLS models based on the minimum MSE values. Table 4.3 summarizes the results of the comparison for different signal-to-noise ratio (SNR) and clearly indicates that poly-PLS and ANFIS-PLS modeling provides a significant improvement over the conventional PLS modeling techniques. This is because the nonlinear PLS algorithm uses the appropriate mapping function in the inner relation of the PLS algorithm, thus it avoids overfitting the model and improves the model prediction ability. Additionally, results showed the strongest predictive capability of ANFIS-PLS among all the models. In the following section, one more example is considered.

| Model | SNR = 5 | SNR = 10 | SNR = 20 |
|---|---|---|---|
| PLS | 0.2189 | 0.1209 | 0.0641 |
| Poly-PLS | 0.2019 | 0.1019 | 0.049 |
| ANFIS-PLS | 0.1739 | 0.08781 | 0.047 |

# ### 4.5.1 Application of plug flow reactor

Here, the detection performance of NLPLS-based monitoring methods is assessed using simulated plug flow reactor (PFR) data. PFRs, or piston flow reactors, consist of a hollow pipe in which reactants travel [79]. Fig. 4.13 displays an example of a schematic representation of a PFR having tubular form wrapped with an acrylic mold that is encased in a tank. To keep a relatively stable reactant temperature, water at a controlled temperature is passed via the tank. PFRs are widely used in either gas or liquid-phase systems. Two first-order reactions are performed in the reactor, based on the reactant species, A:

```
\(A \rightarrow B \rightarrow C\)
```