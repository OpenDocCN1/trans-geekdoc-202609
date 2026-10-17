
matrix \[0, 0, 0; 0, 1, 1; 0, 1, 2\] from input image and has nothing to do with the remaining parts of the input image pixels.

本书版权归Arcler所有

![Image 633](index-142_1.jpg)

![Image 634](index-142_2.jpg)

![Image 635](index-142_3.png)

![Image 636](index-142_4.png)

![Image 637](index-142_5.png)

# Deep Learning Algorithms

116

The parameters for fully or local connectivity for all the layers in this CNN are listed in Table 1.

< # ! ?

**System Validation Using ImageNET Dataset**

Before applying this system into the ocean fish data set developed in this research, authors downloaded images from the well-known ImageNet ILSVRC \[21\] to do a system validation testing through object classification.

There are 500 images with 20 classes ranging from fish, coral, sea turtle,

¯ »

truths images are obtained from operate labeling soware manually. Each

» ^

bounding boxes location information and class information made up of a

{»{» < #" (X, Y), the

width w, and height h of the bounding box confidence scores, and predicted probabilities of fish, as shown in Figure 8.To predict the target location of an image, the target is displayed in a bounding box. There are always errors between the ground truth and the predictions. Loss function was developed to measure errors consisting of three parts: coordinate error, (Intersection over union) IoU error, and class error. Equation (2) gives the mathematics form of the loss function.

(2)

Here, IoU is used to measure position accuracy as shown in Figure 9.

**Figure 4**. Feature extractor using convolutional operation.

本书版权归Arcler所有

![Image 638](index-143_1.jpg)

![Image 639](index-143_2.jpg)

![Image 640](index-143_3.png)

![Image 641](index-143_4.png)

![Image 642](index-143_5.jpg)

![Image 643](index-143_6.png)

![Image 644](index-143_7.png)

![Image 645](index-143_8.png)

# Fish Detection Using Deep Learning

117

Each grid cell in an image will predict 䕲 bounding boxes that encloses an object to predict the object localization and class. In addition, there is a confidence with each bounding box. Confidence score has nothing to do with the class of object. It just depicts how certain it is that the predicted box actually encloses the real object.

(3)

where Pr(object) represents the probability of the object of interest. If there is an object in the grid cell, the Pr(object) is 1; otherwise, it is 0.

Usually, loss function is in the form of the sum of squared errors as shown below \[33\]. It consists of three parts which are localization errors,

##

(4)

where x , y are the ground truth coordinates of objects center; w , h are i

i

i

i

the width and height of the ground truth bounding box;

are the predicted

coordinates of the objects center;

are the width and height of predicted

\# #'# ? {

values from different classes.

**Figure 5**. Fully connected neural net and locally connected neural net \[32\].

本书版权归Arcler所有

![Image 646](index-144_1.jpg)

![Image 647](index-144_2.png)

![Image 648](index-144_3.png)

![Image 649](index-144_4.png)

# Deep Learning Algorithms

118

**Figure 6**. Convolutional operation using local connections.

**Ground Truth Preparation for Real Ocean Environment**

After testing the CNN system with perfect images without noise. Next step is to build our own dataset of fish in the ocean. Because it is difficult to obtain images from other kinds of objects such as the sea turtle, coral and so on. is part of the research, fish is the only object to be detected. For the collection of 410 images, many of them have multiple fish in one image, so the detection is challenging. The same method was chosen to create ground truth image. And all the parameters introduced before remain the same, only

{»{»{ {»{»

because of reduce in the classes. Figure 11 illustrates one labeled image example. It is obvious that this data set is totally different from the ideal images from ImageNET.

**DATA AUGMENTATION**

Since deep learning is based on large training dataset for the system to learn and build up the identification knowledge, enough data has to be provided as learning resources to extract object features \[34\].

< # #

collected in real underwater environment from the Gulf of Mexico and are going to be used to attract object features. However, the number of original images collected from a particular environment is not large enough to train the system.

本书版权归Arcler所有

![Image 650](index-145_1.png)

![Image 651](index-145_2.png)

![Image 652](index-145_3.png)

