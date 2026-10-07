# 1.5 PROBABILISTIC INFERENCE AND DEEP LEARNING | 9

Learning rate

The learning rate $\eta$ is a hyperparameter that determines the size of the update to the weights at each step of the optimization process. If the learning rate is too large, the optimization algorithm overshoots the minimum and leading to instability or diverge.. On the other hand, if the learning rate is too small, the optimization algorithm may take a long time to converge to the minimum. Therefore, choosing an appropriate learning rate is crucial for successful training.

There are few different strategies for choosing the learning rate, including fixed learning rates, learning rate schedules, and adaptive learning rates. Fixed learning rates involve setting a constant learning rate for the entire training process. Learning rate schedules involve gradually decreasing the learning rate over time. Adaptive learning rates involve dynamically adjusting the learning rate during training based on the progress of the optimization process.

There are also various techniques for monitoring the learning rate during training, such as learning rate schedules that reduce the learning rate if the validation loss stops, or methods that monitor the gradient to detect when the learning rate is too high or too low.

Overall, choosing an appropriate learning rate requires some experimentation and tuning, and there is no one-size-fits-all solution.

# 1.5 PROBABILISTIC INFERENCE AND DEEP LEARNING

In high-risk domains, prediction errors come at high costs. Luckily such domains often provide a fail-safe: self-driving cars perform an emergency stop, doctors run another diagnostic test, and industrial processes are temporal. For deep learning models, this can be achieved by rejecting datapoints with a confidence score below a predetermined threshold. This way, a lower error rate can be guaranteed at the cost of rejecting some predictions. However, estimating high quality confidence scores from neural networks, which create well-ordered

![](bbox=[0.695, 0.6965, 0.875, 0.7785])

Figure 1.1: DLVMs layers of stochastic variables.