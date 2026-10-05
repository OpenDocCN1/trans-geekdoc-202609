# 2.5 PROPERTIES OF EXPLANATIONS

in a human understandable way. Other types of explanations consist of a set of data instances (e.g in the case of the k-nearest neighbor model). For example, we could predict risk using a support vector machine and explain predictions using the local surrogate method, which generates decision trees as explanations. Or we could use a linear regression model instead of a support vector machine. The linear regression model is already equipped with an explanation method (interpretation of the weights).

We take a closer look at the properties of explanation methods and explanations (Robnik-Sikonja and Bohnec, 2018). These properties can be used to judge how good an explanation method or is. It is not clear for all these to measure them correctly, one of the challenges is to formalize how they could be calculated.

# Properties of Explanation Methods

+   **Expressive Power** is the "language" or structure of the explanations method is to generate. An explanation method could generate IF-THEN rules, decision trees, a weighted sum, natural language or something else.
**Translucency** describes how the explanation method relies on looking into the machine learning model, like its parameters. For example, explanations relying on intrinsically interpretable models like the linear regression model (model-specific) are highly translucent. Methods relying only on manipulating inputs and the predictions have zero transparency. Depending on the scenario, different levels of translucency may be desirable. The advantage of high translucency is that the method can rely on more information to generate explanations. The advantage of low translucency is that the explanation method is more portable.
**Portability** describes the range of machine learning models with which the explanation method can be used. Methods with a low translucency have a higher portability because they treat the machine learning model as a black box. Surrogate models might be the explanation method with the highest portability. Methods that only work for e.g. recurrent neural networks have low portability.
**Algorithmic Complexity** describes the computational complexity of the method that generates the explanations. This property is important to consider when computation is a bottleneck in generating explanations.

# Properties of Individual Explanations

+   **Accuracy:** How well does an explanation predict unseen data? High accuracy is especially important if the explanation is used for predictions in place of the machine learning model. Low accuracy can be if the accuracy of the machine learning model is also low, and if the goal is to explain what the black box model does. In this case, only fidelity is important.
**Fidelity:** How well does the explanation approximate the most important properties of an explanation, because an explanation with low fidelity is useless to explain the machine learning model. Accuracy and fidelity are closely related. If the black box model has high accuracy and

> 7Robnik-Sikonja, Marko, and Marko Bohnec. "Perturbation-based explanations of prediction models." Human and Machine Learning. Springer, Cham. 159-175. (2018).