# 178 Big recommender systems, volume 1

![](bbox=[0.21033000000000002, 0.09667, 0.7396699999999999, 0.33132999999999996])

Figure 8.3 Resized enlarged image

is be given as input, the command "cv2.imread()" is given. Image is given as digital input to the computer in form of pixels where each pixel has a value depending on its intensity. Each pixel should be processed in an effective manner so that each image being a collection of more than 10,000 pixels are effectively processed. Image is considered to be a matrix of pixels, and each pixel represents one entry of a matrix.

If Grey level images are used for processing, then each pixel is 8-bit length, whereas for a colored image, where each pixel is made of RGB colors, each color is considered to have 8-bit length. Hence, as a whole for three colors, 24 bit are used, making each image 24 bit-length. It is necessary to combine images for doing mathematical operations. Combining images has numerous functions, namely, add, multiply, and divide.

OpenCV for CNN: Before an image is given as an input for neural network either for training or testing, the image is to be preprocessed. The image has to be resized, dimensions to be changed and at last normalized. Each function is an in-built library in OpenCV software. The images are processed in an easier manner without any complex coding.

In order to read the captured image, cv2.imread("img file") is given. The pixel values of the images are extracted. These images, instead of being given directly, are resized, and then further preprocessing is done. All the collected images are converted to images of same size Figure 8.3.

As a next process, images are to be converted from BRG to RGB format. This is done as images are processed in TensorFlow as RGB format, but the input image is always in BRG.

At the latest images are to be normalized for convenience of training the neural network. As each pixel value can have a maximum of 255 pixel, each pixels are divided by 255 and the normalized image is given as input for neural network. For testing, the captured image is resized and normalized and then given to neural network for testing Figure 8.4.