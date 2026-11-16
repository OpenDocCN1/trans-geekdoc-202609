9 https://medium.com/machine-learning-bites/deeplearning-series-deep-eural-networks-tuning-and-optimization-39250ff7786d.

0 https://flyyufelix.github.io/2016/10/03/fine-tuning-in-keras-art1.html and https://flyyufelix.github.io/2016/10/08/fine-tuning-in-eras-part2.html.

1 https://towardsdatascience.com/a-comprehensive-guide-on-how-to-fine-tune-deep-neural-networks-using-keras-on-google-colab-free-aaa0aced8f.

2 https://autokeras.com/.

# 5.11 CONVNET MODELS PRETRAINED ON IMAGENET

With deep learning, rather than starting fresh on every project with costly training, validating and testing, you can use pretrained deep neural network models to:

+   • make new predictions,
+   • continue training them further with new data or
+   • transfer the weights learned by a model for a similar problem into a new model—this is called transfer learning.

# Keras Pretrained Convnet Models

Keras comes bundled with the following pretrained convnet models, 3 each pretrained on Image-Net 4—a growing dataset of 14+ million images:

3 https://keras.io/applications/.

4 http://www.image-net.org.

+   • Xception
+   • VGG16
+   • VGG19
+   • ResNet50
+   • Inception v3
+   • Inception-ResNet v2
+   • MobileNet v1
+   • DenseNet
+   • NASNet