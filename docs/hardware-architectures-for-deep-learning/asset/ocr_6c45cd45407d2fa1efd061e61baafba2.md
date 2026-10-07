# Iterative convolutional neural network 207

![](bbox=[0.079, 0.073, 0.851, 0.212])

![](bbox=[0.079, 0.226, 0.851, 0.355])

![](bbox=[0.079, 0.37, 0.851, 0.499])

![](bbox=[0.273, 0.503, 0.653, 0.642])

**Figure 9.13** Visualization of features in a fully trained model for layers CONV3 for iterations (a) 1, (b) 2, (c) 3, (d) 4, (e) 5, (f) 6 and (g) 7. The figure shows the top 9 activations for all 96 feature maps of CONV3 layer across the validation data, projected down to pixel space using deconvolutional network approach. The reconstructed image patterns from the validation set which cause high activations in a given feature map are depicted on the right, and the corresponding image patches are depicted on the left

highest filter response in a given feature map on the left, and the corresponding image patch that triggered the response on the left

The extracted features are drastically different in the same CONV layer in different iterations. The ability to extract different features in different iterations, and ability of the ICNN to combine these features after last CONV layer of each iteration are the reasons why the accuracy of each iteration increases.