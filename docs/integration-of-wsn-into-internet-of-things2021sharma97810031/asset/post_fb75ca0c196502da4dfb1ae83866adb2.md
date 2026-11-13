
![](img/0b5412a09266b61a5c216084aa99aac2_143_0.png)

FIGURE 7.1 Setup of the smart irrigation system.

read values are compared with the set threshold limits. If the read inputs exceed the threshold, then the DC motor is turned on automatically.

Also, the live data feed is stored on cloud (ThingSpeak.com) to make an analysis via Wi-Fi module, and the updated results are shown on LCD and prompted to the farmers with the help of the GSM module.

## 7.4.3 COMPONENTS

The components of the proposed system are shown in Figure 7.3. It works on the WSN technology. Sensors are connected to a WSN to gather real-time data and monitor various environmental parameters. The features being collected are soil temperature, soil moisture, climate temperature, and humidity. Various weather conditions are also captured to manage water resources. Cloud-based ML algorithms

![](img/0b5412a09266b61a5c216084aa99aac2_144_0.png)

FIGURE 7.2 Workflow of the smart irrigation system.

are implemented to assist farmers for decision-making. The major components are sensor nodes, IoT gateway, and cloud services.

### 7.4.3.1 Wireless Sensor Network

The WSN is a wireless network comprising an Arduino microprocessor and sensors. The sensors are to capture the readings for soil moisture content, soil pH level, soil temperature, ambient temperature, solar radiation, atmospheric pressure, and humidity content in air. The protocol to transfer the sensor data to the gateway and among the nodes is ZigBee. Figure 7.4 demonstrates the sensor inserted in a plant to read the soil moisture, soil pH level, and temperature. Figure 7.5 shows the LCD component displaying the constant readings.

### 7.4.3.2 IoT Gateway

The gateway is used via the ZigBee protocol to communicate with the sensor nodes. A Wi-Fi connection is used to push the data over cloud. A user interface is also developed via gateway to display the captured data. This is a cloud-based mobile app that is installed on the cellphones of the farmers so that they can get the updates.

![](img/0b5412a09266b61a5c216084aa99aac2_145_0.png)

FIGURE 7.3 Component modules of the smart irrigation system.

![](img/0b5412a09266b61a5c216084aa99aac2_145_1.png)

FIGURE 7.4 Sensors in a plant to read soil parameters.

![](img/0b5412a09266b61a5c216084aa99aac2_146_0.png)

**FIGURE 7.5** Readings being displayed using LCD.

### 7.4.3.3 Cloud Services

The ThingSpeak cloud platform is utilized to store and analyze the live data. The forecast and predictions can be accessed through cellular phone-based apps or webapps. The cloud services are used to apply ML algorithms on the data gathered in live environment.

### 7.4.4 Data Analysis

One major contribution of this case study is to make predictions regarding the quantity and quality of the yield from crop by utilizing the sensor data. This proposed system has applications to increase crop yield and raise the productivity with reduced consumption of resources. The model is data-driven, and the ML-based decision-making allows the farmers to manage resources in a smarter way. For example, the data gathered from weather monitoring over a long-term period are fed to the time series forecast model. It will give an opportunity to farmers to make decisions after predicting the weather in advance regarding when to irrigate and how much water will be needed. In fact, the irrigation can be scheduled using the mobile app along with the calendar and clock feature. The activities for data analytics carried out are as follows:

- 1. To gather the data from various sensors
- 2. To preprocess data; to clean and align the data and prepare it for ML algorithm
- 3. To model ML algorithm (to select, train, and test the model)
    - 3a. Classification and regression tree model to predict crop yield and its quality
    - 3b. Autoregressive integrated moving average model to model time series prediction model

### 7.4.5 GRAPHICAL ANALYSIS

The data analysis can be shown graphically using the cloud services for temperature analysis, soil moisture level analysis, humidity level analysis, and light intensity level analysis as shown in Figure 7.6.

![](img/0b5412a09266b61a5c216084aa99aac2_147_0.png)

FIGURE 7.6 Graphical analysis of various parameters.

The measurement of soil moisture, temperature, ambient humidity, etc. is worthy as it allows farmers to manage the scarce water resource in an efficient way. The system provides automation to irrigation task, which saves time and energy. In addition, soil pH level and salinity can be assessed and used to decide the type of crop to be sown. The entire prototype contributes to smart agriculture and helps to enhance the quality and quantity of the crop yield.

## 7.4.6 ADVANTAGES OF THE PROPOSED SYSTEM

After the detailed discussion of the model, let us have a summary of the benefits being offered by the prototype proposed in the candidate case study:

- 1. efficient resource management—water and energy resources;
- 2. supports smart decision-making;
- 3. safety from the danger of snakes or other creatures in the field;
- 4. user-friendly interface to get updates;
- 5. avoids overirrigation and underirrigation;
- 6. avoids the erosion of the top layer of the soil;
- 7. reduces the wastage of water.

This case study brings a WSN using an IoT platform to enable smart agriculture. It demonstrates how the sensors, IoT framework, ML algorithms, and data analytics-based WSNs are successfully being deployed in real farming to collect and monitor multiple environmental, soil, and weather parameters that are in direct association with farming. The entire process is digitalized and available at the fingertips of the farmers.

By implementing such system, a large area of agricultural fields, horticultural parks, and gardens can be irrigated automatically. In large-scale applications, a wide range of sensors with high sensitivity can be installed to cover the big agricultural lands.

## 7.5 CONCLUSION AND FUTURE SCOPE

WSNs along with IoT technology are bringing a green revolution in the agricultural activities. It is making the agricultural activities to be carried out in a smart and intelligent way supported with automation. The practices of smart agriculture are cultivating day by day, turning the face of agriculture by revolutionizing the production in a cost-effective manner. Agriculture is being transformed digitally. The massive data are being collected using sensors from live fields. The usage of WSNs, IoT, robotics, drones, and AI is increasing profoundly. ML algorithms allow to find the interesting pattern hidden in the massive data and use the extracted information to make better decisions later. This chapter has reviewed various applications been contributed by researchers using WSNs in agricultural field. In future, different ML models including ensemble learning models can be applied in multiple applications for a smart agriculture system. To enhance the accuracy of yield prediction, and weed and disease detection, deep learning models such as convolution neural networks can be implemented in future. The use of a WSN for smart agriculture is beautifully showcased through the smart irrigation system case study.

## REFERENCES

- 1. Achilles D. Boursianis, Maria S. Papadopoulou, Panagiotis Diamantoulakis, Aglaiia Liopa-Tsakalidi, Pantelis Barouchas, George Salahas, George Karagiannidis, Shaohua Wan, and Sotirios K. Goudos, (2020). Internet of Things (IoT) and Agricultural Unmanned Aerial Vehicles (UAVs) in smart farming: A comprehensive review, Internet of Things, p. 100187. doi: 10.1016/j.iot.2020.100187.

- 2. Eduardo Gomes, Arnaud Banos, Patrícia Abrantes, Jorge Rocha, and Markus Schläpfer, (2020). Future land use changes in a peri-urban context: Local stakeholder views, Science of The Total Environment, 718, p. 137381. ISSN 0048-9697, doi: 10.1016/j.scitotenv.2020.137381.

- 3. Anastasios Lytos, Thomas Lagkas, Panagiotis Sarigiannidis, Michalis Zervakis, and George Livanos, (2020). Towards smart farming: Systems, frameworks and exploitation of multiple sources, Computer Networks, 172, p. 107147. ISSN 1389-1286, doi: 10.1016/j.comnet.2020.107147.

- 4. Jana Münz, Nicola Gindle, and Reiner Doluschitz, (2020). Exploring the characteristics and utilisation of Farm Management Information Systems (FMIS) in Germany, Computers and Electronics in Agriculture, 170, p. 105246. ISSN 0168-1699, doi: 10.1016/j.compag.2020.105246.

- 5. Somya Goyal, Anubha Parashar, and Anita Shrootriya, (2018). Application of big data analytics in cloud computing via machine learning, Data Intensive Computing Applications for Big Data, IOS PRESS-2018, 29, pp. 236–266. doi: 10.3233/978-1-61499-814-3-236.

- 6. Anubha Parashar, Apoorva Parashar, and Somya Goyal, (2018). Big data analysis using machine learning approach to compute data, Data Intensive Computing Applications for Big Data, IOS PRESS-2018, 29, pp. 133–160. doi: 10.3233/978-1-61499-814-3-133.
