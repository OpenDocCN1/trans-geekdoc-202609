In an edge computing environment, models may need to adapt to changing data distributions. This is achieved through online learning, where the model parameters are updated incrementally as new data arrives, which is done via Equation 5.8:

```
\(\theta(t + 1) = \theta(t) - \eta \nabla L(M(x(t); \theta(t)), y(t))\) (5.8)
```

where \(\theta t\) are the model parameters at time \(t\), \(\eta\) is the learning rate, and \((x_t, y_t)\) is the new data point at time \(t\) in the current scenario sets. Based on this process, the autoML system in edge devices for predictive maintenance is characterized by a robust framework encompassing model selection, hyperparameter optimization, cross validation, and online learning. This system ensures the continual adaptation and optimization of predictive models catering to the dynamic nature of industrial environments.

Similarly, the auto-Sklearn process, which is an automated machine learning (autoML) tool designed to optimize machine learning workflows, particularly focusing on a model selection and hyperparameter tuning, is used for optimizing performance of this process.

Auto-Sklearn employs meta-learning to suggest initial configurations. Given a dataset \(D\), auto-Sklearn references a meta-dataset m containing performance data of various machine learning algorithms on numerous datasets and their samples. The similarity between \(D\) and each dataset in m is calculated, and the best-performing configurations on similar datasets are used as starting points. The similarity score \(s(D, Mi)\) for a meta-dataset instance \(mi\) is quantified via Equation 5.9:

```
\(S(D, Mi) = exp(-\gamma \cdot dist(D, Mi))\) (5.9)
```

where dist(D,Mi) is a distance measure between the datasets, and \(\gamma\) is a scaling factor. Bayesian optimization is another core component of auto-Sklearn for hyperparameter tuning. It models the mapping from hyperparameters \(\theta\) to a performance metric \(P\) as a probabilistic model, and a Gaussian Process (GP), respectively. The acquisition function \(\alpha(\theta)\), such as expected improvement (EI), is used to select the next hyperparameters to evaluate via Equation 5.10:

```
\(A(\theta) = E[max(P(\theta) - P(\theta +), 0)]\) (5.10)
```