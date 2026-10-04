# Data Capture and Client Architecture for a Cloud-Based Real-Time ... 647

# Table 6.4. Functions of the different elements in Main.java

| Variable Name | Swing Element | Function |
| window_s | JTextField | User enters the value of the window size for the algorithm |
| ptime | JTextField | User enters the value of the prediction time |
| predict | JButton | When pressed, the prediction is started |
| monitor | JButton | When pressed, a New Timer object is created and a TimerTask is scheduled to be executed every N Minutes |
| result | JTextArea | Area to display the results of the forecast algorithms obtained from the local server or Java Servlet |
| w_var | JComboBox | Chooses the variable to display graph |
| address_f | JTextField | A textfield for the user to enter the IP address of the local server |
| cloud_wave | JComboBox | Determines whether to send the data directly to the cloud or the local server |
| window_label | JLabel | If checked the cloud otherwise it sends to the local server |
| prediction_label | JLabel | Label for window JTextField |
| result_label | JLabel | Label for prediction JTextField |
| graph_label | JLabel | Label for result JTextArea |
| IP_label | JLabel | Label for graph |
| cloud_label | JLabel | Label for address JTextField |
| download_label | JLabel | Label for the save to cloud JCheckBox |
| download_date | JLabel | Label for the window size JTextField |
| download_Samples | JButton | Label for the date JTextField When pressed, the application data for the specified sample size |
| download_date | JButton | When pressed, the application data for the specified date |
| View_label | JLabel | Label for the viewing JTextArea |
| down_n | JTextField | A JTextField to enter the number of samples to fetch |
| down_date | JTextField | A JTextField to enter the date for which samples are needed |
| data_view | JTextArea | A JTextArea to view the data fetched from the cloud |
| data_src | JComboBox | Choose data source to use |

# 6.4.2. Adding Libraries

The application uses three of Java libraries that need to be imported using the NetBeans import function. The function performed by each library is explained in Table 6.5 and the steps to be followed to add the libraries in the project are given below. The GitHub repository where each library can be downloaded is also given.

+   1. First, a new folder labelled 'lib' is created in the Project's directory. This folder will store all the libraries jar files.
2. Then, the required libraries are downloaded from their respective GitHub repositories and saved in the previously created folder.
3. After downloading the jar files, the files are imported into the project using the NetBeans First, the Project tree is expanded and the “Libraries” Folder is located.