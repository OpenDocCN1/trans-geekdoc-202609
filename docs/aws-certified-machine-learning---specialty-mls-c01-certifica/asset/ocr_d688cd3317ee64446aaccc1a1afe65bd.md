Therefore, if those cases only exist in the training set, the model will flag **false positive** cases in production environments. The opposite scenario is also true: if there is a particular fraud case in production data, not reflected in the training data, the model will flag a lot of **false negative** cases. False positive and false negative ratios are just two of many quality metrics that you can use for model validation. These metrics will be covered in much more detail later on.

By this point, you should have a clear understanding of the importance of having a good training set. Now, supposing you do have a valid training set, how could you have some level of confidence that this model will perform well in production environments? The answer is by using testing and validation sets:

![](bbox=[0.195, 0.315, 0.805, 0.445])

Figure 1.4 – Data splitting

_Figure 1.4_ shows the different types of data splitting that you can have during training and inference pipelines. The training data is used to create the model; the testing data is used to extract the final model quality metrics. The testing data _cannot_ be used during the training process for any reason other than to extract model metrics.

The reason to avoid using the testing data during training is simple: you _cannot_ let the model learn on top of the data that will be used to validate it. This technique of holding one piece of the data for testing is often called **hold-out validation**.

The box on the right side of _Figure 1.4_ represents the production data. Production data usually comes in continuously and you have to execute the inference pipeline in order to extract model results from it. No training, nor any other type of recalculation, is performed on top of production data; you just have to pass it through the inference pipeline as it is.

From a technical perspective, most ML libraries implement training steps with the `.fit` method, while inference steps are implemented by the `.transform` or `.predict` method. Again, this is just a common pattern used by most ML libraries, but be aware that you might find different name conventions across ML libraries.

Still looking at _Figure 1.4_, there is another box, close to the training data, named **Validation data**. This is a subset of the training set often used to support the creation of the best model, before moving