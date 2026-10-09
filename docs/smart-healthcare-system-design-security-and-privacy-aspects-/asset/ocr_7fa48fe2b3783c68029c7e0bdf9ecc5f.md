# 10.4.1 Implementation Using Python

After the hardware was connected and seen to be working correctly, the Python script file was constructed on the RasPi and monitoring server to read and receive the sensor values, respectively. The collected data was then forwarded to the MQTT broker via the internet. On the other hand, the monitoring server received and saved the transmitted data into the database table. In order to implement the proposed system, there are several requirements to be met:

# 10.4.1.1 Prerequisites

The inherent requirements of the proposed protocol are listed below [4]:

+   • Python 2.7: is installed in both devices; RasPi and the monitoring server which helps to read the sensor values, process and forward the data to the monitoring server. It also assisted in receiving, plotting and storing these data sets on the monitoring server database.

+   • SQLite3 database: is installed in the monitoring server and used to save the data on it. SQLite3 is integrated with Python using a SQLite3 module. Thus, it did not require any further installation.

+   • Python pip: is a package management system which was used to install and manage software packages that were written in Python.

+   • Paho MQTT Client: is a lightweight publish and subscribe system that allows sending and receiving data as a client. It was installed in both RasPi and the monitoring server.

+   • MQTT Broker: helps to establish the connection and exchange information between the publisher and subscriber devices. The open service MQTT broker (iot.eclipse.org) was used in this study.

+   • Python matplotlib: is a Python library that draws graphs and plots the data during real-time communication. It was installed on the monitoring server.

# 10.4.2 Monitoring Data

Matplotlib is a plotting library for the Python programming language and was used to plot the collected data during the real-time communication on