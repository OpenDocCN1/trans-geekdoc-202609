![](bbox=[0.301, 0.145, 0.698, 0.493])

Figure 10.5 Schematic representation of a residual block.

# # 10.2.4 Results from convolutional neural network

This chapter evaluates the proposed model performance for predicting the value of the effective Young's modulus, and the accepted prediction gives less than a 10% difference (since the outcome comparison for the validation case in Section 10.2.1). The model was built on Pytorch 1.9, and the training was performed on a device with NVIDIA RTX 2080. In addition, augmentation (see Section 10.2.2) was used for training. Finally, further hyperparameter tuning was performed to obtain the results. Since there is a wide distribution (i.e., a high range or scale) in the Young's modulus, the value of MAE does not provide a good representation of the model regression. The relative error percentage is used to investigate the results for a better baseline.

The model achieved an average error of 5.92%, which is well within the 10% acceptable tolerance initially. The final error distribution is shown in Fig. 10.7. As can be seen, the model does a relatively good job predicting many images with a relatively low error rate struggling with a few images. In fact, for the majority of the tested cases, the error for the prediction is less than 5%. For some limited cases, a rather high error appeared. Observing the mesostructures related to those cases, it was realized that the randomly generated patterns for these cases are accidentally way different compared to the majority of the dataset. The