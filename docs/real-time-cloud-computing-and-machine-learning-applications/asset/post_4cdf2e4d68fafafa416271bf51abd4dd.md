
# Data Capture and Client Architecture for a Cloud-Based Real-Time ... 637

2. The IP address of the local server, running on NetBeans IDE on PC can be entered into the first EditText, before clicking on the “MONITOR” button which starts the network monitoring activity.

![](img/2b52fde0e707e8c2f05a10309c3f8982_648_0.png)

Figure 6.22. Monitoring Visibility Variation.

![](img/2b52fde0e707e8c2f05a10309c3f8982_648_1.png)

Figure 6.23. Sending Data Directly to Cloud.

# 638 T. P. Fowdar, L. Babooram, M. N-U-Dbn Nazir Rosun and M. Indoonundan

3. By default, the "Visibility" parameter is chosen in the dropdown menu shown in Figure 6.21. When the monitoring process starts, the graph will be updated with the corresponding values obtained from the API. The values obtained from the API are for the "Port Louis" region. The graph is shown in Figure 6.22.

4. To send data to the local server, the "Cloud" switch must be off. To send data directly to the Cloud database, the "Cloud" Switch must be toggled in the "ON" position as shown in Figure 6.23.

5. The parameter is displayed on the graph is changed using the drop-down below the graph as shown in Figure 6.24.

![](img/2b52fde0e707e8c2f05a10309c3f8982_649_0.png)

Figure 6.24. Dropdown Menu to Change Weather parameter being displayed.

![](img/2b52fde0e707e8c2f05a10309c3f8982_649_1.png)

Figure 6.25. Graph Updated with Wind Speed Values.

6. For example, in Figure 6.25, "Wind Speed" is chosen and the graph's description is observed to change accordingly. The monitoring process is stopped using the "STOP" button where the graph stops updating and is no longer requested from the web API.

7. Figure 6.26 and Figure 6.27 show the data being pushed to Cloudant Platform and MySQL local database.

![](img/2b52fde0e707e8c2f05a10309c3f8982_650_0.png)

Figure 6.26. Data pushed to MySQL Server.

![](img/2b52fde0e707e8c2f05a10309c3f8982_650_1.png)

Figure 6.27. Data pushed to Cloudant Database.

## 6.3.28.2. Downloading Weather Data

- 1. By clicking on the "DOWNLOAD DATA" button on the Main Activity, "DownloadData" activity is launched as shown in Figure 6.28.

![](img/2b52fde0e707e8c2f05a10309c3f8982_651_0.png)

Figure 6.28. DownloadData Activity.

- 2. To download weather observations from the Cloudant platform, the "Cloud" Switch is toggled to the "ON" position. Then, the "DOWNLOAD" button is pressed. To download weather observations from the Local Java Platform, the "Cloud" Switch is toggled to the "OFF" position. The IP Address of the local server is entered in the EditText. Then, the "DOWNLOAD" button is pressed.
- 3. To download the last N samples from the Cloudant platform, first, the number of samples is entered in the "Download Last N Samples" field. Then, the "DOWNLOAD" button is pressed. The application will download the specified number of weather observations into a CSV file. The application will save the file in its default "Download" folder and save the downloaded data in the "result" TextView as shown in Figure 6.29.

![](img/2b52fde0e707e8c2f05a10309c3f8982_651_1.png)

Figure 6.29. Downloading Samples from Cloudant.

4. To download by, the other "DOWNLOAD" button is clicked after specifying the data in a "DD/MM/YYYY" format. The application will download weather observation for the specified date into a CSV file and save it in the application folder and it will also show the downloaded data in the TextView shown in Figure 6.30.

![](img/2b52fde0e707e8c2f05a10309c3f8982_652_0.png)

Figure 6.30. CSV File with Readings for a Specific Date.

## 6.3.28.3. Performing Analytics

- 1. By clicking on the "ANALYSE" button on the Main Activity, the "Analysis" activity is launched as on Figure 6.31.

![](img/2b52fde0e707e8c2f05a10309c3f8982_652_1.png)

Figure 6.31. Analyse Activity.

![](img/2b52fde0e707e8c2f05a10309c3f8982_653_0.png)

Figure 6.32. Showing Result from Servlet.

- 2. To perform analytics on the collected data, the window size of the regression algorithm and the prediction time for which analysis must be entered accordingly, and the appropriate button is clicked.
- 3. The "Cloud Analysis" button is used to obtain analytics results from the cloud and the "Local Analysis" button is used to obtain analytics results from the Local Java Server provided the IP Address has been entered in the EditText.
- 4. After the analysis is done, the results obtained are displayed in the result TextView. The expected output is shown in Figure 6.32 when the "Cloud Analysis" option is chosen.

## 6.4. DESKTOP APPLICATION FOR WEATHER DATA CAPTURE AND ANALYTICS

This section gives a detailed step-by-step guide to develop the desktop application in Java. The application will request current weather conditions from the OpenWeather API, displays the desired variable readings in real-time, and requests a Java servlet for future weather conditions. The application is developed in the NetBeans IDE which supports the drag and drops feature for building GUI applications.

## 6.4.1. Creating the Desktop Application in NetBeans

To create a Java Swing application in NetBeans, the following steps are:
- 1. The NetBeans is launched and a new project is created by "File" then "New Project".

![](img/2b52fde0e707e8c2f05a10309c3f8982_654_0.png)

Figure 6.33. New Project.
- 2. The next step is to choose the type of project. For this purpose, the category "Java" is chosen to use the Ant tool the project type is "Java Application".

![](img/2b52fde0e707e8c2f05a10309c3f8982_654_1.png)

Figure 6.34. Project Category & Type.

- 3. The name and location of the new project to be. One important step here to unselect “Create Main Class” checkbox. This will prevent the creation of a class with the main method. The Finish button is pressed.

![](img/2b52fde0e707e8c2f05a10309c3f8982_655_0.png)

Figure 6.35. Project Name & Location.
- 4. The newly created project will be empty with no classes. To display a window, the JFrame class needs to be added by right-clicking on the default package. A pop-up window will appear, select “New” then “JFrame Form.”

![](img/2b52fde0e707e8c2f05a10309c3f8982_655_1.png)

Figure 6.36. Adding a JFrame.

- 5. The window in Figure 6.37 will be shown where the JFrame class is renamed before adding it to the source package. The appropriate name for the JFrame is entered and then the finish button is clicked.
- 6. The next step is to build the GUI using the drag and drop feature of NetBeans. Design mode can be accessed by clicking "Design" at the top. The GUI Design mode consists of a palette of GUI elements that can be dragged onto the design and placed on the JFrame needed. This saves time as the code for showing the GUI elements is automatically generated by the IDE.

![](img/2b52fde0e707e8c2f05a10309c3f8982_656_0.png)

Figure 6.38. GUI Design Mode with Palette.

- 7. Figure 6.39 and Figure 6.40 show the GUI elements present in the JFrame and the final design of the JFrame.

![](img/2b52fde0e707e8c2f05a10309c3f8982_657_0.png)

Figure 6.39. GUI Design.
The navigator tab gives a tree of the element placement in the JFrame. It also shows the GUI element type and variable name. Table 6.4 gives detail about each GUI element's roles.

![](img/2b52fde0e707e8c2f05a10309c3f8982_657_1.png)

Figure 6.40. JFrame GUI Elements Navigator.
