# 24.4 Further Reading

This section provides more resources on the topic if you are looking to go deeper.

# 24.4.1 Papers

+   - *Snapshot Ensembles: Train 1, get M for free*, 2017.
+     https://arxiv.org/abs/1704.00109
+   - *SGDR: Stochastic Gradient Descent with Warm Restarts*, 2017.
+     https://arxiv.org/abs/1608.03983
+   - *Cyclical Learning Rates for Training Neural Networks*, 2017.
+     https://arxiv.org/abs/1506.01186

# 24.4.2 APIs

+   - Getting started with the Keras Sequential model.
+     https://keras.io/getting-started/sequential-model-guide/
+   - Keras Core Layers API.
+     https://keras.io/layers/core/
+   - Keras Stochastic Gradient Descent API.
+     https://keras.io/optimizers/#sgd
+   - Keras Callbacks API.
+     https://keras.io/callbacks/
+   - numpy.argmax API.
+     https://docs.scipy.org/doc/numpy/reference/generated/numpy.argmax.html
+   - sklearn.datasets.make_blobs API.
+     http://scikit-learn.org/stable/modules/generated/sklearn.datasets.make_blobs.html

# 24.5 Summary

In this tutorial, you discovered how to develop snapshot ensembles of models saved using an aggressive learning rate schedule over a single training run. Specifically, you learned:

+   - Snapshot ensembles combine the predictions from multiple models saved during a single training run.
+   - Diversity in model snapshots can be achieved through the use of aggressively cycling the learning rate used during a single training run.
+   - How to save model snapshots during a single run and load snapshot models to make ensemble predictions.