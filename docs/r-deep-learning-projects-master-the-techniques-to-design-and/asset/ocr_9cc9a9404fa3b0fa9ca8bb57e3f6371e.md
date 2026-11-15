Besides the 4.77% (93.93% to 98.70%) performance increase compared to no data augmentation, we observe that each iteration takes a longer time than before (around 20 s to around 80 s). This is because `image_data_generator()` generates mini-batches of augmented image data in real time for each iteration. So, even if the same set of samples is used in two iterations, the augmented data can be very different. Such setting adds more variation to the training set, which in turn makes the model more robust. And that is why data augmentation is considered an approach to reduce overfitting.

Another particularly useful application of data augmentation is balancing a dataset. In most unbalanced classification cases (such as online ads click-through prediction, or banking fraud detection), we usually down-sample the dominant class. However, this can be counterproductive for small datasets. The alternative solution is to augment data from the minor class.

Last but not least, there are other approaches not mentioned previously to augment image data. For example, rescaling multiplies pixel values by a factor and, as a result, changes the lighting condition. Shearing and zooming are useful data augmentation transformations as well. They can be specified in `image_data_generator()`. If interested, you can try applying any of these approaches and see whether you can beat 98.70%.

# # Reviewing methods to prevent overfitting in CNNs

Overfitting occurs when the model fits too well to the training set but is not able to generalize to unseen cases. For example, a CNN model recognizes specific traffic sign images in the training set instead of general patterns. It can be very dangerous if a self-driving car is not able to recognize sign images in ever-changing conditions, such as different weather, lighting, and angles different from what are presented in the training set. To recap, here's what we can do to reduce overfitting:

+   • Collecting more training data (if possible and feasible) in order to account for various input data.
+   • Using data augmentation, wherein we invent data in a smart way if time or cost does not allow us to collect more data.
+   • Employing dropout, which diminishes complex co-adaptations among neighboring neurons.