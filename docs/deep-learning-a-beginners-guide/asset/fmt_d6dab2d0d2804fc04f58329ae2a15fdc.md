
# RMSprop Optimizer

RMSprop is an extension of the `AdaGrad` optimizer and is based on the adaptive learning rate. This is based on gradient descent with momentum. The declined moving average of partial gradients is utilized to adjust the update on each parameter. Thus, RMSprop considers the recent partial gradient values over the search space, without relying on previous gradients. Thereby addressing the limitation of `AdaGrad`. RMSprop takes the `EMA` of these gradients, without using the cumulative sum of squared gradients as in `AdaGrad`. As in momentum, this has become a typical update for the learning rate in many optimizers. Here, to avoid the summation of all derivatives of weights becoming a high or very small value, that prevents very small or high learning rates, respectively, these methods consider weighted average instead of derivative of weights. The per-parameter learning rate, which is based on the average of the values of the gradients for the weights in the recent past, is utilized by considering the changing frequency.

Since it prevents vertical fluctuations, a high learning rate can be used, which results in taking large steps horizontally and converting efficiently. However, there is a chance of getting divergent behaviors due to drastic updates with very large learning rates. [Figure 6.12](#ch13.xhtml#f98) shows a representation of fast and slow learning rates.

![Figure 6.12 Representation of the behavior of different learning rates.](html/images/9781032473246_C006_012.jpg)

[Figure 6.12](#ch13.xhtml#f98b) Representation of the behavior of different learning rates.

When we compare the above three techniques, `Adadelta` uses `EMA` instead of the learning rate. `AdaGrad` and `RMSProp` utilize the second moment without and with decay, respectively. Thus, `RMSProp` speeds up the process compared to `AdaGrad`.

## ADAM Optimizer (Adaptive Moment Estimation)

`Adam` is a widely used optimizer and different to classical `SGD`, which uses a fixed learning rate for a given model to update weights throughout the training. This uses the features of both `RMSProp` and Momentum. For instance, for the gradient, the `EMA` of gradients is used as in Momentum. To decide the learning rate of parameters, it divides the learning rate by the square root of the `EMA` of squared gradients as in `RMSProp`. The `RMSProp` optimizer adapts the learning rates of the parameters by considering the mean, which is the average first moment. Whereas `Adam` uses the uncentered variance, which is the average of the second moments of the gradients. This allows for the management of sparse gradients on noisy tasks. Therefore, `Adam` processes the `EMA` of the gradient and the squared gradient by enabling it to handle the decay rates of the moving averages.

Generally, the performance of the `Adam` optimizer is good and used as the default optimizer for most of the applications due to the following reasons.

*   Straightforward to implement.
*   Low memory consumption.
*   Computationally efficient.
*   Faster computation time.
*   Requires few parameter tuning.
*   Applicable for large tasks.
*   Can be used for tasks with noisy or sparse gradients.

# 6.7 Neural Architecture Search (NAS)

## 6.7.1 Overview of NAS

Deep learning models have become autonomous and essential in many industries due to their significant accuracy and robustness. Generally, the design and development of an efficient neural network require the knowledge of architectural engineering, domain expertise, and time to explore an iterative process for the full range of solutions. Designing a neural network is not necessarily straightforward due to the aspects, such as intractable design space, non-transferable optimality, and inconsistent efficiency matrices that affect the development of deep learning models. For instance, neural network designers are faced with a combinatorically massive design space, where different possible architectures can be obtained by merely changing parameters, such as kernel size and the number of filters. When we include additional features, such as the number of layers and skip connections between layers, this creates a complex search space that is intractable to search manually and consumes more time. As a result, usually designers select a model with similar previous tasks and try to evolve the selected architecture in a few iterations. This approach is not sufficient to fully explore the potential architectural space.

In order to generalize neural networks while avoiding overfitting the training datasets, it is important to find optimized architectures. However, based on the objectives of the organization, where productivity is more important than quality and due to the lack of time and expertise, the efficiency of the models may not consider and proceed with a sufficient model that performs the task. Thus, based on the application domain, different architecture-specific solutions should be designed. Since most of the model designs depend on expert knowledge, there is a requirement to find an autonomous way to design and develop efficient and optimized deep learning models.

Neural architecture search (`NAS`) is used to automatically design optimal and efficient neural networks with low losses, for a given dataset. This method evaluates many deep learning architectures across a search space using a search strategy and selects the best match for the objectives of a given problem by maximizing a fitness function. This can be considered a biologically inspired optimization-based algorithm. `NAS` automates both the architecture selection and neural network training, which along with the increase in computational resources available should eventually allow the development of tailor-made architectures for each task per each hardware platform. `NAS` is used in various tasks, such as object detection and image classification in image processing, hyperparameter optimization and meta-learning in `AutoML`. `NAS` will bring flexibility to industries with deep learning applications that can adapt to diverse requirements. Thus, the advantages can be listed as follows.

*   A formal algorithmic approach for developing neural networks.
*   Makes model development easier for each hardware solutions.
*   Can develop models highly competitive with models developed by human experts.
*   Easier to regulate resource constraints.

Generally, `NAS` is not widely applied in real-world applications due to a few limitations. `NAS` methods explore many potential solutions with variable complexities. Hence it is computationally expensive in terms of resources and time. The larger their search spaces, the more there are architectures to test, train, and evaluate. Since the architectures are evaluated with training data, it can be hard to predict the performance on real data. Also, expert knowledge is required to speedup the search process by fine-tuning different architectures and guiding the search to converge quickly towards an optimal solution. Additionally, it may not produce the global optimal solution even with sufficient resources. Further, many `NAS` studies are irreproducible and may not be able to compare with the baseline models.

## 6.7.2 NAS Process
