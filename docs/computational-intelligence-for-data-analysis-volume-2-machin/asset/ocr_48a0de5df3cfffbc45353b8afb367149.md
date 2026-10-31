based SLAM in the proposed design system to make a 3D map for obstacle detection [12].

Shahdib designed a model that involves the head of mounted stereo vision to search ground planes and break up six degrees of freedom (6DOF) into ground plane motion and planer motion which assist visually impaired people. Due to the investigation of the variation array, they evaluate the ground plane and normal to the ground plane using optical/visible data or with the IMU reading [13].

Maidenbaum implements a system based on ultrasonic sensors and a camera for obstacle detection and recognition. While the camera has been used to recognize and measure the size of obstacles [14].

Patil has been designing a system based on two infrared emitter (IR) sensors to emit and receive beams. The sensor has been used to detect waist-level obstacles within a five-meter range and ground-level obstacles at 45 degrees to provide direction to visually impaired people [15].

# MATERIALS AND METHODS

# Dataset Description

The dataset consists of different obstacles, such as Vehicles (1,510 images), Doors (1,349 images), Pillars (1,559 images) and Stairs (1,300 images), through various operations and variations to make it in perfect shape. The dataset has been created from the short videos through a Raspberry pi camera, and each frame is extracted from the videos with a size of 640,480 in width and height. The primary rule of deep learning is to divide the data into two parts, training and testing phases, while 70% of the dataset is used for training and 30% for testing purposes (Fig. 1).

# Methods

This paper aims to detect and recognize the obstacles (Vehicles, Doors, Pillars, and Stairs) for visually impaired people based on the deep convolutional network. The number of steps involved in our proposed system explained in this section is presented in Fig. (2).