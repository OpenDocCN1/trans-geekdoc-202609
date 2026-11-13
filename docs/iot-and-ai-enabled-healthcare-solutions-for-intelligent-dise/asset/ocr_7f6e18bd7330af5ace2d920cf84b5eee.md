+   • Process:
+       • Forward Pass: Input data is passed through the network layer by layer to generate predictions.
+       • Compute Loss: The loss function measures the difference between the predicted output and the actual target.
+       • Backward Pass: The loss is propagated backward through the network, layer by layer, to compute the gradient of the loss with respect to each weight. This involves applying the chain rule of calculus to compute these gradients efficiently.
+       • Weight Update: The gradients are used to update the weights in the direction that reduces the loss.

# 2. Gradient Descent:

+   • Purpose: Gradient descent is the optimization algorithm used to update the network's weights using the gradients computed by backpropagation.
+   • Variants:
+       • Batch Gradient Descent: Computes the gradient using the entire training dataset. It provides accurate gradients but can be slow and computationally expensive [15].
+       • Stochastic Gradient Descent (SGD): Computes the gradient using a single training example. It is faster but introduces more noise into the weight updates.
+       • Mini-Batch Gradient Descent: Computes the gradient using a small subset (mini-batch) of the training data. It balances the efficiency and accuracy of the gradient estimation [14].

# 3. Mathematical Formulation:

+   • For each weight www in the network, the update rule in gradient descent.

Loss Functions and Optimization

# 4. Loss Functions:

+   • Purpose: The loss function quantifies how well the predictions of the neural network match the actual targets. It guides the optimization process by providing a measure to minimize.
+   • Common Loss Functions:
+       • Mean Squared Error (MSE): Used for regression tasks, it calculates the average squared difference between the predicted and actual values.
+       • Cross-Entropy Loss: Commonly used for classification tasks, it measures the difference between the predicted probability distribution and the actual distribution.
+       • Binary Cross-Entropy: Used for binary classification problems.