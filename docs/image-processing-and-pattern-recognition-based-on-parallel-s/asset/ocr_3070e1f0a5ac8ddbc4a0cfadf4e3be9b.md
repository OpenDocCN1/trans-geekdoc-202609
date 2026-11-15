# 3.2 Use of Parallel Shift Technology for Noise Removal in Images

In the real world, information perception by any intelligent system is accompanied by the presence in a signal of a certain amount of noise among useful data. Misinformation arises owing to the effects of certain internal and external factors.

The intelligent system cannot influence the external factors without changing the environment. Reduction in the amount of noise can build new means of signal detection.

Internal factors of negative impact are lost during transmission of information within the system and the error in the chosen method of noise control. In processing the signals, one of the methods of noise control is frequency filtering. Digital image processing is widely used by a variety of masking. It allows smoothing out of sudden changes in pixel brightness of the object. Also, masking allows selection of certain elements of the image for further removal from the visual field.

The use of parallel shift technology allows separation of the noise removal process into three stages. Since use of the parallel shift technology analysed the shape of the image, the object of study will be considered as a binary image. Half-tone images are divided into binary image at the stage of the bundle. Assume that noise information is evenly distributed across all levels of brightness of the image. Then, if the image is divided into brightness gradations of ranges and converted into n binary objects, in each range hit only a 1/n part of all non-zero elements of noise. Noise elements with zero value will be duplicated in each layer. Expected number of noise information that hits into each binary object is less than the noise amount of the original image. Thus, the separation process can be considered as the first step in removal of noise.

The second stage of the process should be removal of noise by using parallel shift technology. As we study the binary image, the noise in this case can be considered a stand-alone group of single elements and zero elements that distort the object. In the process of software simulation following types of noise were used:

+   1. ‘Pepper’ type of noise: Equal filling of the visual field of a binary image by cells that have ‘1’ value.
+   2. ‘Salt’ type of noise: It is equal filling of the visual field of a binary image by zeros.
+   3. ‘Salt’ and ‘pepper’ type of noise: Here it is a combination of the two previous types.

In the noise removal process, use of parallel shift technology is necessary to apply in the edge detection method described above. In this