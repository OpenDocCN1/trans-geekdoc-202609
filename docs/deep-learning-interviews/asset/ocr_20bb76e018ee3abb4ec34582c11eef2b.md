exploit ways for FE and transfer learning, e.g., in the application of ImageNet trained CNNs, to target datasets in which labeled data is scarce .

# **SOL-162 ✏ CH.SOL- 7.6.**

There are two main reasons why this is possible:

+   1 The huge number of images inside the ImageNet dataset ensures a CNN model that generalizes to additional domains, like the histopathology domain, which is substantially different from the original domain the model was trained one (e.g., cats and dogs) .

+   2 A massive array of disparate visual patterns is produced by an ImageNet trained CNN, since it consists of 1, 000 different groups .

# **SOL-163 ✏ CH.SOL- 7.7.**

Complete the missing parts regarding the VGG19 CNN architecture:

+   1 The VGG19 CNN consists of $\boxed{19}$ layers .

+   2 It consists of $\boxed{5}$ convolutional and 3 $\boxed{FC}$ layers .

+   3 The input image size is $\boxed{244}$ , the default size most ImageNet trained CNNs work on .

+   4 The number of input channels is $\boxed{3}$ .

+   5 Every image has its mean RGB value $\boxed{\text{subtracted}}$ . (why?)

+   6 Each convolutional layer has a $\boxed{\text{small}}$ kernel sized $\boxed{3 \times 3}$ . (why?)