
fact that it is not restricted or limited to one or couple of systems but the fact that it has the ability to link every possible sensor and actuator to build up an actually complete system. This is the underlying concept behind the inception of IoT. Entire cities can get network-based connectivity. One area that could be greatly improved by this technological advancement is of the transportation system. The expanse of a typical and entire transportation system of a city is so tremendous and vast that it only makes it logical to implement IoT and reap the rewards of it leading to intelligent transportation systems (ITS). An extremely important area that could be worked upon by using IoT is the department of route optimization. This could be done by using the input from drivers’ hand-held devices or with any other sensor along the commuting route for correctly analyzing the traffic situation for prompt update to future passengers on that route [15] and eventually leading to lesser fuel consumption and emission of harmful gases. This can be done by integrating sensors or cameras in street lights for effective monitoring and surveillance for security purposes as well [16]. Many experts have also proposed the idea of developing a parking system based on the principles of IoT as it can promptly notify the user in case of a vacant parking spot using simple IR and proximity sensors [16]. This could be of immense help and use to the general public and increase their productive time as they are not wasting it on a meaningless job just to park their car.

## 5.2 TRENDS OF SMART TRANSPORTATION SYSTEM

This section of the chapter provides a basic gist of the smart transportation system and all the limitations associated with it. As nearly as six different divisions of issues involved in it are identified, and their possible solutions are presented in this section. The solution is derived with the use of technologies such as ML and IoT algorithms. Table 5.1 depicts the categories of issues and their references along with it.

**Table 5.1** Smart Transportation Current State of the Art

| S. No. | Smart Transportation System Application | Articles to Read |
|---|---|---|
| 1 | Parking | [16,18,19] |
| 2 | Road anomalies | [20–24] |
| 3 | Navigation | [25–29] |
| 4 | Infrastructure | [17,30] |
| 5 | Lights | [31–33] |
| 6 | Accident detection | [34–37] |

### 5.2.1 Route Optimization-Navigation

Urban and metropolitan cities often have a major nuisance with their transportation systems called traffic congestion or overcrowding. This problem will only grow with the rapid increase in population and increased attention toward migration to urban cities for finding livelihood. A solution that could be presented using IoT and ML algorithms is of route optimization. This is basically a technique that could provide any particular driver with the shortest route to any destination by accounting in all of the external factors. These factors can include time of day, weather conditions, road surface conditions and any other possible vehicle accidents. This could lead to ground-breaking development as it can prove valuable in not only providing comfort to the general public but also help in reducing road accidents. Emission of harmful gases can only be reduced if the vehicles are made to run for a shorter duration [15]. Several ways of implementing a route optimization algorithm have been proposed. One of them is by using an Markov decision process (MDP) algorithm that establishes a communication between vehicles for a group route. This will lead to entire groups of vehicles collaborating with each other with the same destination for a collective effort [38]. The other approach that has been proposed is a ML technique of implementing k-means and deep belief network (DBN) networks to streamline the traffic situation [25]. Several other literatures have provided background on different types of traffic forecasting. Short-term forecasting of traffic is handled in [39], and several other techniques such as FF-NN, Nonlinear Autoregressive (NARX) model and Seasonal Autoregressive Integrated Moving Average (BN-SARIMA) have been proposed for it. The same problem along with its counterpart are dealt in [28] with respect to application of four ML algorithms. These four algorithms are then tested among each other for performance and result evaluations. These four algorithms include baseline predictors, RF, FF-NN and a regression tree. FF-NN and baseline predictors are also used in [29] to estimate variations in time and total duration of the journey.

Researchers in [27] implemented a logistic regression model along with support vector machine algorithms and other models to predict traffic conditions. Lv et al. [40] used advanced data analytics and extraction to perform operations on the sensor data to predict the basic flow of traffic. The approach makes use of stacked autoencoder.

Swarm intelligence algorithms are a new department in computer science as they are nature-inspired algorithms and show great performance in modeling real-life systems. One of them is the ant colony optimization algorithm that could be used in conjunction with mobile crowd-sensing for ITS. The passengers are able to communicate with them for data regarding routes, surface conditions and other factors to find out less congested routes. This draws an analogy to how ants find their way to food by following the secretion of pheromone/chemicals [43].

Implementation of a different algorithm for route optimization is done in [42]. It makes use of a vehicular ad-hoc network that gathers traffic situation using mobile navigation devices and optimizes the route. This is similar in comparison to the above-mentioned techniques as it lets vehicles interact between them to share the traffic conditions.

The research in [43] takes a different approach of crowdsourcing the route planning by making use of a mobile application. An application by the name of Crowd Navi is installed on mobile devices, which wirelessly uploads the information about a particular traffic area to the Internet and among various vehicles.

### 5.2.4 Accident Detection and Prevention

Accident prevention is major issue associated with the transportation system of any city. It is probably the most impacting event and hence must be taken into account very seriously as it directly affects the lives of people. A great deal of road accidents can be prevented if the drivers are focused on their commute, provided that they are abiding all the traffic rules. Smarter facilities in the transportation network can also help us detect already happened accidents at the earliest to supply them with emergency care measures.

The research article [35] uses a CHMM technique to exchange information between the vehicles in real time to prevent collisions and crashes. This way of preventing accidents but autonomously is presented in the research article [47] which also makes use of road sensors data fed into a FF-NN and regression tree algorithm. The basis of all techniques is the V2V (vehicle-to-vehicle) communication for an overall smarter decision [37]. Another important aspect is touched upon in [26] where along with V2V communication, blind-spot identification is also done using the Fully Convolutional Layer (FCN) method. This can also be implemented using the deep recurrent attention model (DRAM) method [48] which is based upon image processing and object detection. Driver consciousness [49] can also be monitored using image data and by using different computer vision techniques. These images can also be fed into a neural network to work up for most accurate and reliable results [36,50].

### 5.2.5 Road Anomalies Detection

Condition of road surface is another very important parameter that directly affects the flow of traffic and vehicle degradation. Effective and efficient identification of potholes and bumps will let users know beforehand of the caveats of any route and will present them with an option to change it accordingly.

The review paper [20] presents an elaborate take on the different deep learning techniques used in learning the surface of different pavements and roads. It makes use of as many as 12 of the most recent studies done in the same field. The neural networks that are employed are CNN and Deep convolutional neural network (DCNN). The techniques are pitted against each other with vital parameters such as performance, results, reliability and frameworks measured. The author finishes off with the opinion that CNNs perform the best when classifying pavement images.

### 5.2.6 Infrastructure

With the recent advancement in IoT technology, conventional transportation systems can benefit greatly from it. The transportation system can be improved with much smarter working modes that can provide comfort at any level. The following paragraphs enlist the ways in which it can be done.

The research article [51] provides a mix of hardware and software to monitor bus fleets. This is done by using RFID tags, with each bus being uniquely identifiable and IR sensors fitted in the buses to count the number of passengers in a particular bus. GPS sensors are used to give information about the location of the vehicles. The
