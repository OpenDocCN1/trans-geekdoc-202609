# Table 4.1. (Continued)

| | prediction.java class |
| --- | --- |
| onCreate() | Sets the prediction xml layout onto the display and contains two buttons that execute the prediction and classification functions from databases from either the cloud or localhost. |
| predictThread (Thread) | Constructs an appropriate URL to query the servlet for predictive analytics using Socket connections. Sets the obtained result onto the GUI. |
| predictThreadLocalhost (Thread) | Contacts the local server running on NetBeans to perform analytics using locally stored databases. |
| classifyThread (Thread) | Constructs an appropriate URL to query the servlet for classification analytics using Socket connections. Sets the obtained result onto the GUI. |
| classifyThreadLocalhost (Thread) | Contacts the local server running on NetBeans to perform classification using locally stored databases. |
| Main components of download.java class |
| onCreate() | Sets the download layout onto the display and contains three buttons. One for the location to store the .csv files while the rest performing the downloading functions. The latter can be performed from Cloudant or locally stored databases. |
| showDirectoryPicker() | Initializes the StorageFileChooser class from the Storage chooser as well as registers a listener on the chooser object. |
| hasPermissions() | Helper method that verifies the permissions of a given array are granted or not. |
| onRequestPermissionsResult() | Call-back that handles the status of the permissions request. |
| fetchRegression ValuesAndroid() | Connects to the Cloudant database using the CloudantClient to fill a series of arrays of type double with seven network parameters captured by the Android device and their timestamps.|

Each class detailed above has its specific purpose in terms of acquiring the parameters, uploading them to the Cloudant database and performing analytics. Download functionalities are also provided whereby the user can select the parameters to be downloaded into .csv files by either specifying a desired number of samples or searching by date. The application also provides the ability to choose from the “Cloudant” or “Local” databases. To summarise, buttons placed on the GUI using the XML files are mapped to the respective above actions. This results in different threads being created upon clicking a button. Threads are implemented to permit the application to perform various tasks at the same time, allowing concurrent I/O operations. They are defined through the use of either the Runnable or Thread classes.

# 4.3.1. Creating the Android project

+   1. The Android Studio application is first started and with the following popping up, a new project is created as shown in Figure 4.3.