# # 17 Model training

This section addresses model training. We will follow the following steps to get our model trained and ready, in order to perform gapfilling:

+   1. Download the code of the implementation from the author’s repository.
+   2. Use the code to train the model. Model weights will be saved in *checkpoint* files.
+   3. Export a trained **SavedModel** from an existing *checkpoint*.
+   4. Use the **SavedModel** with the OTBT **TensorflowModelServe** application to perform the optical image restoration.

# ## 17.1 Training from Python

Many practitioners like to have full control of their training process, and will prefer the TensorFlow Python API rather than using the **TensorflowModelTrain** application. Indeed, **TensorflowModelTrain** hides the complexity of the training and provides the user an easy interface to train models on their geospatial data, but with a drastically simplified training approach. However, this user-friendliness comes with the cost of over-simplifying the process, which can be frustrating for deep learning experts and people that would prefer a more customized approach to train their models. In this section, we show that experts can still train their models from their own Python code, and apply the trained model using OTBT. The *deep-gapfill* code illustrates this in providing the build and training of a deep learning architecture in pure Python. The resulting model can be exported as a TensorFlow **SavedModel** and used with the **TensorflowModelServe** application to generate the gap-filled image.