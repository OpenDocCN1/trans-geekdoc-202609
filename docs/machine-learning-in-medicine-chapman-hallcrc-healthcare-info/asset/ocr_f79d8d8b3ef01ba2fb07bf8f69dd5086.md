In another example, in the classification of melanoma using a deep learning model, eight augmentation techniques and a combination (mix and match) of these eight were implemented and assessed for their improvement/decrement in the accuracy of the model [17]. The augmentation techniques included saturation, contrast, and brightness; saturation, contrast, brightness, and hue; affine (rotate, shear, scaling, and adding pixels symmetrically at the edge); flipping; cropping; random replacement of image with noise; warping; and mixing two lesions into one image. These changes can help to account for the variability in images taken by different cameras, by different picture takers and account for the variability in the setting/background among others. Another feature of this study was that three different CNNs were run in parallel to account for the variability among the CNNs. The study found that geometric augmentation (affine, cropping, and warping) had a more consistent improvement in all three CNNs than did color augmentation (saturation, contrast, brightness, and hue). Some augmentation techniques such as random erasing resulted in worse performance or only slight improvements in the model. Cropping was shown to significantly improve the accuracy of the model. The highest AUC in this study was found with the following combined augmentation techniques: random cropping, affine, flipping, and saturation and contrast, brightness, and hue. Overall, data augmentation has proven to be a very useful method by which the accuracy of a neural network can be improved. More complex data augmentation techniques such as Gaussian blur are likely to be implemented in the future to dermatological image analysis to assess their impact on the model.

# 2.6 LIMITATIONS

Some of the issues/limitations with the adaptation of AI at present are enumerated below:

+   a. Ethical issues and data privacy in sharing of patient data and images

+   b. Quality of images taken by patients or under sub-optimal lighting conditions

+   c. Lack of standardization of training images

+   d. Transportability/sharing of images

+   e. Quality and capability of image recognition programs