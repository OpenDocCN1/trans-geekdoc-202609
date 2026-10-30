can interpret high-level features better than low-level ones, similarly, the LIME tool sees high-level features in the form of super pixels, which are collections of pixels of the image that cover a particular area in the image.

Evaluation of the results is done using metrics, which is discussed in the next section, along with the experimental setup for implementation of this whole framework.

# 8.5 METRICS AND EXPERIMENTAL SETUP

Metrics are used to evaluate the performance of models during training and testing, which is discussed in this section, along with the experimental setup, i.e., hardware and software used.

# 8.5.1 Evaluation metric

Accuracy is used as a metric to evaluate the results of the models on the test set after implementation and accuracy is also seen in graphs while training for train and validation sets. Accuracy stands for the number of correct predictions, i.e., real as real and fake as fake, out of the total number of predictions. Also, heatmaps and boundary maps from LIME are used to validate the results.

# 8.5.2 Experimental setup

This framework was implemented using Tensorflow version 2.10.1 and Keras API in Jupyter notebook and Anaconda GPU environment. For the explainability part, LIME was installed. The specifications for the GPU machine used were NVIDIA GeForce RTX 3060 GDDR6 @6GB.

Evaluation of the results obtained from this whole framework is given in Section 8.6 in the form of accuracy and loss curves, along with LIME visualization in the form of boundary maps for super pixels and heatmaps.

# 8.6 RESULTS AND DISCUSSION

This section shows the results of implementation in the form of graphs and visualization of classification using LIME. The accuracy and loss curves using the models given in Section 8.4 are shown here. The number of epochs is fixed as 10 for all the models since a reasonable accuracy rate was achieved with 10 epochs for some of the models. Figure 8.8 shows the loss and accuracy curve for the custom CNN model.