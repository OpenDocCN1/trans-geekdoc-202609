
The model achieved a validation accuracy, F1 score, and AUC score of 95.83%, 96.68%, and 95.38%, respectively.

A general study was conducted about the applications of machine learning in various fields. Subbarao et al. [26] explore the application of machine learning techniques to enhance the adoption and efficiency of solar energy in urban settings. Sardar et al. [27] provide an in-depth analysis of the role of machine learning in transforming healthcare by leveraging biomedical big data, addressing both the significant potential and the challenges that need to be overcome. Sardar et al. [28] provide a comprehensive overview of the concepts and theory behind explainable AI, highlighting its significance, especially in medical data analysis. It discusses various approaches to achieving explainability, applications in healthcare, and the challenges and future directions for research in this field. Guru et al. [29] present a novel approach to brain tumor identification and classification using an adapted AlexNet architecture, demonstrating significant improvements in accuracy and efficiency. The proposed method shows great potential for enhancing diagnostic processes in medical imaging.

Going over the various findings of the survey, we were able to understand the shortcomings of the various approaches and learn about the future scope of possibilities. We concluded that there is room for advancement and improvement by the application of different approaches to deep learning and models while also building systems around it to make it a complete product.

## 13.3 PROPOSED ARCHITECTURE

To implement the above-stated pneumonia detection model, we followed the architecture outlined in this section.

We selected a dataset of chest X-ray images, which was available from an online Kaggle data repository. The chest X-ray images, both anterior and posterior, were chosen from “Guangzhou Women and Children’s Medical Center, Guangzhou”. The X-ray images had been collected previously through various checkups and studies done as part of their routine.

We opted to use a simple HTML website for the UI. The website provides the functionality to select the image from the host system's file directory. Then, it feeds it to the model, and the result of the model is displayed on the website. It is implemented using FastAPI, which provides an API for transferring images and data.

Docker is used to provide access to the model to anyone who wishes to apply it for pneumonia detection. A Docker image is created, which will allow medical professionals to pull and create Docker containers, so as to implement the pneumonia detection model in their workflow.

In Figure 13.1, we present the architecture diagrams, in which we can observe the various layers of the deep learning model based on convolutional neural network or CNN. The expected input size of the VGG16 architecture is 224 × 224 × 3 dimensions of images. It then applies 3 × 3 filters in the convolution layers for feature extraction, which are combined to create larger feature sets in the pooling layers. The activation function is used in ReLU or rectified linear unit.

![](img/8c9c25929b8bfe55c61ba059d5462e42_338_0.png)

FIGURE 13.1 Overview of VGG16 architecture and its layers

## 13.4 MODULES

Following a modular approach for our system allows for the swapping of modules for experimentation and adaptability according to new needs. For example, if we wish to switch the deep learning model, we can simply swap the model without having to change the other modules. Listed below are the modules of the proposed system:

### 13.4.1 COLLECTION OF Chest X-RAY IMAGES TO TRAIN AND TEST THE MODEL

This module deals with the aggregation of chest X-ray images, from various patients. This stage requires both pneumonia and normal chest X-ray images. These images are obtained from “Guangzhou Women and Children’s Medical Center, Guangzhou”, collection of chest X-ray images, available on Kaggle for research and experimentation.

### 13.4.2 PREPROCESSING THE IMAGES

Preprocessing of images is an important stage in every image-based work. It encompasses various processes ranging from image resizing to changing of color dimensions to horizontal and vertical flipping. These processes are done to make the image a better fit for our model in terms of expected dimensions as well as for feature extraction processes. For our work, the images are rotated, color balanced, resized, shifted, and cropped based on a trial-and-error basis, until we find that the best possible results are obtained for the set of preprocessing operations done on the images.

### 13.4.3 TRAINING OF THE VGG16 DEEP LEARNING MODEL

Training the model in the case of a classification problem is the process wherein the inputs whose labels we are aware of are given as input to the model for it to learn the features and train its weights accordingly. Doing so will allow it to classify the input images whose labels we are trying to obtain. In this module, the preprocessed training images of the chest X-rays are fed to the VGG16 model, and the training process is carried out in this module. After obtaining the trained model, we test the model and obtain its accuracy.

### 13.4.4 PREPARING USER INTERFACES FOR THE MODEL

User interfaces (UIs) are implemented to allow for the abstraction of the functionality of a system, for ease of access and usability. For our system, a UI is built using HTML, and a FastAPI server is set up to allow the frontend UI to communicate with the model. The UI will allow for selecting images easily and clear representation of the output of the model.

### 13.4.5 DEPLOYING ON DOCKER

Docker is a cloud-based platform where independent systems can be uploaded to be shared and reproduced anywhere and on any system. It allows any user with the Docker system setup to pull an image and run as many of these independent systems they wish to run in containers. These containers are independent from each other, and they do not require the dependencies to be installed separately, as they are included as part of the instructions in the image. Thus, after the model and the UI are ready, the files are containerized and the Docker image is prepared to allow for the distribution of the model for whoever wishes to use it.

## 13.5 ALGORITHM

In this section, we go over the algorithm, which provides an overview of our work.

![](img/8c9c25929b8bfe55c61ba059d5462e42_340_0.png)

FIGURE 13.2 Algorithmic flowchart for the proposed work

**Repository link:** https://github.com/yash-seth/Pneumonia-Prediction-DL

## 13.6 IMPLEMENTATION

In this section, we go over the implementation details of each of the modules which are part of the proposed system. We go over the step-by-step process involved in the implementation of each module.

### 13.6.1 IMPORTING THE NECESSARY LIBRARIES

- Step 1: Import the modules – Input, Lambda, Dense, Flatten, and Global AveragePooling1D from keras.layers library.
- Step 2: Import model module from keras.models.
- Step 3: Import VGG16 and preprocess_input from keras.applications.vgg16 library.
- Step 4: Import image module from keras.preprocessing library.
- Step 5: Import ImageDataGenerator from keras.preprocessing.image library.
- Step 6: Import sequential module from keras.models.
- Step 7: Import numpy.
- Step 8: Import glob from glob.
- Step 9: Import matplotlib.pyplot.
- Step 10: Import tensorflow.

### 13.6.2 PREPROCESSING ON THE INPUT RAW IMAGE

- Step 1: Import ImageDataGenerator from keras.preprocessing.image library.
- Step 2: Pass the following parameters to create an object of the ImageDataGenerator class for the training dataset preprocessing: rescale = 1/255, width_shift_range = 0.1, height_shift_range = 0.1, shear_range = 0.2, zoom_range = 0.2, horizontal_flip = True, rotation_range = 20
- Step 3: Pass the following parameters to create an object of the ImageDataGenerator class for the test dataset preprocessing: rescale = 1/255
- Step 4: Pass training images to train_datagen.flow_from_directory to normalize them. Pass the following parameters: path, target_size = (224, 224), batch_size = 32, class_mode = "categorical"
