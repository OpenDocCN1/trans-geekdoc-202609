# 590 T. P. Fowdur, B. Baboor, M. N-D-Ibn Naz Rosun and M. Indoonondon

# 6.3.3. Program Structure

Table 6.2 shows the program structure of the android application. The different classes and methods used are listed and detailed.

# Table 6.2. App Structure

| MainActivity.java | QueryAPI.java | Analysis.java | QueryCloudServer.java |
| --- | --- | --- | --- |
| Uses: activity_main.xml & QueryAPI | Responsible for requesting weather information from the API using JSON. | Uses: activity_main.xml & the API | Responsible for contacting the java server hosted in the cloud to obtain predictions |
| DownloadData.java | QueryDateLocal.java | DataRetriever.java | QueryLocalServer.java |
| Uses: activity_download.data & QueryServer to display a UI where we view the data fetched from the cloud. | AsyncTask class to fetch data from the Cloud database Used connectivity from the main Thread | Responsible for fetching data from the Cloudant database. | Responsible for contacting the local server to obtain analytics results. |
| | | QueryDateLocal.java | |
| AsyncTask class that uses Socket Connection to fetch data from the main Thread. Used to perform connectivity away from |
| | Main Methods of the MainActivity.java class |
| onCreate() - Displays the screen, registers the buttons listeners, and initializes the spinner and graph. | addEntry(it) – Adds a new value to the graph and update it |
| createState() - Creates a new LineDataSet with label being the selected variant and sets the styling. | onItem(i) – Shows the graph clearly. |
| Main Methods of the Analysis.java class |
| doInBackground() - requests weather information from the API using JSP | onExecute(i) – sends data to the local server or directly to the cloud. Also updates the graph with the new value |
| Main Methods of the QueryServer.java class |
| onCreate() - Displays the screen, registers the button listeners. |
| doInBackground() - requests forecast from the java servlet hosted on the cloud | onExecute(i) – shows the result in a TextView. |
| Main Methods of the QueryLocalServer.java class |
| doInBackground() - requests forecast from the local java server | onExecute(i) – shows the result in a TextView. |
| Main Methods of the DownloadData.java class |
| onCreate() - Displays the screen, registers the button listeners. | writeToStorage() – Saves the CSV string to the internal folder of the application |
| convertToCSV() - Converts the data from the Cloudant Platform to its CSV value. |
| Main Methods of the QueryDateLocal.java class |
| QueryServer() – Constructor | doInBackground() – fetches the data from the Cloudant database using DataRetriever and saves it to the internal storage. | onExecute(i) – displays the data fetched in the TextView. |
| Main Methods of the DataRetriever.java class |
| DataRetriever() – constructor that establishes a connection to the Cloudant database |
| getNoRows() – gets the number of rows in the database. | getDatabaseArray() – fetches the last N samples of weather readings for a specific date. |
| Main Methods of the QueryDateLocal.java class |
| QueryServer() – Constructor | doInBackground() – fetches the data from the local server via a Socket Connection and saves it to the internal storage. | onExecute(i) – displays the data fetched in the TextView. |