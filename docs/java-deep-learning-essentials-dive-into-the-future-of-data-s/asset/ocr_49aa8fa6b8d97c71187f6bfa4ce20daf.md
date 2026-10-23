# Deep Belief Nets (DBNs)

DBNs are deep neural networks where logistic regression is added to RBMS as the output layer. Since the theory necessary for implementation has already been explained, we can go directly to the implementation. The package structure is as follows:

![](bbox=[0.33, 0.25, 0.67, 0.52])

The flow of the program is very simple. The order is as follows:

+   1. Setting up parameters for the model.
+   2. Building the model.
+   3. Pre-training the model.
+   4. Fine-tuning the model.
+   5. Testing and evaluating the model.

Just as in RBM, the first step in setting up the main method is the declaration of variables and the code for creating demo data (the explanation is omitted here).