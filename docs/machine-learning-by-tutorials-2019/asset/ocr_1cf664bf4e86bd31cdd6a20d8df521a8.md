# Machine Learning

# Chapter 7: Going Convolutional

Figuring out how to get your training data over to the cloud service is of importance. Different providers have different solutions for this. Storing your data in the cloud usually isn't free, but the datasets are small enough — about 120MB — that it won't break the bank. Usually, you only pay a few cents per gigabyte per.

Here are some suggestions for machine learning in the cloud:

+   Google Colaboratory at colab.research.google.com is free Jupyter notebook environment. You can use Colab to run your notebooks on a cloud GPU and even a TPU — Google's high-performance Tensor Processing hardware for free. That's pretty good deal. Your notebooks are stored in Google Drive. The easiest way to upload the dataset is using Google Cloud Storage, although they may offer different options. Colab is best from Chrome.

+   Paperspace at www.paperspace.com

+   Crestle at www.crestle.com

+   FloydHub at www.floydhub.com

+   LeaderGPU at www.leadergpu.com

+   Amazon AWS EC2 at aws.amazon.com. AWS is the world's most popular provider of general-purpose cloud computing. This is just like having your deep-learning box, except that you're renting it from Amazon. You can start out by using the free tier but they also have GPU instances. Not the easiest or cheapest solution, but definitively the most flexible.

# Convolution layers

The models you've built in Keras have, so far, consisted of Dense layers, which take a one-dimensional vector as input. But images, by nature, have a width and a height, which is why you had to "flatten" the first image.

Unfortunately, flattening destroys the spatial nature of the input data. What's more, it also removes depth information from the image. Recall that the depth dimension stores the three color components for each pixel: red, green and blue. These three values are closely related, so you don't want to treat them as separate numbers, but as one indivisible unit: the pixel's color.

The spatial relationships between the pixels — which pixels are above, below and next to any other pixel — as well as the relationship between the pixel's color

![](bbox=[0.162, 0.923, 0.338, 0.953])

244