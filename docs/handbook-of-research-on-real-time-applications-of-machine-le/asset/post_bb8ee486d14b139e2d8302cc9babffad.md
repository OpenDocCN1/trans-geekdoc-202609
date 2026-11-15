
## CYBER-PHYSICAL SYSTEMS FOR AGRICULTURE DOMAIN

In agriculture, mechanization is widespread. However, advances in robotics and autonomous systems will propel agriculture forward as a result of artificial intelligence and embodied systems applications (Tyagi, S.K.S., et al., 2020). A drone is a flying robot in and of itself, but when a generation of embedded intelligent CPS robotics systems is deployed, a substantial evolution will occur (Huo & Chaudhry, 2021; Rakesh Kumar Birda & Manish Dadhich, 2019). These systems can be interconnected, interdependent, collaborative, autonomous, and provide computing, communication, checking, and control of physical components and processes in various applications. In other words, by observing how these systems communicate with the physical world (including human users), Typically intended as intelligent sensor networks of (autonomous) systems with unique detecting and actuation capabilities, they play a key role in acquiring data (Jimenez et al., 2020). The cyber and physical worlds cannot be considered separate entities, yet they are inextricably linked with sensor/actuator integration in so-called cyber systems. By providing real-time control coming from conventional cyber systems, cyber systems became responsive to the physical environment. As a result, the concept of a CPS was born. The “assimilation of computation with physical processes” is what a CPS is. Sensors and actuators, for example, are used to connect computational systems to the real environment. CPS presented significant hurdles, especially because the physical components of such systems introduced safety and dependability; as a result, typical computing abstractions must be altered to meet qualitatively different requirements than those in general-purpose computing (Liao et al., 2021).

Furthermore, physical components differ fundamentally from object-oriented software components, yet concurrency is both inherent. It was a significant advancement in state of the art in computers (Malathi & Padmaja, 2021). The interaction of the “cyber” and “physical” aspects is crucial in CPSs; computation, control, sensing, and networking can be extensively interwoven into every component, and component and system behavior must be safe and interoperable (Myllyaho et al., 2021; Shalendra Singh Rao, n.d.). CPSs have been on the model of engineering research agenda in the United States, and since 2010, the European academic and industry community has focused on CPSs as paradigms for the future of systems. The industry as a whole has shown a lot of interest. This is evident when considering that embedded systems, wireless sensor networks, IoT, communication protocols, and their interactions are the most important elements and pillars in CPS (Hiran & Henten, 2020; N. Sharma & Dadhich, 2014). To move forward with CPS’s difficulties and prospects, there must be widespread agreement on fundamental principles and shared knowledge of the features and technology that are unique to CPS.

## RELATED WORKS

(Nerurkar et al., 2018) studied the technologies based on cyber-physical systems (CPS) created to monitor terrain parameters and make them available on a platform that multiple users can access. (Priyadarshini et al., 2021) studied that CPS can monitor entire agricultural areas and thanks to cellular telephony gateways and information monitoring systems that can display data on a web application. Other options include: Applying and implementing the new and helpful concept of Cyber-Physical Systems (CPSs) in the agriculture industry, which consists of a Zigbee-based network with nodes that function below the ground surface.

(Raza et al., 2018) assessed the mobile devices used in some of the most recent projects, which are advanced, comprehensive systems that monitor environmental factors and employ a closed-cycle control system in which actuators are controlled based on sensor data (Hiran, K. K., 2021). While it is only a theoretical solution, it still lacks a functional human-machine interaction sub-system. Several studies (Dadhich, Purohit, et al., 2021; Dinesh Setha, Minah Ahemad A.Rehman, 2018; Shen et al., 2020) developed Drone-based solutions to obtain picture data at various wavelengths to provide a continual overview of the terrain's physical and chemical state. Different types of camera-equipped drones are already on the market (for example, from Precision Hawk, senseFly, and Agribotix) that take medium-high resolution photographs (up to 20 MP) in various electromagnetic spectrums regions, usually in the visible and Near Infrared (NIR) fields (M. Dadhich, M. S. Pahwa, 2021; Restrepo et al., 2021). Different types of camera-equipped drones are already on the market that take medium-high resolution photographs (up to 20 MP) in various electromagnetic spectrums regions, usually in the visible. The Spanish startup Agroptima is working on another unique system (Kumar Naresh, Dadhich Manish, 2014). This system does not use hardware such as sensors or actuators. Still, it does provide a stunning graphic interface for field cataloguing and management, as well as irrigation and fertilization planning. (R. Sharma et al., 2020) studied agrodron used for parasite control and made it ideal for spraying activities on crops.

## PROPOSED FRAMEWORK

Data preprocessing, forecasting, and classifying are the three primary processes in machine learning-based architecture (Manish Dadhich, Manvinder Singh Pahwa, Vipin Jain, 2021; Shubham Tripathi and Manish Gupta, 2021). The data will then be measured using a forecasting algorithm to avoid data shortages or inaccurate data collection for the following sensing cycle. The data classifier uses a Naïve Bayes classifier to predict a real-time event using a discretized fusion of forecasted data and prior knowledge (Dadhich, Rao, et al., 2021). In each time cycle, the event prediction is calculated.

### Normalizing Data

The best way to overcome this problem is to use normalization to produce data in the same interval. The normalizing method is used to scale each feature element to interval values with a range of [0–1]. In the first equation, the implementation is shown. I denote each source index, and j is a normalized element index in sensor I.

```
\(\hat{x}_{ij} = \frac{x_{ij} - x_{i\max}}{x_{i\max} - x_{i\min}}\)
```

### Handling Incorrect Data

Due to a variety of variables, data acquired from diverse sources such as sensors can occasionally be incorrect or null. We suggest a novel approach for predicting faulty data rather than discarding all of the data or altering the incorrect value to a random number to address this issue. After that, we estimated the average of proximity between all existing normalized values in all data at the time_t () and source (i) where the event of the wrong value happens. The process of forecasting inaccurate data is depicted in the second, third, and fourth equations.

```
\(\phi(i) = \sum_{j=1}^{N-1} (\hat{x}_j - \hat{x}_{(j+1)}) \text{ for } \hat{x}_{(j+1)} \neq null\)
```

```
\(k_i = \phi_i x_{i\max}\)
```

```
\(xf(i)_j = \frac{\sum_{i=1}^N k_{(j+1)} + \sum_{i=1}^N k_{(j-1)}}{2}\)
```

### Information Fusion

After that, we estimated the average proximity between all existing normalized values in all the data at the time_t () and source (i) where the wrong value event happens. The process of forecasting inaccurate data is depicted in the second, third, and fourth equations.

```
\(\hat{x}_t = \frac{\sum_{i=1}^N x_i^t w_i}{N}\)
```

### Prediction Method

To predict the consecutive data at the time, we utilize a single aggressive smoothing forecasting method. The method is selected for the actual value that does not have a significant trend and seasonal behavior at each subsequent time. The exponential smoothing method is defined as the 6th equation.

```
\(F_t = F_{(t-1)} + \left(A_{(t-1)} - F_{(t-1)}\right)\)
```

### Naïve Bayes Classifier

To choose based on the data sources available at the moment (t). The probabilities or conditional opportunities are expressed as the 7th equation using the Bayesian theorem

```
\(P\left(H \mid X\right) = \frac{P\left(X \mid H\right) P\left(H\right)}{P\left(X\right)}\)
```

P(H | X) is the probability of having the correct value of H assumption for true X evidence for H assumption or posterior probability of X with H, where X is a proof and H is an assumption, and P(H | X) is the probability of having the correct value of H assumption for true X evidence for H assumption or posterior probability of X with H, where X is a proof and H is an assumption, and P(H | X) is the probability of having the correct values (H) is the prior probability of evidence X, and P (X) is the preceding hypothesis probability of H. There is a presumption that tuple X is located
