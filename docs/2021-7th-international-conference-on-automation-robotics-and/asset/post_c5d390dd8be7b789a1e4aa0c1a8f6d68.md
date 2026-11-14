
## Accurate Gridless Indoor Localization Based on Multiple Bluetooth Beacons and Machine Learning

Konstantinos Kotrosios
School of Science and Technology
Hellenic Open University
Patras, Greece
kkotrosios@gmail.com

Theofanis Orphanoudakis
School of Science and Technology
Hellenic Open University
Patras, Greece
fanis@eap.gr

*Abstract*—In this work we present an indoor location method using smartphones as a source of location information. The proposed method uses the Received Signal Strength Indicator (RSSI) value from Bluetooth Low Energy Beacons scattered around interior spaces. We present the results of our model using machine learning, which was developed based on measurements of RSSI values from Beacons inside a lab environment occupying a space of 31m². Measurements were fed to the open-source TensorFlow framework to develop an estimator of the distance between the mobile phone and the beacon. Next, based on the cross-sections of peripheral lines having as a center the location of the Beacons and radius the predicted distances we compute the intersection points from all circles and base our position estimation on the Geometric median of intersection points. Through experiments, we show that our system has an average accuracy of 69.58cm and can predict position with an accuracy of less than a meter in 80% of the cases.

*Keywords-Indoor Localization, Bluetooth, Beacons, Machine Learning*

### I. INTRODUCTION

Indoor positioning systems are becoming a vital part of the so called Internet of Things (IoT) [1] and applications used to estimate the location of a subject in areas like malls, airports, libraries, hospitals, etc., which are enablers for services such as context-based advertising, indoor navigation, robotics applications, emergency response, assisted living, etc.

There are many systems available for outdoor positioning GPS, A-GPS, Galileo, etc. However, they are available only outdoors and cannot provide the necessary accuracy for an indoor positioning application. For example, GPS can provide maximum accuracy of 5 meters. An accuracy not suitable for interior areas.

Many techniques have been developed to estimate the location in interior environments based on different techniques, such as, UWB signals [2], ultrasounds [3], RFID [4], Channel State Information (CSI) in WiFi networks [5], [6], etc. But all these methods require specialized hardware and therefore cannot be used on smartphones in our case, where we want to develop a system with no use of any special hardware.

Indoor localization approaches based on RSSI measurement of wireless signals such as WiFi and Bluetooth [7] are the most popular due to their low infrastructure cost, their use in all smartphones and potential high accuracy. The majority of approaches used today are based on Wi-Fi signals to estimate indoor locations. Additionally, most usually they are using algorithms to estimate the distance from a known position.

The remainder of the paper is organized as follows. In section II we review the related recent work in the literature. In section III we summarize the basics of our positioning model approach. Section IV describes the data collection process for the development and training of our machine learning model. In section V we provide a detailed description of our model. Finally, the paper concludes with presenting the results in Section VI and a discussion and conclusions in Section VII.

### II. RELATED WORK

Indoor positioning and accurate location tracking are open research problems that have attracted the interest of many researchers in recent years [7], [8], which have used different approaches based on different technologies and exploiting different methods to address them. Methods of indoor localization are usually based on monitoring the radio signal strength, the so-called Received Signal Strength Indicator (RSSI) value from wireless signals such as WiFi and Bluetooth [9]. The RSSI from wireless signals and specifically from Beacons (low-cost transmitters based on Bluetooth low energy that broadcast their identifier to nearby mobile devices) is the most popular method with many researchers using this method as a solution in recent years.

Authors in [10] proposed an Iterative Weighted K Nearest Neighbors (IW-KNN) method based on RSSI of the BLE. They propose three principal improvements. First, Euclidean distance and Cosine similarity are combined to measure the similarity of two RSSI vectors, which can take both length and direction of the vector into consideration. Second, unlike traditional k-NN which estimates a position by a majority vote of its neighbors, a weighting factor is applied to neighbors for localization. Third, IW-KNN selects different iBeacons to obtain RSSI at each iteration and calculates the mean position as the final result after several iterations. They can estimate positions effectively and reduce the mean error by 1.5 to 2.7 meters in an experimental environment dividing the interior space in a dense grid with a size of 60cm. In [11] a k-NN algorithm is proposed based on the Bluetooth fingerprint library location method also dividing the interior space selecting a grid with a size of 1m. The k-NN algorithm processes the matching of measured RSSI value and the closest value in the fingerprint library. The positioning accuracy is controlled within 1 meter and basically controlled within the designed grid, thus realizing the positioning requirements.

### III. OUR MODEL

Our positioning model introduces a system for finding indoor locations with high precision in real-time by making use of the Bluetooth RSSI values obtained from smartphones. We chose to make use of Bluetooth Beacons because they have several advantages against other indoor localization technologies. The main advantage of this approach is that the cost for the required infrastructure is low, since it only requires a number of Bluetooth Beacons (we experimented with a ratio of 1 Beacon per about 6m² of internal space to achieve best coverage with no blind spots) scattered around the interior space in predefined and known positions (e.g. walls, ceiling etc.) [10], [11], [14], [15]. Additionally, smartphones are considered ubiquitous and can be the optimal device that can enable internal location tracking of humans (else any other embedded Bluetooth device for tracking “things” equipped with such sensors).

The proposed Trilateration algorithm in [12] is an easily implemented solution due to its low complexity and operates independently of any predefined grid. On average this system has an error of about 1 meter. In [13] authors experimented with mathematical filtering functions to smooth RSSI and improve accuracy. They use functions like median, mode, single direction outlier removal, shifting and feedback filtering. For position calculation, they use a trilateration algorithm and achieve an accuracy of about 1-2 meters.

We can divide our internal location estimation approach into three phases.

- In the first phase, our system makes use of a set of machine learning models (one for each Beacon deployed in the interior space). These models are used to predict the distance from the smartphone and a specific Beacon based on the current RSSI level measurement and its comparison against past measurements collected and used during the training phase.

In recent years, many efforts have been made to make use of machine learning algorithms for indoor location systems. In [14], a machine learning approach to indoor positioning for mobile targets based on BLE signals is proposed. The authors in [14] design a feature vector for the position prediction and perform machine learning with well-known decision-tree based algorithms, which is shown to achieve a predictive accuracy less than one meter. In [15] a BLE based machine learning location and tracking system for indoor positioning with experimental results is proposed showing that this method has an average estimation error of 50 cm.

- In phase two our system takes as input the distances from the Beacons from the first phase and calculates the peripheries of circles that have as a center the Beacons’ location and as a radius the distances found in phase one. After that, we find the intersection points of all circles.

Following the advances described above we have been investigating methods that can exploit the latest powerful machine learning technologies to solve the problem of indoor location with an accuracy much closer than 1m based on low cost solutions. Machine learning is becoming ubiquitous, with the cost of hardware reducing fast and new methods and tools providing efficient solutions to a large number of problems related to the processing of signals from sensor and IoT networks in order to enable smart applications and lead to actual Artificial Intelligence. Therefore, in [16] we presented a system where we use a smartphone to find the location by using the measured RSSI value from Bluetooth Beacons combined with measurements from other smartphone sensors and feeding a machine learning model. The approach of our past work in [16] was based on the selection of a grid layout of the interior space, against which the user positioning was attempted based on the signals received from the Beacons installed in fixed locations, i.e. similar to the approach followed in [10] and [11], however with improved accuracy i.e. accurate user positioning within less than a meter.

- In the third and last phase, our system gets as input the intersection points from phase two and finds the geometric median from the intersection points. This geometric median point is defined as the estimated location.

In this work we present an improved method, which can exploit powerful machine learning as in [14], [15] and [16] but can also achieve improved performance, while operating in real-time and independent of any interior grid layout. In this work, we develop a machine learning model to solve a regression problem. This way we overcome the need to select a predefined grid as was done in [15] and [16], which also simplifies the model training process and leads to improved accuracy. Additionally, we demonstrate an average accuracy of 69.58cm and we can predict position with an accuracy of less than a meter in 80% of all cases. It is important to stress that our method can operate in real-time, while the grid-based method presented in [15] can achieve comparable results at the cost of repeated RSSI measurements at each location, which can be applicable only for semi-static and not actual mobile users.

### IV. DATA COLLECTION

The first step in developing our system was to set up a data collection procedure to train and evaluate our neural network models for phase one of predicting the distance from Beacons.

To create the data collection, we used five iBKs105 Bluetooth Beacons from Accent Systems that we placed in different locations around a 31m² apartment “Fig. 1”. The locations of the Beacons are fixed and we know the distances (x and y) from the lower left corner of the apartment for each Beacon.

Then by using an application that we have developed on Android for a commercial smartphone we started to move around the space of the apartment and take measurements. For each measurement, we record the current position of the mobile (distance from upper and left walls x and y), the RSSI values for all five Beacons, the distance from each Beacon, and the timestamp of the moment we took the measurement. The mobile phone we used to collect the data is a Xiaomi Mi A1.
