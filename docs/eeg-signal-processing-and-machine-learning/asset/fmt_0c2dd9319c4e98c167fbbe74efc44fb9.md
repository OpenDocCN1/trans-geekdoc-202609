
## 7.3 Classification Algorithms

Training using a large number of data ensamples and testing a new ensample are the two main stages of classification algorithms. In the training stage, the separability of data plays a crucial role in minimizing the so‐called cross‐validation error. Although by using kernels the data feature space can be mapped to a higher dimensional space where the features become separable, identification of suitable and accurate kernels is not easy to achieve for all types of data. In the following sections more popular classifiers used for classification of biomedical signals such as EEG are briefly reviewed.

### 7.3.1 Decision Trees

Decision trees (DTs) are popular, simple, powerful, and generally nonlinear tools for classification and prediction. They represent `rules` which can be deciphered by human being and utilized in knowledge‐based systems.

The main steps in a decision tree algorithm are:

1.  Selecting the `best` attribute(s) to split the remaining instances and make that (those) attribute(s) a decision node (decision nodes)
2.  Repeating this process recursively for each child
3.  Stop when:
    1.  All the instances have the same target attribute value
    2.  There are no more attributes
    3.  There are no more instances.

One simple DT example for a humidity sensor can be:

> If the time is 9:00am and there is no rain what would be the humidity level (out of low, medium, and severe)?

Depending on the number of attributes, a decision tree may look like [Figure 7.3](#c07.xhtml#c7-fig-0003). DTs can be perfectly fitted to any training data, with zero bias and high variance. Different algorithms are used to determine the `best` split at a node.

![Figure 7.3 An example of a decision tree to show the humidity level at 9:00 a.m. when there is no rain.](images/c07f003.gif)

[**Figure 7.3**](#c07.xhtml#R_c7-fig-0003) An example of a decision tree to show the humidity level at 9:00 a.m. when there is no rain.

DTs are often used to predict data labels by iterating the input data through a learning tree [[25]](#c07.xhtml#c7-bib-0025). During this process, the feature properties are compared relative to the decision conditions to reach a specific category. A DT works only with linearly separable data and the process of building optimal learning trees is NP‐complete [[26]](#c07.xhtml#c7-bib-0026).

In application of DT to EEG signals we need to consider that the input signals are naturally nonstationary, have poor signal to noise ratio, depend on physical or mental tasks, and are contaminated with various artefacts such as external electromagnetic waves, electromyogram and electrooculogram.

In an example [[27]](#c07.xhtml#c7-bib-0027) the authors proposed a simple DT structure to classify the EEG data related to up/down/right/left computer cursor movement imagery EEG data. The mean and variance of continuous Morlet wavelet coefficients, autoregressive (AR) model parameters, average derivative, and skewness are calculated from the EEG of three subjects and used as the input features to the DT system.

In another application [[28]](#c07.xhtml#c7-bib-0028) a classification framework and a data reduction method have been proposed to distinguish between multiclass motor imagery EEG for BCI based on the manifold of covariance matrices using Riemannian geometry [[29]](#c07.xhtml#c7-bib-0029). Riemannian geometry is useful when the solution iterations follow a manifold (rather than for example Euclidean space) due to the imposed constraints. In the context of BCI for example, such constraints are spatial constraints related to the different zones within the motor cortex each belonging to the movement of a particular body part. The function of interest should be differentiable over the Riemannian manifold. In the BCI context, therefore, a spatial covariance matrix is used which is a symmetric and positive definite matrix [[27]](#c07.xhtml#c7-bib-0027), [[28]](#c07.xhtml#c7-bib-0028).

To perform the classification a DT classifier is designed to identify motor imagery tasks and reduce the classification error for the non‐separable cases. Later this has been combined with other classifiers to enable semi‐supervised classification.
