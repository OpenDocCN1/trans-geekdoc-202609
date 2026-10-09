
establishes the connection with the MQTT broker requires an MQTT client. Therefore, an MQTT client is installed on both publisher (RasPi) and subscriber devices (monitoring server) to connect, disconnect, publish and subscribe data. The RasPi must specify a topic to publish data to the MQTT broker, and only the device that is subscribed to the same specified topic can receive that data from the MQTT broker. By establishing connections between the RasPi and the MQTT broker based on MQTT QoS (2), the important decisions taken are based on the EEDF algorithm.

Each sensor senses 7 B of data, obtained by sensing events from the test section. Thus, the total data gathered by all sensors is 42 B. It is now proposed that the EEDF algorithm also checks and compares simultaneously collected data with the previous record for each sensor individually. If the collected data in each sensor is not equal to the previous record, then it is sent to the broker via the internet. Otherwise, the EEDF protocol detects no change in the data and then filters the duplicated data out and thus this data is not sent to the broker. As a result, the RasPi antenna goes into sleep mode. Of course, in the first round, all the collected data is sent to the broker because there is no previous data record for comparison. As a result, the proposed scheme minimizes the processing and transmission time for the RasPi. This, in turn, helps minimize the energy consumption of the RasPi. It also reduces the delay time and bandwidth used over the entire path of the network and improves the performance of the end-to-end system. The flowchart of the proposed algorithm to sense and forward the data is presented in Figure 10.10.

### 10.3.2 Predicting Process

The first concern of the PNDD protocol is to establish the connection between the monitoring server and MQTT broker based on MQTT QoS (2). When the QoS (2) process is complete, the connection is created and the monitoring server can communicate with the MQTT broker and receive messages. However, the PNDD algorithm requires a database to store the data that comes from the MQTT broker. Therefore, SQLite was installed on the monitoring server to store, analyze and plot the data.

After that, the PNDD protocol listens to the MQTT broker and gets a copy of the data forwarded by RasPi. The transmitted data could be a number of bytes or an empty row based on the EEDF publisher policy. The PNDD algorithm receives and stores the empty row of data when there is a connection between monitoring server and RasPi through the MQTT broker, but no data is received (data filtered by EEDF algorithm). Otherwise, the PNDD algorithm stores the transmitted data (payload) in the monitoring server database.

![](img/bb4a43d3cc1537c84f048d14c493ee68_265_0.png)

Figure 10.10 Flow chart of the publisher algorithm.

Real-time plotting plays a significant role in the diagnostics of any remote monitoring system. Thus, the PNDD protocol provides the end-user with a real-time plotting system for further processing and diagnosing the information. The PNDD algorithm predicts and retrieves data when it is required. If the collected data in the database is not equal to the empty row data, then it plots the current data. Otherwise, it plots the previous record as the new data. As a result, the PNDD protocol reduces the capacity required to store information. The flowchart of the PNDD protocol is shown in Figure 10.11.

![](img/bb4a43d3cc1537c84f048d14c493ee68_266_0.png)

Figure 10.11 Flow chart of the subscriber algorithm.

### 10.3.3 Remote Monitoring Systems

IoT has gained considerable popularity and is widely applied in many fields, but different devices using various sensors are utilized for monitoring activities [22]. These sensors collect data and use that data to trigger automatic alerts and actions such as maintenance requests, remote diagnostics and other optional processes [23, 24].

Thus, this chapter, in addition to a filtering mechanism also proposes a remote monitoring system for a gas turbine engine in an IoT environment.

The system aims to monitor and diagnose the condition of the gas turbine engine, sensors and IoT device (RasPi). Here, the RasPi acts as the gateway, connecting the sensors to the internet. The data is gathered by the six sensors and forwarded to the RasPi which uses its WiFi connectivity to establish the connection and disseminate the data to the monitoring server (end-user) based on the MQTT broker.

On the monitoring side, each item of data that is sent by each sensor requires the plotting of an individual sub-figure. Therefore, the end-user has a dashboard for displaying and analyzing the data for each sensor (see Figures 10.14 to 10.19). Based on these figures, the end-user can check the system status, sensors or RasPi for errors during real-time communication. For instance, the end-user checks the engine condition based on the x- and y-axes of the sub-figures. Should the RasPi experience connectivity issues or sensor stop sending data to the end-user, the sub-figure stops plotting the data. Thus, the end-user can see which sensor is faulty. Figure 10.12 presents the architecture of the proposed work which includes four main parts: engine, sensors, gateway (RasPi) and end-user.

![](img/bb4a43d3cc1537c84f048d14c493ee68_267_0.png)

## 10.4 Experimental Setup

The experimental set-up to test the performance of the proposed algorithms for an IoT application is defined in this section. In Figure 10.13, the hardware is deployed. As the working medium, water is used and pumped from the tank into the test section. Six transmitter sensors measure the volume of the water flow rate.

![](img/bb4a43d3cc1537c84f048d14c493ee68_268_0.png)

Figure 10.13 The experimental setup.

The sensors are interfaced and powered by the CPi. They are placed in different positions in the test section to sense and forward the data to the RasPi via the CPi. The CPi is linked to and powered by the RasPi. The RasPi is used to process and forward the data to the monitoring server via the cloud. The data is dispatched by the RasPi every 15 s. The network was tested for 25 min. The parameters and protocols used in the setup are shown in Table 10.1.

Here the RasPi is mains powered, but in a real situation, it will most certainly be battery powered, i.e., resource-limited. To validate the reduced energy consumption, the measurements were made using a USB 3.0 LCD voltmeter ammeter voltage multimeter tester.

Table 10.1 A list of all parameters used in this study.

| Parameter | Value |
| :--- | :--- |
| Type of IP | IPv4 |
| Header Size + Payload | 27 bytes |
| Type of MQTT-QoS used | 2 |
| RasPi B power | 5-volt, 700 mA |
| RasPi to access point link | Wireless |
| Monitoring server to access point link | Wireless |
| Monitoring server operating system | Windows 8.1 |
| RasPi B operating System | Raspbian |

## 10.4.1 Implementation Using Python

After the hardware was connected and seen to be working correctly, the Python script file was constructed on the RasPi and monitoring server to read and receive the sensor values, respectively. The collected data was then forwarded to the MQTT broker via the internet. On the other hand, the monitoring server received and saved the transmitted data into the database table. In order to implement the proposed system, there are several requirements to be met:

### 10.4.1.1 Prerequisites

The inherent requirements of the proposed protocol are listed below [4]:

- Python 2.7: is installed in both devices; RasPi and the monitoring server which helps to read the sensor values, process and forward the data to the monitoring server. It also assisted in receiving, plotting and storing these data sets on the monitoring server database.
- SQLite3 database: is installed in the monitoring server and used to save the data on it. SQLite3 is integrated with Python using a SQLite3 module. Thus, it did not require any further installation.
- Python pip: is a package management system which was used to install and manage software packages that were written in Python.
- Paho MQTT Client: is a lightweight publish and subscribe system that allows sending and receiving data as a client. It was installed in both RasPi and the monitoring server.
- MQTT Broker: helps to establish the connection and exchange information between the publisher and subscriber devices. The open service MQTT broker (iot.eclipse.org) was used in this study.
- Python matplotlib: is a Python library that draws graphs and plots the data during real-time communication. It was installed on the monitoring server.

### 10.4.2 Monitoring Data

Matplotlib is a plotting library for the Python programming language and was used to plot the collected data during the real-time communication on
