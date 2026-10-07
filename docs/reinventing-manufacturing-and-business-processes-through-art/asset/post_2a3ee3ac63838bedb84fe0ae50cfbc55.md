
# Rise of AI in Modern Healthcare Sector

The BCI headset has an adjustable headband. A power supply, a microcontroller, dry electrode and reference electrode are mounted on the head. The position of the dry electrode is on the frontal part on left side and reference electrode has to plug into the left ear. The hardware structure for testing a miniature wheelchair is having HC-05 Bluetooth module to receive signal from Android application, a motor driver that controls the movement of the wheel based on instructions and a microcontroller module that processes signal received from Bluetooth and provide instruction to motor driver. The wheelchair is equipped with four motors and respective wheels. The motor driver has four DC motors connected to it, and responsible for both speed and direction control. The Android application plays the role between the headset and wheelchair.

### 3.2.3 Working

- First, turn on the BCI headset and connect it with Android application and wheelchair with Bluetooth.
- Trigger command mode using blinking. Once direction cycles, blinking at least twice selects the direction and focus mode.
- To get the robot running, try to focus on something to get focus level at least 50. Once attention level reaches value of 50, running mode will be triggered and the robot will start based on whatever direction selected earlier.
- Whenever needing to stop running, blink consecutively at least two times.
- If wanting to run again, blink once to trigger operation. Controlling the robot using BCI headset command and direction cycle proposed by Jadhav and Momin (2018).

### 3.3LLIGENT VISION

Intelligent vision is a micro-controlled system that takes input using camera and provides output as audio signal to visually disabled person. The image captured by camera is processed by machine learning for image processing to identify surrounding objects. In this system, we have face recognition, object recognition using machine learning and output module as shown in Figure 3.6. This intelligent vision device for widely challenged people so this device contains multiple features. Our startup code does not contain anything but just to import files; whenever user can use any features they want in the startup code.

![](img/b43ebeccbd4344aca82fb570_66.png)

# Reinventing Processes Through AI

Head mount belt
Microcontroller
Camera

FIGURE 3.6 Head mounted intelligent vision. The startup code will do everything that is on its own. This device consists of headband and camera module, microcontroller and control button mounted on it. Recognition for face, objects are performed by machine learning. Different techniques of machine learning are used to implement these features which startup code contains the following:

### Module for Facial Recognition

This module contains code of facial recognition. In this module, do not have to pass any argument; after calling it, start using camera for picture and then it will predict the name of the person according to dataset. If unknown person on runtime, then add as parameter so that device can recognize the person.

### Module for Object Recognition

This module will also work the same as facial recognition; it does not require any parameters and will also work same way as facial recognition, returning the name of object that was captured after calling the module. This module use pre-trained libraries "MobileNet"; we can directly import functions and use them in our code. When we use library which is not understandable by us, use separate file with names of objects called "COCO"; at the end as result.

Facial recognition initiates with feature extraction from stored image. Features are eyes, pupil, mouth and other facial points. The facial recognition system performs comparison of given face with patterns stored in database, and finds the closest (facial metrics). Facial recognition has numerous practical applications such as security, access control and surveillance systems; that is why in the last decade, number of algorithms have been published and show improvement in terms of identification. A formal method of classifying faces was first proposed by Galton (1888). Galton proposed a method for collecting facial profiles as curves and finding their norm, and based on deviations from the norm, classifies faces with other profiles. This type of classification is multi-model; it provides results in independent measures of vectors and these vectors could be compared with others in stored database. Continuous progress in algorithm and advancing technology has explored real-world application and implementation for facial recognition systems. Facial recognition in early stage works on detection of face patterns in clustered scenes; those clustered scenes normalize the images to calculate geometric changes (Chellappa et al., 1995).

The appearance of facial patterns identifies the faces using classification algorithms and model-based schemes and logic feedback. The availability of large databases of facial images, development of algorithms and evaluation methods are factors for rapid development and achievements of facial recognition. Facial-related applications have to provide a still image or a video clip, and the system has to find the person available in the image or in the video. This intelligent vision uses Python as a programming language and uses OpenCV and facial recognition libraries with it to recognize the faces. Basically, in this project, the code finds the encoding of people images from the database which we have to provide, and after that—based on that encoding—the code predicts the name of the face captured by the camera at runtime.

### 3.3.2 OBJECT RECOGNITION

There are multiple studies on detecting and recognizing objects from camera images. According to Donner et al. (2015), object recognition is basically a technique of classifying objects based on images captured or live video streams. The authors of “Object Recognition by Effective Methods and Computer Vision” designed new solutions for objects sensed by cameras to perform image recognition with the intention to detect and recognize objects. The camera module is used to first sense and receive objects, then determine and recognize them after prior processing of data provided by the camera. Neural network-based techniques like convolutional neural network (CNN) are widely used to perform the feature extraction that is the process of computer vision using neural-based methods. This type of recognition system may be used in various applications where recognition and tracking of objects and understanding of the real world is required. Nowadays, intelligent vision system is also adapted by automobiles to recognize objects in front of vehicle.

Khurana et al. (2016) in “A Survey on Object Recognition and Segmentation Techniques” used images and videos to analyze object recognition and segmentation techniques. Object recognition techniques are being used by numerous applications such as robot navigation, human-computer interface, medical diagnosis, security, industrial inspection, autonomous vehicles and drones. Segmentation is implemented in fields such as video recognition, image processing, human activity recognition, gesture identification, shadow detection, and many more. Many authors have performed systematic analyses of existing object recognition and segmentation methods with respect to precise and arranged parameters. In the field of object recognition, most of the techniques used are based on mathematical and algorithmic models.

### 3.3.3 CURRENCY RECOGNITION

Currency recognition which we are using is defined as the recognition of paper currency; here we are using this feature to predict the value of paper currency with the help of cameras. Murthy et al. (2016) in “Design and Implementation of Paper Currency Recognition with Counterfeit Detection” used a method that can classify and subsequently verify Indian paper currency using a trained model of previously stored currency images.

MANI (Mobile Added Identifier) is a system based on image processing; this application has launched by the Reserve Bank of India (RBI) for Android users. The MANI application provides aid for visually impaired people to recognize Indian paper currency notes using their mobile phone camera module. The application does not need an internet connection to operate. The MANI application is user friendly, and also supports English and Hindi languages. It gives out in the form of audio notification, and to support users with hearing impairments, the app has provided response in the form of predefined vibrations for different values of currency (Table 3.2). MANI is free to download and It is one of the best implementations of AI and mobile phone technology in healthcare for visually challenged and hearing impaired patients.

# Rise of AI in Modern Healthcare Sector

require AI model for this feature which we are going to program or create through Google’s Teachable Machine. Teachable machine is something which helps to make AI models by simply providing images to platform.

### 3.3.1 FACIAL RECOGNITION

Nowadays, there are many facial recognition algorithms and techniques available from around the world. According to Salakanidu et al. (2008), facial recognition becomes an interesting research topic and has wide variety of applications in healthcare and industry. Different machine learning and neural network techniques are used to implement facial recognition. Facial recognition is a significant research problem across different disciplines and fields. Facial recognition initiates with feature extraction from stored image. Features are eyes, pupil, mouth and other facial points. The facial recognition system performs comparison of given face with patterns stored in database, and finds the closest (facial metrics).
