# Server and Servlet Architectures for a Cloud-Based Real-Time ...

3. A JFileChooser window will be presented to the user, the user can choose which location to save the CSV file as shown in Figure 7.19. The application will also show the downloaded data in the result TextView as shown in Figure 7.20.

4. To download weather observation for a specific date, the required date is entered in the "Download Data for:" JTextField. Then, the "Download" button is pressed. The application repeats step 2 allowing the user to choose where to save the file.

5. The CSV files downloaded in the specific directory are depicted in Figure 7.21. They are automatically labelled as "weather_data x" and "weather_data y", respectively, on the requests made by the user.

![](bbox=[0.082, 0.325, 0.918, 0.653])

Figure 7.21. CSV file for last 10 records and CSV file for 29/11/2020.

# 7.2.3. Performing Analytics

+   1. To use from the local database, the user must choose "Local database" from the JComboBox, and use data from the Cloudant database the user must choose "Cloud database" from the JComboBox.

+   2. Analytics can be performed by specifying the "Prediction Time" and "Window Size" values, before clicking on the "Predict" button. The application will perform the analytics locally and display it in the JResult as shown in Figure 7.22.