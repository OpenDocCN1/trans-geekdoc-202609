+   8 https://medium.com/nanonets/how-to-use-deep-learning-when-you-ave-limited-data-part-2-data-augmentation-c26971dc8ced.

# rocessing Power

Deep learning can require significant processing power. Complex models trained on big-data datasets can take hours, days or even more to train. The models we present in this chapter can be trained in minutes to just less than an hour on computers with conventional CPUs. You’ll need only a reasonably current personal computer. We’ll discuss the special high-performance hardware called GPUs (Graphics Processing Units) and TPUs (Tensor Processing Units) developed by NVIDIA and Google to meet the extraordinary processing demands of edge-of-the-practice deep-learning applications.

# Bundled Datasets

Keras comes packaged with some popular datasets. You’ll work with two of these datasets in the chapter’s examples. You can find many Keras studies online for each of these datasets, including ones that take different approaches.

In the “Machine Learning” chapter, you worked with Scikit-learn’s Digits dataset, which contained 1797 handwritten-digit images that were selected from the much larger MNIST dataset (60,000 training images and 10,000 test images). 9 In this chapter you’ll work with the full MNIST dataset. You’ll build a Keras convolutional neural network (CNN or convnet) model that will achieve high performance recognizing digit images in the test set. Convnets are especially appropriate for computer vision tasks, such as recognizing handwritten digits and characters or recognizing objects (including faces) in images and videos. You’ll also work with a Keras recurrent neural network. In that example, you’ll perform sentiment analysis using the IMDb Movie reviews dataset, in which the reviews in the training and testing sets are labeled as positive or negative.

9 The MNIST Database. MNIST Handwritten Digit Database, Yann LeCun, Corinna Cortes and Chris Burges. http://yann.lecun.com/exdb/mnist/.

# Future of Deep Learning

Newer automated deep learning capabilities are making it even easier to build deep-learning solutions. These include Auto-Keras 0 from Texas A&M University’s DATA Lab, Baidu’s EZDL 1 and Google’s AutoML 2 .

0 https://autokeras.com/.

1 https://ai.baidu.com/ezdl/.

2 https://cloud.google.com/automl/.

# 15.1.1 Deep Learning Applications

Deep learning is being used in a wide range of applications, such as: