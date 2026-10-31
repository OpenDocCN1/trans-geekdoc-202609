
## Smart Cane: Obstacle Recognition for Visually Impaired People Based on Convolutional Neural Network

Adnan Hussain¹, Bilal Ahmad¹ and Muhammad Imad²,*
¹ Islamia College University Peshawar, Peshawar, Pakistan
² Abasyn University, Peshawar, Pakistan

**Abstract:** According to the World Health Organization (WHO), there are millions of visually impaired people in the world who face a lot of difficulties in moving independently. 1.3 billion people are living with some visual impairment problem, while 36 million people are completely visually impaired. We proposed a system for visually impaired people to recognize and detect objects based on a convolutional neural network. The proposed method is implemented on Raspberry Pi. The ultrasonic sensors detect obstacles and potholes by using a camera in any direction and generate an audio message for feedback. The experimental results show that the Convolutional Neural Network yielded impressive results of 99.56% accuracy.

**Keywords:** Convolutional Neural Network, Raspberry Pi, Ultrasonic Sensors, Voice Message.

## INTRODUCTION

According to the World Health Organization, at least 2.2 billion people have vision impairment problems, of which 1 billion people have preventable or yet to be addressed. The world faces extensive challenges related to eye care, including treatment, shortage of trained eye care service providers, and poor integration of eye care in the health system [1]. The report was released on World Sight Day to warn the population of aging, an increasing number of vision impairments, and blindness problems from different eye diseases, such as Presbyopia, affecting 1.8 billion individuals, which can occur at an early age. Myopia affects 2.6 billion, with 312 million under the age of 19. Other diseases are cataract, which affects 65.2 million, glaucoma affects 6.9 million, corneal opacities affect 4.2 million, diabetic retinopathy affects 3 million, trachoma affects 2 million people, which is the cause of vision impairments [2].

A visually impaired person faces many difficulties that take a sighted person's aid to find their way. In an unfamiliar environment, blind persons can't find their path themselves. Generally, visually impaired persons use a white cane or walking cane. Electronic Aid technology like Ultrasonic sensors can be used to help visually impaired persons. In the ultrasonic system, energy waves are emitted, reflecting from the obstacles on any side (left, right, front) to help the visually impaired person detect the obstacle within the defined range. The distance between visually impaired persons and the objects is calculated according to the starting and ending pulse from the ultrasonic sensor. We have used a buzzer sensor to inform the blind user about the obstacles. Suppose the obstacles are too close to the blind user. In that case, the proposed system will generate a voice message, and also, a buzzer will be active to inform the visually impaired person about the obstacles. The main objectives of the smart cane system are to develop a model of cane for the blind, which is widely used in mobility. The second objective is to design a proposed model that consumes less power, is weightless, and has precise, accurate object/obstacle detection and recognition performance. This proposed design can provide full support against obstacle avoidance with a voice message. The proposed module will be useful for blind people. It is easier for them to find daily activities without using the standard mobility aid and available for individuals with this disability since mobility aids are less costly, light in size, and can be taken easily anywhere.

The Nivedita presented an electronic aid device consisting of a Raspberry pi device, an ultrasonic sensor, a webcam microphone, and an LDR sensor. The ultrasonic sensor with a camera has been used to detect obstacles. The LDR sensor has been used to detect the brightness of the environment to check whether there is dark or bright automatically. The proposed system detects the object around the visually impaired person and sends feedback by voice using a microphone [3].

The Mary presents a Raspberry pi-based system for blind people with unique features, such as tracking the object around, sending feedback through voice, and providing information about the environment. The most important feature of the paper is to track the location of the blind person and notify the caretaker to ensure safety [4].

The rest of the paper comprises a literature review in Section 2, details of the proposed methodology (convolutional neural network) are given in Section 3, experimental result analysis, and discussion in Section 4. Finally, the paper is concluded in Section 5.

## LITERATURE STUDY

The Tapu has been implemented as a smartphone-based obstacle detection and classification to aid visually impaired people to walk freely and safely in an indoor and outdoor environments. The Lucas Kanade algorithm has been used to extract the feature from images or frames [5].

The camera and the background motion have been estimated through homographic transforms. The obstacles are detected as critical or normal, based on a specific distance, and then the obstacle has been detected and recognized [6].

The model has been proposed, which they used for obstacle detection techniques. Two methods have been used: adaptive colour segmentation and stereo-based colour homography. The pixels are classified into a frame or image in colour segmentation to find the obstacle or free space. The present system has been built on a training algorithm [7].

The proposed design model consists of a 2D laser scanner, foot-mounted pedometer, and three-axis gyroscopes to aid visually impaired people in an indoor environment. They presented 2-layered estimators. In the first estimated layer, the blind cane location has been tracked in the first layer. The second estimated layer finds the person's location keeping a blind cane is tracked [8].

Rodríguez presented a method for obstacle prevention devices to help visually impaired persons. They have implemented an incremental map of the environment with the help of optical SLAM techniques to provide spatial direction and location of the visually impaired people at the same time. The proposed design also provided audio feedback to inform the blind person about obstacles [9].

The electronic aid device consisted of three ultrasonic sensors and a microcontroller to detect the object range. The audio and vibration system also has been used to warn visually impaired people to avoid obstacles [10].

Pradeep proposed a device that involves an RGB-D camera for environment perception. The proposed system imposes three things; self-localization, obstacle detection, and object recognition. In self-localization, depth has been perceived based on the tracking technology of colour information. Obstacle detection and recognition provide meaningful information to visually impaired people and help recognize the obstacles such as stairs, walls, vehicles, and doors [11].

Leung has proposed a head-mounted, stereo-vision-based direction system for visually impaired people. They have used visible odometry and feature-based SLAM in the proposed design system to make a 3D map for obstacle detection [12].

Shahdib designed a model that involves the head-mounted stereo vision to search ground planes and break up six degrees of freedom (6DOF) into ground plane motion and planar motion which assist visually impaired people. Due to the investigation of the variation array, they evaluate the ground plane and normal to the ground plane using optical/visible data or with the IMU reading [13].

Maidenbaum implemented a system based on ultrasonic sensors and a camera for obstacle detection and recognition. The camera has been used to recognize and measure the size of obstacles [14].

Patil designed a system based on two infrared emitter (IR) sensors to emit and receive beams. The sensor has been used to detect waist-level obstacles within a five-meter range and ground-level obstacles at 45 degrees to provide direction to visually impaired people [15].

## MATERIALS AND METHODS

### Dataset Description

The dataset consists of different obstacles, such as Vehicles (1,510 images), Doors (1,349 images), Pillars (1,559 images) and Stairs (1,300 images), through various operations and variations to make it in perfect shape. The dataset has been created from the short videos through a Raspberry pi camera, and each frame is extracted from the videos with a size of 640×480 in width and height. The primary rule of deep learning is to divide the data into two parts, training and testing phases, while 70% of the dataset is used for training and 30% for testing purposes (Fig. 1).

### Methods

This paper aims to detect and recognize the obstacles (Vehicles, Doors, Pillars, and Stairs) for visually impaired people based on the deep convolutional network. The number of steps involved in our proposed system explained in this section is presented in Fig. 2.
