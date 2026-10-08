# Choosing the right model

There are a lot of options for architectures. Based on the flexibility of deployment, you can choose the model. Remember that convolution is smaller and slower, dense layers are bigger and faster. There is a trade-off between size, runtime, and accuracy. It is advisable to test out all the architectures before the final decision. Some models work better than others, based on the application. You can reduce the input size to make the inference faster. Architectures can be selected based on the metrics as described in the following section.

# Tackling the underfitting and overfitting scenarios

The model may be sometimes too big or too small for the problem. This could be classified as underfitting or overfitting, respectively. Underfitting happens when the model is too small and can be measured when training accuracy is. Overfitting happens when the model is too big and there is a large gap between training and testing accuracies. Underfitting can be solved by the following methods:

+   * Getting more data
* Trying out a bigger model
* If the data is small, transfer learning techniques or do data augmentation

Overfitting can be solved by the following methods:

+   * Regularizing using techniques such as dropout and batch normalization
* Augmenting the dataset

Always watch for loss. The loss should be decreasing over iterations. If the loss is decreasing, it signals that training has stopped. One solution is to try out a different optimizer. Class imbalance can be dealt with by weighting the loss function. Always use Tensor to watch the summaries. It is difficult to estimate how much data is needed. This section is the best lesson on training any deep learning models. Next, we will cover some application-specific guidance.