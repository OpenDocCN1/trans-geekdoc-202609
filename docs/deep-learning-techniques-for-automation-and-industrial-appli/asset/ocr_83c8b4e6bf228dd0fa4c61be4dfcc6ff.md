![](bbox=[0.1, 0.13, 0.88, 0.32])

Figure 4.1 Methodology of classification.

# 4.3 Methodology

In the proposed network architecture, as shown in Figure 4.1, the base model is an architecture of any deep learning model with ImageNet weights. We explored the VGG, ResNet, Inception, Exception, EfficientNet, MobileNet, and NasNet models. All models were extended with three fully connected layers of 2048, 1024, and 512 neurons for uniformity and performance enhancement. After that, the model converged into 21 classes, which is the output layer of every model. The UC Merced dataset was pre-processed before being fed to the model, as images were converted to grayscale along with resizing operations.

# 4.3.1 Pre-Trained Models

A pre-trained model is one that has already been taught to solve a problem. For pre-trained models, we used Keras Applications, a collection of deep learning models that can be used with already trained ImageNet weights. This collection consists of 31 different models belonging to eight families and two versions. The major models belong to the families of VGG, Xception, Inception, ResNet, DenseNet, NasNet, EfficientNet, and MobileNet. Among these models, EfficientNet, ResNet, and MobileNet have two versions each.

# 4.3.2 Dataset

The dataset used in the study was UC Merced Land-Use Dataset, which was made publicly available on October 28, 2010. It consists of 21 classes with 100 images per class, for a total of 2,100 images with a 256 x 256-pixel resolution.