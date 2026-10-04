
# Data Capture and Client Architecture for a Cloud-Based Real-Time ... 335

![](img/2b52fde0e707e8c2f05a10309c3f8982_346_0.png)
Figure 4.27. Selecting another parameter with dynamic graph updates.

- 6. The monitoring process is stopped using the “STOP” button where the graph comes to a halt in Figure 4.28.

![](img/2b52fde0e707e8c2f05a10309c3f8982_346_1.png)
Figure 4.28. Stopping the monitoring process.

- 7. Additionally, any point on the graph can be zoomed in and clicked on so that its specific value is displayed through a Toast as depicted by Figure 4.29.

![](img/2b52fde0e707e8c2f05a10309c3f8982_347_0.png)
Figure 4.29. Clicking on a data point generates Toast.

## 4.13.2. Downloading Functionalities

- 1. By clicking on the “GO TO DOWNLOAD” button from Figure 4.21, “Download Menu” activity in Figure 4.30 is made available to the user.

![](img/2b52fde0e707e8c2f05a10309c3f8982_347_1.png)
Figure 4.30. Download Menu.

- 2. A destination for the .csv file to be downloaded is first selected using the “BROWSE” button where the desired folder is selected using the “Select” button.

![](img/2b52fde0e707e8c2f05a10309c3f8982_348_0.png)
Figure 4.31. Browsing a path for .csv file.

![](img/2b52fde0e707e8c2f05a10309c3f8982_348_1.png)
Figure 4.32. Finding the desired directory.

![](img/2b52fde0e707e8c2f05a10309c3f8982_349_0.png)
Figure 4.33. Selecting chosen directory.

- 3. With a destination already browsed and a data source to download values by a selected number of registered samples, the “DOWNLOAD” button for the “Last N” field is used. A Toast specifies where the .csv file is being created. The values are also displayed on the GUI on-screen as illustrated by Figures 4.34 and 4.35. Figure 4.36 shows the downloaded .csv file opened on the Android phone.

![](img/2b52fde0e707e8c2f05a10309c3f8982_349_1.png)
Figure 4.34. Downloading by last N.

![](img/2b52fde0e707e8c2f05a10309c3f8982_350_0.png)
Figure 4.35. Values displayed on GUI.

![](img/2b52fde0e707e8c2f05a10309c3f8982_350_1.png)
Figure 4.36. CSV file downloaded.

- 4. To download by date, the second “DOWNLOAD” button is clicked after specifying the date in a “MMM, DD YYYY” format, with the month being abbreviated.

![](img/2b52fde0e707e8c2f05a10309c3f8982_351_0.png)
Figure 4.37. Downloading by date.

![](img/2b52fde0e707e8c2f05a10309c3f8982_351_1.png)
Figure 4.38. Values displayed on GUI.

- 5. The same above steps can be repeated while enabling the "Local" option for the data source as well as entering the IP address of the running local server on NetBeans as shown in Figure 4.39.

![](img/2b52fde0e707e8c2f05a10309c3f8982_352_0.png)
Figure 4.39. Downloading values through the local server.

## 4.3.13.3. Performing Analytics

- 1. By clicking on the "GO TO ANALYSIS" button in Figure 4.21, the analytics menu in Figure 4.40 is opened. It should be noted that the monitoring activity can be running on the first screen that analytics can be performed in real-time.

![](img/2b52fde0e707e8c2f05a10309c3f8982_352_1.png)
Figure 4.40. Prediction Menu.

- 2. To perform regression analytics, the desired values are entered accordingly, and the "PREDICT" button is clicked after selecting a data source. As shown in Figure 4.41, the Cloudant option is selected, meaning that the hosted servlet is being used. With a prediction time of 10 seconds and a window size of 20 values, the results show that the predicted number of packets to be received after 10 seconds with Multiple Linear Regression (MLR) using the Multilayer Perceptron (MLP) algorithm. The URL that performs an HTTP request to the hosted servlet is as follows: https://networkcloud.eu-gb.myuemix.net/downloadSpeed=200&uploadSpeed=25&packetsReceived=300&packetsSent=200&predictionTime=10&windowSize=20&device=2&source=1.

![](img/2b52fde0e707e8c2f05a10309c3f8982_353_0.png)
Figure 4.41. Performing regression analytics.

- 3. For classification analytics, the "CLASSIFY" button is clicked to classify the values being recorded by the live graph at the time. Classification is thus performed by the servlet using K-nearest neighbour (KNN) and Multilayer Perceptron (MLP) which both yield an activity status of "streaming" since the Android phone is displaying a live stream. The results are displayed on the GUI. The URL requesting the hosted servlet is as follows: https://networkcloud.eu-gb.myuemix.net/ml/downloadSpeed=126.35&uploadSpeed=137.62&packetsReceived=94.0&packetsSent=214.0&predictionTime=10&windowSize=20&device=2&action=1.

![](img/2b52fde0e707e8c2f05a10309c3f8982_354_0.png)
Figure 4.42. Performing classification.

- 4. The combination of an IP address and the “Local” option as the data source connects the Android phone to the local server running on NetBeans, through which the buttons are used through the same principle described in steps one to three.

## 4.4. DESKTOP APPLICATION FOR NETWORK DATA CAPTURE AND ANALYTICS

Along with the Android phone used as an edge device, the second machine used in this architecture for parameter monitoring is the desktop PC. It is one of the most popular devices on the planet and consists of an integral part of network monitoring with data traffic involving a PC in networking systems.

As observed with the Android device, particular classes are used to retrieve network parameters. Likewise, for the desktop PC, network data is exploited using the Sigar library available at [16]. The NetBeans IDE is used for designing this Java application whereby the integrated Swing Graphical Interface (GUI) is firstly used to create the layout for the application. This is then followed by mapping the buttons created to specific functionalities.

The parameters that are investigated and extracted for the PC application are:

- Wi-Fi download speed in Kbps
- Wi-Fi upload speed in Kbps
- Number of packets received per second
- Number of packets sent per second

This section, therefore, consists of detailing the desktop PC software purposes resemble that of the Android application previously detailed. It can therefore monitor the changes in network data every second with the possibility of pushing the data to the cloud database, or one stored on localhost using software such as XAMPP. The latter is then performed by connecting to the local server, also running on NetBeans using the PC's IP address. For this application, separate databases are used for the Android phone and the PC since they have different parameters being monitored. A general schema of the complete program structure is illustrated in Figure 4.43. The threads used by the receiver buttons are also shown.

![](img/2b52fde0e707e8c2f05a10309c3f8982_355_0.png)
Figure 4.43. Overview of program structure for Desktop Application.

The Desktop Application makes use of a single Java class, named netmonitor.java, whose methods can be described in Table 4.4.

## Table 4.4. Complete program structure for netmonitor.java

| Methods | Description |
| :--- | :--- |
| netmonitor() | Is the constructor of the class that initializes all components onto the GUI and calls the createGraphSpace() method which programmatically adds the graph to it. |
| createGraphSpace() | Allocates space for the graph on the GUI by adding a chart onto the canvas amounts the existing JFrame using the JFreeChart class. |
| getNumberOfItems(Thread) | Retrieves the list of records stored from the Cloudant database before pushing values so that they can be entered in an orderly fashion. Uses the CloudClient and Database objects. |
| startMonitoringActionPerformed() | Starts the parameter fetching process as well as pushing to the server or the Cloudant database on active radio buttons. |
| stopMonitoringActionPerformed() | Makes of the Thread object. |
| parameterSelectionActionPerformed() | Clears the drop-down menu for parameter selection is altered. |
| predictButtonActionPerformed() | Requests data from the servlet by taking the parameters entered by the user on the GUI for local prediction using a URLConnection. Also creates a thread for local prediction that connects the local server running on PC using an IP address. |

## 4.4.1. Creating the NetBeans project

- 1. The NetBeans IDE is started and "New Project" is selected under the "File" tab on the menu bar as shown in Figure 4.44.
